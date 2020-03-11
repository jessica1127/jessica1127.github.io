# Use Hugo to build blog
Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.
## Install Hugo
### Mac installation
```
brew install hugo
```
### Verification
```
hugo version
```
## Build a Hugo project
### Create your project
```
hugo new site [project-name]
eg: 
hugo new site Myblog
```
After your issed above command, here is the file structure under myBlog
```
.
├── archetypes # 存放生成博客的模版
├── assets # 存放被 Hugo Pipes 处理的文件
├── config # 存放 hugo 配置文件 支持 JSON YAML TOML 三种格式配置文件
├── content # 存放 markdown 文件
├── data # 存放 Hugo 处理的数据
├── layouts # 存放布局文件
├── static # 存放静态文件 图片 CSS JS文件
└── themes # 存放主题
```
### Install your themes
Offical here:  https://themes.gohugo.io/ 
I used: LeaveIt
```
cd themes
git clone https://github.com/liuzc/LeaveIt.git
```
### Modify your config.toml
```
baseURL = "https://jessica1127.github.io/" # <head> 里面的 baseurl 信息，填你的博客地址
#baseURL = "http://localhost:1313/"
title = "Jessica1127`s Blog" # 浏览器的标题
languageCode = "zh-cn" # 语言
hasCJKLanguage = true # 开启可以让「字数统计」统计汉字
theme = "LeaveIt" # 主题 (需要自己下载)
paginate = 11 # 每页的文章数
enableEmoji = true # 支持 Emoji
enableRobotsTXT = true # 支持 robots.txt
googleAnalytics = "" # Google 统计 id
preserveTaxonomyNames = true

[blackfriday]
  hrefTargetBlank = true
  nofollowLinks = true
  noreferrerLinks = true

[Permalinks]
 posts = "/:year/:filename/"
 
[menu]
  [[menu.main]]
    name = "Blog"
    url = "/posts/"
    weight = 1
  [[menu.main]]
    name = "Categories"
    url = "/categories/"
    weight = 2
  [[menu.main]]
    name = "Tags"
    url = "/tags/"
    weight = 3
  [[menu.main]]
    name = "About"
    url = "/about/"
    weight = 4

[params]
    since = 2010
    author = "Jessica"                          # Author's name
    avatar = "/images/me/avatar.png"           # Author's avatar
    subtitle = "Live beautifully, dream passionately, love completely."                  # Subtitle
    cdn_url = ""           # Base CDN URL
    home_mode = "" # post or other
    enableGitalk = true # gitalk 评论系统
    google_verification = ""
    description = "Jessica new blog since 2020" # (Meta) 描述
    keywords = "" # site keywords
    beian = ""
    baiduAnalytics = ""
    license= '本文采用<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/" target="_blank">知识共享署名-非商业性使用 4.0 国际许可协议</a>进行许可'
[params.social]
    GitHub = "https://jessica1127.github.io/"
    Twitter = "xxoo"
    Email   = "bbzhang66@gmail.com"
    Instagram = "xxoo"
    Wechat = "/images/me/wechat.png"  # Wechat QRcode image
    Facebook = "xxoo"
    Telegram = "xxoo"
    Dribbble = "xxoo"
    Medium = "xxoo"
[params.gitalk] # Github: https://github.com/gitalk/gitalk
    clientID = "" # Your client ID
    clientSecret = "" # Your client secret
    repo = "" # The repo to store comments
    owner = "" # Your GitHub ID
    admin= "" # Required. Github repository owner and collaborators. (Users who having write access to this repository)
    id= "location.pathname" # The unique id of the page.
    labels= "gitalk" # Github issue labels. If you used to use Gitment, you can change it
    perPage= 15 # Pagination size, with maximum 100.
    pagerDirection= "last" # Comment sorting direction, available values are 'last' and 'first'.
    createIssueManually= false # If it is 'false', it is auto to make a Github issue when the administrators login.
    distractionFreeMode= false # Enable hot key (cmd|ctrl + enter) submit comment.
```
## Launch and Test your blog in local
```
hugo server --buildDrafts -w
```
Notes:
--buildDrafts: 生成被标记为 「草稿」 的文档
-w: 监控更改，如果发生更改直接显示到博客上 (非常有用，这也是我最喜欢的一点特性了)

You can visit your blog here:
http://localhost:1313

## Publish your blog to Github pages
```
hugo 
```
After apply above command you can see public/ folder under myBlog.

```
cd public
git init
git remote add origin https://github.com/[Github 用户名]/[Github 用户名].github.io.git
git add -A
git commit -m "[介绍，随便写点什么，比如日期]"
git push -u origin master
```

Well done, visit your blog here: https://Github 用户名].github.io