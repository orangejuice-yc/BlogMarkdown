# blog-hexo
## 安装melody主题：
git clone -b master https://github.com/Molunerfinn/hexo-theme-melody themes/melody
修改themes/melody目录下_config.yml文件
```markdown
# ---------------
# Theme color for customize
# Notice: color value must in double quotes like "#000" or may cause error!
# ---------------
theme_color:
  enable: true
  main: "#49B1F5"
  paginator: "#00C4B6"
  button_hover: "#FF7242"
  text_selection: "#00C4B6"
  link_color: "#858585"
  hr_color: "#A4D8FA"
  tag_start_color: "#A4D8FA"
  tag_end_color: "#1B9EF3"
  header_text_color: "#EEEEEE"
  footer_text_color: "#EEEEEE"


# Main menu navigation
menu:
  Home: /
  Archives: /archives
  Tags: /tags
  Categories: /categories
  #XXX: /xxx

# Favicon
# ---------------
favicon: /melody-favicon.ico

# PWA
# See https://github.com/JLHwung/hexo-offline
# ---------------
pwa:
  enable: false
  manifest: /manifest.json
  # If you don't want to trouble, just ignore the following things
  # See https://realfavicongenerator.net/
  # theme_color: "#49B1F5"
  # apple_touch_icon: /apple-touch-icon.png
  # favicon_32_32: /favicon-32x32.png
  # favicon_16_16: /favicon-16x16.png
  # mask_icon: /safari-pinned-tab.svg

# Highlight theme
# ---------------
highlight_theme: darker

code_word_wrap: true

# Nav settings
# see the icon_name in fontawesome website.
# And you need to add the `fa` or `fab` prefix by your self.
# ---------------
#social:
#icon_name fa: url
#icon_name fab: url

# Algolia search
# ---------------
algolia_search:
  enable: false
  hits:
    per_page: 10

# Local search
# Please see doc for more details: https://molunerfinn.com/hexo-theme-melody-doc/third-party-support.html#local-search
# ---------------
local_search:
  enable: false

# MathJax
# Please see doc for more details: https://molunerfinn.com/hexo-theme-melody-doc/third-party-support.html#mathjax
# ---------------
mathjax:
  enable: false
#   cdn: https://cdn.jsdelivr.net/npm/mathjax/MathJax.js?config=TeX-AMS-MML_HTMLorMML

# KaTeX
# Please see doc for more details: https://molunerfinn.com/hexo-theme-melody-doc/third-party-support.html#katex
# ---------------
katex:
  enable: false
  cdn:
    css: https://cdn.jsdelivr.net/npm/katex@latest/dist/katex.min.css
  hide_scrollbar: true

# Toggle fireworks (IE >= 10)
# ---------------
fireworks: true

# Analysis
# ---------------
baidu_analytics:

google_analytics:

# Tencent_analytics ID
tencent_analytics:

# stylesheets loaded in the <head>
# ---------------
stylesheets:
  - /css/index.css
# scripts loaded in the end of the body
# ---------------
scripts:
  - /js/utils.js
  - /js/fancybox.js
  - /js/sidebar.js
  - /js/copy.js
  - /js/fireworks.js
  - /js/transition.js
  - /js/scroll.js
  - /js/head.js

# cdn for third-party library
# ---------------
cdn:
  css:
    fontawesome: https://cdn.jsdelivr.net/npm/font-awesome@latest/css/font-awesome.min.css
    # fontawesomeV5: https://use.fontawesome.com/releases/v5.3.1/css/all.css
  js:
    anime: https://cdn.jsdelivr.net/npm/animejs@latest/anime.min.js
    jquery: https://cdn.jsdelivr.net/npm/jquery@latest/dist/jquery.min.js
    fancybox: https://cdn.jsdelivr.net/npm/@fancyapps/fancybox@latest/dist/jquery.fancybox.min.js
    velocity: https://cdn.jsdelivr.net/npm/velocity-animate@latest/velocity.min.js
    velocity-ui: https://cdn.jsdelivr.net/npm/velocity-ui-pack@latest/velocity.ui.min.js

# Post info settings
# ---------------
avatar: 

top_img: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1573029701101&di=fec5f3a1606d2a21b449b7e8f437998c&imgtype=0&src=http%3A%2F%2F00.minipic.eastday.com%2F20170330%2F20170330044720_920fd3e0ab07e2f6e28b04d44b733f4b_4.jpeg # false or url of img

top_img_height: 0 # best range: 60 - 100

post_meta:
  date_type: created # created or updated
  categories: true
  tags: true

toc:
  enable: true
  # number: true

post_copyright:
  enable: true
  license: CC BY-NC-SA 4.0
  license_url: https://creativecommons.org/licenses/by-nc-sa/4.0/

# Please see doc for more details: https://molunerfinn.com/hexo-theme-melody-doc/theme-config.html#auto-excerpt
auto_excerpt:
  enable: true
  length: 300

# slide
# For reveal.js config, see https://github.com/hakimel/reveal.js#configuration
slide:
  separator: ---
  separator_vertical: --
  charset: utf-8
  theme: black
  # optional
  mouseWheel: false
  transition: slide
  transitionSpeed: default
  parallaxBackgroundImage: ""
  parallaxBackgroundSize: ""
  parallaxBackgroundHorizontal: null
  parallaxBackgroundVertical: null

# QR_code:
# - itemlist:
#     img:
#     text:

# adv:
# enable: false
# info:

# Share System
# ---------------
addThis:
  enable: false
  #pubid:

# sharejs:
# enable: false
# disabled_sites:

# Comments System
# ---------------
disqus:
  enable: false
  #shortname:
  #count:

# laibili:
# enable: false
# uid:

# gitment
# enable: false
# owner:
# repo:
# client_id:
# client_secret:

# gitalk:
#   enable: false
#   client_id:
#   client_secret:
#   repo:
#   owner:
#   admin:

# valine comment system. https://valine.js.org
# valine:
#   enable: false # if you want use valine,please set this value is true
#   appId:  # leancloud application app id
#   appKey:  # leancloud application app key
#   notify: false # valine mail notify (true/false) https://github.com/xCss/Valine/wiki
#   verify: false # valine verify code (true/false)
#   pageSize: 10 # comment list page size
#   avatar: mm # gravatar style https://valine.js.org/#/avatar
#   lang: zh-cn # i18n: zh-cn/en
#   placeholder: Just go go # valine comment input placeholder(like: Please leave your footprints )
#   guest_info: nick,mail,link #valine comment header inf

# Footer Settings
# ---------------
since: 2019

# footer_custom_text:

ICP:
  enable: false
  #text:

# busuanzi count for PV / UV in site
busuanzi:
  # count values only if the other configs are false
  enable: true
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: <i class="fa fa-user"></i>
  site_uv_footer:
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: <i class="fa fa-eye"></i>
  site_pv_footer:
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file"></i>
  page_pv_footer:

# canvas_ribbon
# See: https://github.com/hustcc/ribbon.js
canvas_ribbon:
  enable: false
  size: 150
  alpha: 0.6
  zIndex: -1
  click_to_change: false

# Sidebar Settings
# ---------------
# links_title: Links
# links:
# Name: url

# Follow Me Button
# follow:
#   enable: true
#   url: ''
#   text: ''

# controls the sidebar showing or hidden in different pages
sidebar_display: post # all/index/post/index-none/post-none/hidden

# Ads
# ---------------
# Google Adsense
google_adsense:
  enable: false
  js: //pagead2.googlesyndication.com/pagead/js/adsbygoogle.js
  client: ca-pub-...........
  enable_page_level_ads: true

# Google Webmaster tools verification setting
# See: https://www.google.com/webmasters/
google_site_verification:

# Bing Webmaster tools verification setting
# See: https://www.bing.com/webmaster/
bing_site_verification:

# Yandex Webmaster tools verification setting
# See: https://webmaster.yandex.ru/
#yandex_site_verification:

# Baidu Webmaster tools verification setting
# See: https://ziyuan.baidu.com/site/
baidu_site_verification:

# 360 Webmaster tools verification setting
# see http://zhanzhang.so.com/
qihu_site_verification:

# avoid baidu transformation
disable_baidu_transformation: true

# 404 Page SubTitle
404Text:

```
## npm install
## 启动
```
npm run server
```
## 发布
```
npm run clean
npm run deploy
```