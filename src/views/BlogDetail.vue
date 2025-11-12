<!-- src/views/BlogDetail.vue -->
<template>
  <div v-if="post" class="blog-detail">
    <router-link to="/blog" class="back-link">← Back to Blog</router-link>
    <h1>{{ post.title }}</h1>
    <p class="post-date">{{ post.date }}</p>
    <div class="post-content" v-html="post.content"></div>
  </div>
  <div v-else>
    <p>Post not found.</p>
  </div>
</template>

<script>
import { ref, onMounted, watch } from 'vue'
import { useRoute } from 'vue-router'

export default {
  name: 'BlogDetail',
  setup() {
    const loadPost = async () => {
      loading.value = true
      error.value = null
      post.value = null
    
      try {
        // 正确的写法：使用 BASE_URL 并指向正确的数据文件
        const dataUrl = `${import.meta.env.BASE_URL}data/blog.json`
        console.log('Fetching from:', dataUrl) // 保留这行用于调试
    
        const response = await fetch(dataUrl)
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`)
        }
        
        const allPosts = await response.json()
        const postId = route.params.id // 这是从 URL 获取的 ID，比如 "1"
        
        const foundPost = allPosts.find(p => p.id === postId) // 在数据中查找这个 ID
        
        if (!foundPost) {
          throw new Error(`Post with ID "${postId}" not found`)
        }
        
        post.value = foundPost
    
      } catch (err) {
        console.error("Failed to load post:", err)
        error.value = err.message
      } finally {
        loading.value = false
      }
    }


    onMounted(fetchPost)
    watch(() => route.params.id, fetchPost)

    return { post }
  }
}
</script>

<style scoped>
.blog-detail {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  background: #1a1a1a;
  color: #fff;
}

.back-link {
  color: #aaa;
  text-decoration: none;
  margin-bottom: 1rem;
  display: inline-block;
}

.post-date {
  color: #888;
  margin-bottom: 2rem;
}

.post-content {
  line-height: 1.8;
  font-size: 1.1rem;
  color: #bbb;
}
</style>
