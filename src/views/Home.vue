<template>
  <div class="home">
    <div class="container">
      <!-- 左侧个人信息栏 -->
      <aside class="sidebar">
        <div class="profile-section">
          <!-- 头像 -->
          <div class="avatar-container">
            <img src="/avatar.jpg" alt="Profile" class="avatar" />
            <div class="avatar-ring"></div>
          </div>
          
          <!-- 姓名 -->
          <h1 class="name">Your Name</h1>
          
          <!-- 一句话总结 -->
          <p class="tagline">Full Stack Developer & Creative Thinker</p>
          
          <!-- 简介 -->
          <div class="bio">
            <p>
              Passionate about building beautiful, functional web applications. 
              Specializing in Vue.js, modern JavaScript, and responsive design. 
              Always learning, always creating.
            </p>
          </div>
          
          <!-- 联系方式按钮 -->
          <div class="contact-buttons">
            <a href="mailto:your.email@example.com" class="contact-btn primary">
              <span class="btn-icon">📧</span>
              Email Me
            </a>
            <a href="https://github.com/yourusername" target="_blank" class="contact-btn secondary">
              <span class="btn-icon">📦</span>
              GitHub
            </a>
            <a href="https://linkedin.com/in/yourprofile" target="_blank" class="contact-btn secondary">
              <span class="btn-icon">💼</span>
              LinkedIn
            </a>
          </div>
          
          <!-- 社交链接 -->
          <div class="social-links">
            <a href="#" class="social-link" title="Twitter">
              <span>🐦</span>
            </a>
            <a href="#" class="social-link" title="Instagram">
              <span>📷</span>
            </a>
            <a href="#" class="social-link" title="Discord">
              <span>💬</span>
            </a>
          </div>
        </div>
      </aside>

      <!-- 右侧内容区域 -->
      <main class="main-content">
        <!-- 动态区域 -->
        <section class="updates-section">
          <h2 class="section-title">
            <span class="title-icon">🔔</span>
            Latest Updates
          </h2>
          <div class="updates-list">
            <div class="update-item" v-for="update in updates" :key="update.id">
              <div class="update-date">{{ update.date }}</div>
              <div class="update-content">
                <h3>{{ update.title }}</h3>
                <p>{{ update.description }}</p>
                <a v-if="update.link" :href="update.link" class="update-link">Learn more →</a>
              </div>
            </div>
          </div>
        </section>

        <!-- 个人项目 -->
        <section class="projects-section">
          <h2 class="section-title">
            <span class="title-icon">🚀</span>
            Featured Projects
          </h2>
          <div class="projects-grid">
            <div v-for="project in featuredProjects" :key="project.id" class="project-card">
              <div class="project-image">
                <img :src="project.image" :alt="project.title" />
                <div class="project-overlay">
                  <a :href="project.githubUrl" target="_blank" class="project-link">
                    <span>📦</span>
                  </a>
                  <a v-if="project.liveDemoUrl" :href="project.liveDemoUrl" target="_blank" class="project-link">
                    <span>🌐</span>
                  </a>
                </div>
              </div>
              <div class="project-content">
                <h3>{{ project.title }}</h3>
                <p>{{ project.introduction }}</p>
                <div class="project-tech">
                  <span v-for="tech in project.techStack" :key="tech" class="tech-tag">
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>
          </div>
          <div class="section-footer">
            <router-link to="/projects" class="view-all-btn">View All Projects →</router-link>
          </div>
        </section>

        <!-- Blog -->
        <section class="blog-section">
          <h2 class="section-title">
            <span class="title-icon">📝</span>
            Recent Blog Posts
          </h2>
          <div class="blog-list">
            <article v-for="post in recentPosts" :key="post.id" class="blog-post">
              <div class="blog-meta">
                <span class="blog-date">{{ post.date }}</span>
                <span class="blog-reading-time">5 min read</span>
              </div>
              <h3>{{ post.title }}</h3>
              <p class="blog-excerpt">{{ post.excerpt }}</p>
              <router-link :to="`/blog/${post.id}`" class="blog-link">
                Read more →
              </router-link>
            </article>
          </div>
          <div class="section-footer">
            <router-link to="/blog" class="view-all-btn">View All Posts →</router-link>
          </div>
        </section>
      </main>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'Home',
  setup() {
    const updates = ref([
      {
        id: 1,
        date: '2024-01-15',
        title: '🎉 New Portfolio Launched',
        description: 'Just launched my new personal portfolio website built with Vue 3 and Vite!',
        link: null
      },
      {
        id: 2,
        date: '2024-01-10',
        title: '📝 Published New Blog Post',
        description: 'Wrote about my experience learning Vue 3 Composition API.',
        link: '/blog/vue3-composition-api'
      },
      {
        id: 3,
        date: '2024-01-05',
        title: '🚀 Completed E-commerce Project',
        description: 'Finished a full-stack e-commerce application with Vue and Node.js.',
        link: '/projects/ecommerce'
      }
    ])

    const featuredProjects = ref([])
    const recentPosts = ref([])

    // 加载项目数据
    const loadProjects = async () => {
      try {
        const response = await fetch('/data/projects.json')
        const projects = await response.json()
        featuredProjects.value = projects.slice(0, 3) // 只显示前3个项目
      } catch (error) {
        console.error("Failed to load projects:", error)
      }
    }

    // 加载博客数据
    const loadPosts = async () => {
      try {
        const response = await fetch('/data/blog.json')
        const posts = await response.json()
        recentPosts.value = posts.slice(0, 3) // 只显示前3篇文章
      } catch (error) {
        console.error("Failed to load blog posts:", error)
      }
    }

    onMounted(() => {
      loadProjects()
      loadPosts()
    })

    return {
      updates,
      featuredProjects,
      recentPosts
    }
  }
}
</script>

<style scoped>
/* 整体布局 */
.home {
  min-height: 100vh;
  padding: 80px 20px 20px;
  background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 350px 1fr;
  gap: 3rem;
  height: 100%;
}

/* 左侧边栏 */
.sidebar {
  position: sticky;
  top: 100px;
  height: fit-content;
}

.profile-section {
  background: rgba(45, 55, 72, 0.8);
  backdrop-filter: blur(10px);
  border-radius: 24px;
  padding: 2.5rem;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
}

/* 头像 */
.avatar-container {
  position: relative;
  display: inline-block;
  margin-bottom: 2rem;
}

.avatar {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid var(--primary-color);
  box-shadow: 0 0 30px rgba(102, 126, 234, 0.5);
}

.avatar-ring {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border: 2px solid var(--primary-light);
  border-radius: 50%;
  animation: rotate 20s linear infinite;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

/* 个人信息 */
.name {
  font-size: 2rem;
  font-weight: 800;
  margin-bottom: 0.5rem;
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.tagline {
  font-size: 1.1rem;
  color: var(--primary-light);
  margin-bottom: 1.5rem;
  font-weight: 500;
}

.bio {
  margin-bottom: 2rem;
}

.bio p {
  color: var(--text-secondary);
  line-height: 1.6;
  font-size: 0.95rem;
}

/* 联系按钮 */
.contact-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}

.contact-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.8rem 1.5rem;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  gap: 0.5rem;
}

.contact-btn.primary {
  background: var(--gradient-primary);
  color: white;
  box-shadow: 0 4px 6px rgba(102, 126, 234, 0.3);
}

.contact-btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(102, 126, 234, 0.4);
}

.contact-btn.secondary {
  background: rgba(102, 126, 234, 0.1);
  color: var(--primary-light);
  border: 1px solid rgba(102, 126, 234, 0.3);
}

.contact-btn.secondary:hover {
  background: rgba(102, 126, 234, 0.2);
  transform: translateY(-2px);
}

.btn-icon {
  font-size: 1.1rem;
}

/* 社交链接 */
.social-links {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.social-link {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(102, 126, 234, 0.1);
  border-radius: 50%;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: var(--primary-color);
  transform: translateY(-3px);
}

.social-link span {
  font-size: 1.2rem;
}

/* 右侧主内容 */
.main-content {
  display: flex;
  flex-direction: column;
  gap: 3rem;
}

/* 通用区域样式 */
section {
  background: rgba(45, 55, 72, 0.6);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  padding: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.section-title {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 2rem;
  font-size: 1.5rem;
  color: var(--primary-light);
}

.title-icon {
  font-size: 1.5rem;
}

/* 动态区域 */
.updates-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.update-item {
  display: flex;
  gap: 1.5rem;
  padding: 1.5rem;
  background: rgba(102, 126, 234, 0.05);
  border-radius: 12px;
  border-left: 3px solid var(--primary-color);
  transition: all 0.3s ease;
}

.update-item:hover {
  background: rgba(102, 126, 234, 0.1);
  transform: translateX(5px);
}

.update-date {
  color: var(--text-muted);
  font-size: 0.9rem;
  min-width: 100px;
}

.update-content h3 {
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.update-content p {
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}

.update-link {
  color: var(--primary-light);
  text-decoration: none;
  font-weight: 500;
}

.update-link:hover {
  text-decoration: underline;
}

/* 项目区域 */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.project-card {
  background: rgba(102, 126, 234, 0.05);
  border-radius: 16px;
  overflow: hidden;
  transition: all 0.3s ease;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(102, 126, 234, 0.2);
}

.project-image {
  position: relative;
  height: 180px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-link {
  width: 40px;
  height: 40px;
  background: var(--primary-color);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all 0.3s ease;
}

.project-link:hover {
  transform: scale(1.1);
  background: var(--primary-light);
}

.project-content {
  padding: 1.5rem;
}

.project-content h3 {
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.project-content p {
  color: var(--text-secondary);
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-tag {
  background: rgba(102, 126, 234, 0.2);
  color: var(--primary-light);
  padding: 0.3rem 0.8rem;
  border-radius: 12px;
  font-size: 0.8rem;
}

/* Blog区域 */
.blog-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.blog-post {
  padding: 1.5rem;
  background: rgba(102, 126, 234, 0.05);
  border-radius: 12px;
  transition: all 0.3s ease;
}

.blog-post:hover {
  background: rgba(102, 126, 234, 0.1);
  transform: translateX(5px);
}

.blog-meta {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

.blog-date, .blog-reading-time {
  color: var(--text-muted);
  font-size: 0.9rem;
}

.blog-post h3 {
  color: var(--text-primary);
  margin-bottom: 0.5rem;
}

.blog-excerpt {
  color: var(--text-secondary);
  margin-bottom: 1rem;
  line-height: 1.6;
}

.blog-link {
  color: var(--primary-light);
  text-decoration: none;
  font-weight: 500;
}

.blog-link:hover {
  text-decoration: underline;
}

/* 区域底部 */
.section-footer {
  text-align: center;
  padding-top: 1rem;
}

.view-all-btn {
  color: var(--primary-light);
  text-decoration: none;
  font-weight: 500;
  padding: 0.5rem 1rem;
  border: 1px solid var(--primary-color);
  border-radius: 20px;
  transition: all 0.3s ease;
}

.view-all-btn:hover {
  background: var(--primary-color);
  color: white;
}

/* 响应式设计 */
@media (max-width: 1024px) {
  .container {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .sidebar {
    position: static;
    max-width: 500px;
    margin: 0 auto;
  }
  
  .projects-grid {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }
}

@media (max-width: 768px) {
  .home {
    padding: 80px 1rem 1rem;
  }
  
  .profile-section {
    padding: 2rem 1.5rem;
  }
  
  .name {
    font-size: 1.5rem;
  }
  
  section {
    padding: 1.5rem;
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .update-item {
    flex-direction: column;
    gap: 1rem;
  }
  
  .update-date {
    min-width: auto;
  }
}
</style>
