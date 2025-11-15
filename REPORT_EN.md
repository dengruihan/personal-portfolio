/src - Source code directory
    App.vue: Root component of the application, containing global styles and router-view
    main.js: Application entry point, responsible for creating Vue instance and configuring router

/src/components - Reusable components
    Navbar.vue: Top navigation bar component with responsive menu
    /icons: Collection of icon components (built-in, not used)
        IconDocumentation.vue: Documentation icon
        IconTooling.vue: Tooling icon
        IconEcosystem.vue: Ecosystem icon
        IconCommunity.vue: Community icon
        IconSupport.vue: Support icon

/src/views - Page view components
    Home.vue: Homepage view
    About.vue: About page view
    Skills.vue: Skills and education experience display page
    Projects.vue: Project list page
    ProjectDetail.vue: Project detail page
    Blog.vue: Blog list page
    BlogDetail.vue: Blog detail page
    Links.vue: Related links page (initially AI-generated, later removed from navigation and unused)

/src/router - Router configuration
    index.js: Defines all routing rules, including dynamic route parameters

/public - Static assets
    /data: JSON data files
        about.json: Personal information data for About page
        blog.json: Blog post data
        projects.json: Project data
        skills.json: Skills data
        <!-- most of the information can edit at here easily -->
    /icons: Website icon resources
        bell.svg: Bell icon
        blog.svg: Blog icon
        book.svg: Book icon
        chart.svg: Chart icon
        cloud.svg: Cloud computing icon
        email.svg: Email icon
        expert.svg: Expert icon
        eye.svg: Eye icon
        gear.svg: Gear icon
        gitHub.svg: GitHub icon
        lightbulb.svg: Lightbulb icon
        paint.svg: Paint palette icon
        phone.svg: Phone icon
        project.svg: Block icon representing projects
        robot.svg: Robot icon
        target.svg: Target icon
        web.svg: Internet icon
    avatar.jpg: Profile picture
    favicon.ico: Vue default (unused)
    github_logo.png: GitHub icon (initially used GitHub logo, later changed to GitHub SVG icon)
    index.html: Should be Vue's default template, but wasn't generated initially. Created manually later to define header information, mainly title.

.github/workflows/deploy.yml: Workflow configuration for automatic deployment to GitHub Pages

Configuration files
    vite.config.js: Vite build tool configuration
    package.json: Project dependencies and scripts configuration
    eslint.config.js: ESLint code checking configuration
    jsconfig.json: JavaScript project configuration
    .prettierrc.json: Prettier code formatting configuration
