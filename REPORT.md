/src - 源代码目录
    App.vue: 应用程序的根组件，包含全局样式和路由视图
    main.js: 应用程序入口文件，负责创建 Vue 实例并配置路由

/src/components - 可复用组件
    Navbar.vue: 顶部导航栏组件，包含响应式菜单
    /icons: 图标组件集合，自带的，没有用到
        IconDocumentation.vue: 文档图标
        IconTooling.vue: 工具图标
        IconEcosystem.vue: 生态系统图标
        IconCommunity.vue: 社区图标
        IconSupport.vue: 支持图标

/src/views - 页面视图组件
    Home.vue: 主页视图
    About.vue: About页面视图
    Skills.vue: 技能和教育经历展示页面
    Projects.vue: 项目列表页面
    ProjectDetail.vue: 项目详情页
    Blog.vue: 博客列表页面
    BlogDetail.vue: 博客详情页
    Links.vue: 相关链接页面（一开始AI生成的，后面在导航栏中删去了，没调用）

/src/router - 路由配置
    index.js: 定义所有路由规则，包括动态路由参数

/public - 静态资源
    /data: JSON 数据文件
        about.json: about页面个人信息数据
        blog.json: 博客文章数据
        projects.json: 项目数据
        skills.json: 技能数据
    /icons: 网站图标资源
        Bell.svg: 铃铛图标
        gitHub.svg: GitHub图标
        email.svg: 邮件图标
        phone.svg: 电话图标
        Resume.svg: 简历图标
        User.svg: 用户图标
    avatar.jpg: 头像图片
    favicon.ico: vue自带，没用到
    github_logo.png: GitHub图标，一开始用的github的logo，后面改成github的svg图标
    index.html: 本应该是vue自带的默认模板，但是一开始没有生成，后来手动创建的，尝试修改网页title的时候进行过修改，但是没有实际使用
