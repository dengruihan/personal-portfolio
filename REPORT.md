## /src - 源代码目录
    App.vue: 应用程序的根组件，包含全局样式和路由视图
    main.js: 应用程序入口文件，负责创建 Vue 实例并配置路由

## /src/components - 可复用组件
    Navbar.vue: 顶部导航栏组件，包含响应式菜单
    /icons: 图标组件集合，自带的，没有用到
        IconDocumentation.vue: 文档图标
        IconTooling.vue: 工具图标
        IconEcosystem.vue: 生态系统图标
        IconCommunity.vue: 社区图标
        IconSupport.vue: 支持图标

## /src/views - 页面视图组件
    Home.vue: 主页视图，包含了项目，博客，动态，quick fact，联系方式等信息以及跳转链接
    About.vue: About页面视图，有故事、目标、兴趣、联系方式
    Skills.vue: 技能和教育经历展示页面
    Projects.vue: 项目列表页面
    ProjectDetail.vue: 项目详情页
    Blog.vue: 博客列表页面
    BlogDetail.vue: 博客详情页
    Links.vue: 相关链接页面（一开始AI生成的，后面在导航栏中删去了，没调用）

## /src/router - 路由配置
- **index.js**: 路由系统核心配置
  - 定义所有页面路由规则
  - 配置动态路由参数
  - 处理路由守卫
  - 设置页面过渡效果

## /public - 静态资源目录
    ### /data - JSON数据文件
        - **about.json**: 个人信息数据
        - 基本资料
        - 教育背景
        - 工作经历
        - **blog.json**: 博客文章数据
        - 文章列表
        - 分类信息
        - 标签系统
        - **projects.json**: 项目数据
        - 项目基本信息
        - 技术栈
        - 项目链接
        - **skills.json**: 技能数据
        - 技能分类
        - 熟练程度
        - 相关经验

    /icons: 网站图标资源
        bell.svg: 铃铛图标
        blog.svg: 博客图标
        book.svg: 书籍图标
        chart.svg: 图表图标
        cloud.svg: 云计算图标
        email.svg: 邮件图标
        expert.svg: 专家图标
        eye.svg: 眼睛图标
        gear.svg: 齿轮图标
        gitHub.svg: GitHub图标
        lightbulb.svg: 电灯泡图标
        paint.svg: 颜料板图标
        phone.svg: 电话图标
        project.svg: 方块图标，代表项目
        robot.svg: 机器人图标
        target.svg: 目标图标
        web.svg: 因特网图标
    avatar.jpg: 头像
    favicon.ico: vue自带，没用到
    github_logo.png: GitHub图标，一开始用的github的logo，后面改成github的svg图标
    index.html: 本应该是vue自带的默认模板，但是一开始没有生成，后来手动创建的，用来定义头信息，主要是title.


.github/workflows/deploy.yml: 自动部署到 GitHub Pages 的工作流配置

配置文件
    vite.config.js: Vite 构建工具配置
    package.json: 项目依赖和脚本配置
    eslint.config.js: ESLint 代码检查配置
    jsconfig.json: JavaScript 项目配置
    .prettierrc.json: Prettier 代码格式化配置