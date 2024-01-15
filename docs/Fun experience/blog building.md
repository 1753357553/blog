# 用Mkdocs和Material主题搭建与维护个人技术博客

## 介绍
对于技术博客而言，我们或许不需要炫酷的动画效果，但是我们需要一个简洁、易于维护的博客框架。本文将介绍如何使用 MkDocs 和 Material 主题搭建一个简洁、易于维护的技术博客。
## Mkdocs是什么？
MkDocs 是一个用于构建项目文档的工具，它可以将 Markdown 文件转换为静态网站。MkDocs 由 Python 编写，使用 Python-Markdown 解析 Markdown 文件，使用 Pygments 语法高亮代码，使用 Jinja2 模板引擎渲染 Markdown 文件。
## Material主题是什么？
Material 主题是一个基于 Material Design 的 MkDocs 主题，它提供了一个简洁、现代的界面，支持多种语言，支持自定义主题颜色，支持搜索、导航、侧边栏、标签、分类、评论、Google Analytics、Disqus、多种插件等功能。
## 如何安装和使用Mkdocs?
[MkDocs中文文档](https://hellowac.github.io/mkdocs-docs-zh/)
[MkDocs官方原文档](https://www.mkdocs.org/getting-started/)
### Mkdocs的安装
Mkdocs可以直接通过pip安装
`
```python``python
pip install mkdocs
```
运行mkdocs --version来检查一切是否正常。
```python
mkdocs --version
```
如果未安装python或已安装python但未安装pip请先自行装好在执行以上步骤
### Mkdocs的使用
##### 第一步：创建项目
```python
mkdocs new my-project
```
这一步会在当前目录下创建一个名为my-project的文件夹，该文件夹包含以下内容
```python
my-project/
├── docs/
│   └── index.md
└── mkdocs.yml
```
其中docs文件夹即是我们要搭建的网站内容的存放目录，mkdocs.yml用于配置Mkdocs，是本次搭建的重中之重，也是最难的部分。index.md是网站默认的首页，我们可以自行更改。
##### 第二步：启动网站
```python
cd my-project
mkdocs serve
```
这一步将会启动一个本地服务器，我们可以在浏览器中访问http://127.0.0.1:8000/查看网站。这一步使用了MkDocs的内置服务器，每次修改完，点击保存，网站就会自动刷新。
##### 第三步：构建网站
```
mkdocs build
```
这一步将会在主目录下生成site文件夹，其中包含该项目构建的静态网站的全部源文件，我们只需将该文件夹下的内容部署到服务器上即可。
##### Mkdocs的配置
MkDocs的配置文件是mkdocs.yml，我们可以在其中配置网站的名称、描述、主题、导航栏、侧边栏、插件等。
```
site_name: My Project
site_description: A short description of my project.
site_author: Your Name
site_url: https://example.com
site_dir: site
site_favicon: images/favicon.ico
# ...
```
这部分暂时先不动，建议直接基于material主题模板进行配置修改。nav配置导航栏和所有文章的结构。默认的文件存放位置是docs，但是我们可以通过docs_dir配置文件存放位置。

## 如何安装和使用Material主题
[Material主题文档](https://squidfunk.github.io/mkdocs-material/)
### Material的安装
Material可以通过pip安装
```python
pip install mkdocs-material
```
### 配置Material主题
Material提供了非常多的配置悬着，可以根据自己需求结合官方文档进行配置。具体可以参考如下配置。
> 原作者文章链接https://www.zhihu.com/question/29755481/answer/3329235340?utm_campaign=&utm_medium=social&utm_oi=1465757294314684416&utm_psn=1729840522947129344&utm_source=qq
```python
# 项目信息
site_name: Eureka! # 项目名称
site_url: https://localhost:端口/ # 我在nginx中使用的是8000端口，如果你使用的是80端口，可以直接写成https://localhost/。
site_author: Shuaiwen Cui # 作者
site_description: >- # 项目描述
  Welcome to Shaun's rabbit hole. This site serves as a personal knowledge base for me to record my thoughts and ideas. It is also a place for me to share my knowledge and experience with the world. I hope you find something useful here. 

# 代码仓库信息
repo_name: Shuaiwen-Cui/Infinity # 仓库名称
repo_url: https://github.com/Shuaiwen-Cui/Infinity.git/ # 仓库地址

# 版权信息
copyright: Copyright &copy; 2023 ~ now |   Shuaiwen Cui (Shaun)

# 配置
theme:
  custom_dir: material/overrides # 自定义文件夹，对于个别页面，如果你不想使用主题的默认样式，可以在这里进行修改，使用里面的文件覆盖主题的默认文件。具体可以参考material官方文档。
  name: material # 主题名称，Material已经是最优秀的选择了，相信我。
  logo: static/images/logo.png # logo 图片
  language: en # 默认语言
  features: # 功能  
    - announce.dismiss # 可以叉掉公告的功能
    - content.action.edit # 编辑按钮，似乎没啥用
    - content.action.view # 查看按钮，似乎没啥用
    - content.code.annotate # 代码注释，具体不清楚
    - content.code.copy # 复制代码按钮
    # - content.code.select # 选择代码按钮
    # - content.tabs.link # 链接标签
    - content.tooltips # 不太清楚呢这个
    # - header.autohide # 自动隐藏header
    - navigation.expand # 默认展开导航栏
    - navigation.footer # 底部导航栏
    - navigation.indexes # 索引按钮可以直接触发文件，而不是只能点击其下属选项浏览，这个功能可以给对应的section提供很好的预览和导航功能
    # - navigation.instant # 瞬间加载 最好注释掉，多语言切换这个会导致跳回首页
    - navigation.instant.prefetch # 预加载
    - navigation.instant.progress # 进度条
    - navigation.path # 导航路径， 目前好像没啥用
    # - navigation.prune # 只构建可见的页面
    - navigation.sections # 导航栏的section
    - navigation.tabs # 顶级索引被作为tab
    - navigation.tabs.sticky # tab始终可见
    - navigation.top # 开启顶部导航栏
    - navigation.tracking # 导航栏跟踪
    - search.highlight # 搜索高亮
    - search.share # 搜索分享
    - search.suggest # 搜索建议
    - toc.follow # 目录跟踪-页面右侧的小目录
    # - toc.integrate # 目录跟踪集成到左侧大目录中
  palette:
    - media: "(prefers-color-scheme)" # 主题颜色
      scheme: slate
      primary: black
      accent: indigo
      toggle:
        icon: material/link
        name: Switch to light mode
    - media: "(prefers-color-scheme: light)" # 浅色
      scheme: default
      primary: indigo
      accent: indigo
      toggle:
        icon: material/toggle-switch
        name: Switch to dark mode
    - media: "(prefers-color-scheme: dark)" # 深色
      scheme: slate
      primary: black
      accent: indigo
      toggle:
        icon: material/toggle-switch-off
        name: Switch to system preference
  font: # 字体，大概率不需要换
    text: Roboto
    code: Roboto Mono
  favicon: assets/favicon.png # 网站图标 似乎不需要管
  icon: # 一些用到的icon
    logo: logo
    previous: fontawesome/solid/angle-left
    next: fontawesome/solid/angle-right
    tag:
      default-tag: fontawesome/solid/tag
      hardware-tag: fontawesome/solid/microchip
      software-tag: fontawesome/solid/laptop-code

# Plugins
plugins:
  - tags # 标签功能插件
  - blog # 博客功能插件
  - rss: # rss订阅插件 - 不太懂是干嘛的目前
      match_path: blog/posts/.* 
      date_from_meta:
        as_creation: date
      categories:
        - categories
        - tags 
  # - social # 目前我开启会报错，还没研究透 
  - search: # 搜索插件
      separator: '[\s\u200b\-_,:!=\[\]()"`/]+|\.(?!\d)|&[lg]t;|(?!\b)(?=[A-Z][a-z])' # 分隔符
  - minify: # 压缩插件
      minify_html: true
  # - privacy # 隐私插件
  - i18n: # 多语言插件
      docs_structure: suffix # 抄来的，不太懂
      fallback_to_default: true # 抄来的，不太懂
      reconfigure_material: true # 抄来的，不太懂
      reconfigure_search: true # 抄来的，不太懂
      languages: # 多语言配置 - 需要小心一点
        - locale: en
          default: true # 默认语言
          name: English
          build: true # 是否构建
          # site_name: Infinity
        - locale: zh
          name: 简体中文
          build: true
          nav_translations: # 导航栏翻译，不可以有缩进
            HOME: 首页
            ABOUT: 关于
            SPONSORSHIP: 赞助
            CS: 计算机
            CODING: 编程
            EMBEDDED-SYS: 嵌入式系统
            DSP: 数字信号处理
            PERCEPTION: 感知
            ACTUATION: 执行
            IOT: 物联网
            CLOUD: 云
            CLOUD-TECH: 云技术
            HANDS-ON: 上手实践
            Have A Server: 拥有一台服务器
            Server Configuration: 服务器配置
            Get A Domain Name: 获得一个域名
            AI: 人工智能
            RESEARCH: 研究
            PROJECT: 项目
# Hooks - 讲真，这个东西我还没搞懂
# hooks:
#   - material/overrides/hooks/shortcodes.py
#   - material/overrides/hooks/translations.py

# 额外配置项
extra:
  generator: false # 是否显示生成器
  status: # 不是很懂有什么用
    new: Recently added
    deprecated: Deprecated
  analytics: # 分析工具， 我反正没用到
    provider: google
    property: !ENV GOOGLE_ANALYTICS_KEY
    feedback: # feedback form
      title: Was this page helpful?
      ratings:
        - icon: material/thumb-up-outline
          name: This page was helpful
          data: 1
          note: >-
            Thanks for your feedback!
        - icon: material/thumb-down-outline
          name: This page could be improved
          data: 0
          note: >- 
            Thanks for your feedback! Help us improve this page by
            using our <a href="..." target="_blank" rel="noopener">feedback form</a>.
  # alternate: # 由上面那个i18n插件提供的多语言功能，这个似乎就不需要了。 这个是官方文档的例子，但是官方没有提供很详细的例子，所以我也不知道怎么用。
  #   - name: English
  #     link: /en/ 
  #     lang: en
  #   - name: Chinese
  #     link: /zh/
  #     lang: zh
  social: # 社交媒体
    - icon: fontawesome/solid/house
      link: http://www.cuishuaiwen.com/
    - icon: fontawesome/brands/github
      link: https://github.com/Shuaiwen-Cui
    - icon: fontawesome/brands/linkedin
      link: https://www.linkedin.com/in/shaun-shuaiwen-cui/
    - icon: fontawesome/brands/researchgate
      link: https://www.researchgate.net/profile/Shuaiwen-Cui
    - icon: fontawesome/brands/orcid
      link: https://orcid.org/0000-0003-4447-6687
    - icon: fontawesome/brands/twitter
      link: https://twitter.com/ShuaiwenC
  tags: # 自定义标签
    Default: default-tag
    Hardware: hardware-tag
    Software: software-tag
  # consent: # 征求同意 Cookie
  #   title: Cookie consent
  #   description: >- 
  #     We use cookies to recognize your repeated visits and preferences, as well
  #     as to measure the effectiveness of our documentation and whether users
  #     find what they're searching for. With your consent, you're helping us to
  #     make our documentation better.

# 扩展
markdown_extensions: # markdown extensions
  - abbr
  - admonition
  - attr_list
  - def_list
  - footnotes
  - md_in_html
  - toc:
      permalink: true
  - pymdownx.arithmatex:
      generic: true
  - pymdownx.betterem:
      smart_enable: all
  - pymdownx.caret
  - pymdownx.details
  - pymdownx.emoji:
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
      emoji_index: !!python/name:material.extensions.emoji.twemoji
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.keys
  - pymdownx.magiclink:
      normalize_issue_symbols: true
      repo_url_shorthand: true
      user: squidfunk
      repo: mkdocs-material
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.snippets:
      auto_append:
        - includes/mkdocs.md
  - pymdownx.superfences:
      custom_fences:
        - name: mermaid
          class: mermaid
          format: !!python/name:pymdownx.superfences.fence_code_format
  - pymdownx.tabbed:
      alternate_style: true
      combine_header_slug: true
      slugify: !!python/object/apply:pymdownx.slugs.slugify
        kwds:
          case: lower
  - pymdownx.tasklist:
      custom_checkbox: true
  - pymdownx.tilde

# 导航树 - 请按照我的做法来做，否则可能无法正常工作。引号可以省略。开头的点和斜杠也可以省略 ("./HOME/about.md" 或 Home/about.md) 。注意，导航树这里的文件名是 filename.md 这样的，但在文件夹中，它实际上被命名为 filename.en.md 和 filename.zh.md。我猜测默认是英文，所以, index.en.md 和 index.md 是一样的。i18n插件会自动识别文件名，然后根据文件名的后缀来切换语言。所以，如果你想添加一个新页面，你需要添加两个文件，一个是 filename.en.md，另一个是 filename.zh.md。其中，filename.en.md 也可以被命名为 filename.md，但是 filename.zh.md 不能被命名为 filename.md，否则会导致无法识别。
nav: 
  - HOME: 
      - "index.md"
      - ABOUT: "./HOME/about.md"
      - SPONSORSHIP: "./HOME/sponsorship.md"
  - CS: 
      - "./CS/CS.md"
  - CODING: 
      - "./CODING/coding.md"
  - EMBEDDED-SYS: 
      - "./EMBEDDED-SYS/embedded-sys.md"
  - DSP: 
      - "./DSP/dsp.md"
  - PERCEPTION: 
      - "./PERCEPTION/perception.md"
  - ACTUATION: 
      - "./ACTUATION/actuation.md"
      - ROS: "./ACTUATION/ROS/ros.md"
  - IOT: 
      - "./IOT/iot.md"
  - CLOUD: 
      - "./CLOUD/cloud.md"
      - CLOUD-TECH: "./CLOUD/CLOUD-TECH/cloud-tech.md"
      - HANDS-ON:
          - Have A Server: "./CLOUD/HANDS-ON/001-HAVE-A-SERVER/have-a-server.md"
          - Server Configuration: "./CLOUD/HANDS-ON/002-SERVER-CONFIG/server-config.md"
          - Get A Domain Name: "./CLOUD/HANDS-ON/003-DOMAIN-NAME/domain-name.md"
  - AI: 
      - "./AI/ai.md"
  - RESEARCH: 
      - "./RESEARCH/research.md"
  - PROJECT: 
      - "./PROJECT/project.md"
      - TECH-BLOG: "./PROJECT/TECH-BLOG/mkdocs_and_material.md"
```
除了外观，所有的配置功能基本上都在这个配置文件中，所以你可以根据自己的需求进行修改。
## 使用Git&Github部署至服务器
### 前要
如果你熟悉Git和Github，那么这种方法会更加方便。我们可以在本地使用Git管理网站，然后将网站上传至Github，然后在服务器上使用Git拉取网站，然后部署。

如果还不会使用Git&Github，建议学习并使用
[Windows系统Git详细安装教程](https://blog.csdn.net/mukes/article/details/115693833)
[密码:7aik，电子书，特别棒的入门书籍，强烈建议看这个](https://wwc.lanzouo.com/i4BWko0gfje)


注意，最好在服务器上构建网站，因为MkDocs的版本可能会发生变化，如果本地构建的网站上传至服务器，可能会导致网站无法正常显示。可以在.gitignore文件中添加site，这样就不会将site文件夹上传至服务器。
```python
/site
```
服务器如何安装python，pip，以及git在此不再赘述
### 构建本地库与远程库并建立关联
##### 构建本地库
首先cd到项目文件夹如上文提及的my-project，初始化好仓库，要依次执行以下命令
```python
git init 
git add .
(可选)新建.gitignore文件并写入site/
git commit -m "First commit"
```
##### GitHub上建立远程仓库并关联
1. 在GitHub上新建一个空仓库
2. 将本地git仓库与GitHub进行关联，比如
```
git remote add origin git@github.com:xxx/xxx.git
```
至此已经建立了本地仓库与远程仓库的连接。
### 项目部署与维护
接下来从本地将项目推送到GitHub远程仓库里
```
git push -u origin
```
然后在服务器上将项目clone下来。如果这一步报错Permission Denied(publickey)的话，就需要设置SSH key
具体请参考[在服务器上git clone github项目的过程](https://blog.csdn.net/a61022706/article/details/122228080)
```
git clone git@githun.com:xxx/xxx.git
```
然后进入到项目文件夹构建网站
```
mkdocs build
```
再配置nginx指向site目录即可
后续维护只需本地更改后push，服务器pull即可
