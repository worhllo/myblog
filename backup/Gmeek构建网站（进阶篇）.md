## 一、主题配置 👀
### 1.1手动模式（默认）
这种模式就是当访问者第一次打开博客页面时，呈现的是亮主题。
访问者可以通过页面右上角的按钮随意切换（亮/暗/跟随系统），当切换过后，会自动在浏览器存储目前的选择，之后访问者用同一浏览打开博客任何页面，则自动为上次选择的模式。

```
"themeMode":"manual",
"dayTheme":"light",
"nightTheme":"dark",
```
### 1.2 固定模式
```
"themeMode":"fix",    定义固定
"dayTheme":"light",   定义固定的主题，`light`则永远为亮主题，`dark`则永远为暗主题，用户无法切换
"nightTheme":"github-light",    定义`utterances`评论框的永久固定主题。
```
#### 1.2.1 固定亮主题
```
"themeMode":"fix",
"dayTheme":"light",
"nightTheme":"github-light",
```
#### 1.2.2 固定暗主题
```
"themeMode":"fix",
"dayTheme":"dark",
"nightTheme":"dark-blue",
```
#### 1.2.3 utterances评论框的主题选择有：
亮主题：github-light boxy-light preferred-color-scheme
暗主题：github-dark github-dark-orange icy-dark dark-blue photon-dark gruvbox-dark

##　二、右上角的按钮配置 👀
在首页上部的右侧有一些按钮，配置方式如下：

### 2.1站内链接
* 关于页面和友情链接
1. 添加config.json配置
```
   "singlePage":["about"],

```
2. 添加一个Labels标签为about，在你的issue里面写一个文章，然后配置Labels为about即可
3. 手动全局生成一次。
> [!IMPORTANT]
> about标签只可以添加给唯一一篇issue
如果有多个singlePage，可以这样定义"singlePage":["link","about"],
about和link这两个图标的SVG是内置的无需定义iconList，其他则需要自己定义


* 站外链接
如果你的about页面是站外的，或者想定义其他的站外链接，例如music。下面以添加music页面按钮为示例。

1. 添加config.json配置
   此处iconList自定义了图标的SVG，exlink定义了外部链接的地址



```
"iconList":{"music":"M12.7 0.9L7.3 0.9C6 0.9 4.9 2 4.9 3.3L4.9 10.1C4.5 9.9 4.1 9.8 3.6 9.8C2.1 9.8 0.9 11 0.9 12.4C0.9 13.9 2.1 15.1 3.6 15.1C5 15.1 6.2 13.9 6.2 12.4L6.2 3.3C6.2 2.7 6.7 2.2 7.3 2.2L12.7 2.2C13.3 2.2 13.8 2.7 13.8 3.3L13.8 7.5C13.4 7.3 12.9 7.1 12.4 7.1C11 7.1 9.8 8.3 9.8 9.8C9.8 11.2 11 12.4 12.4 12.4C13.9 12.4 15.1 11.2 15.1 9.8L15.1 3.3C15.1 2 14 0.9 12.7 0.9ZM3.6 13.8C2.8 13.8 2.2 13.2 2.2 12.4C2.2 11.7 2.8 11.1 3.6 11.1C4.3 11.1 4.9 11.7 4.9 12.4C4.9 13.2 4.3 13.8 3.6 13.8ZM12.4 11.1C11.7 11.1 11.1 10.5 11.1 9.8C11.1 9 11.7 8.4 12.4 8.4C13.2 8.4 13.8 9 13.8 9.8C13.8 10.5 13.2 11.1 12.4 11.1ZM12.4 11.1"},
"exlink":{"music":"https://music.meekdai.com"},

```
2. 手动全局生成一次。
3. SVG图标格式
   使用iconList自定义SVG图标必须是16px大小的，建议使用github的Octicons 图标

[点击跳转Octicons图标链接](https://primer.style/foundations/icons/#16px)
[点击跳转大佬自己转换的Octicons图标path列表](https://gist.github.com/Meekdai/f6375fe2740428af39d90f1afa678fdc)
  
## 三、提示标签 👀
Github的语法里面有5种警报强调信息，分别是NOTE TIP IMPORTANT WARNING CAUTION
在写文章的时候，适当使用可以提高文章的可读性

* 使用方式：
```
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

```
* 效果：
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.

## 四、折叠显示 👀
* 使用方式：
```
<details>
    <summary>展开</summary>
    <pre><code>
    # 这里空一行，下面开始写代码
    # 在这里写折叠的代码
    # 最后这两行结束标签一定要顶格写且不能接在代码后面！！！
    </code></pre>
</details>

```
* 效果：
<details>
    <summary>展开</summary>
    <pre><code>
    # 这里空一行，下面开始写代码
    # 在这里写折叠的代码
    # 最后这两行结束标签一定要顶格写且不能接在代码后面！！！
    </code></pre>
</details>

## 五、文章插入html标签 👀
Github由于安全考虑，是不允许使用iframe等标签的，而且在issues插入的图片也会自动转换为github的地址。
为了文章的多样性，在Gmeek的v2.19版本中添加了支持html标签的功能。

使用方式：
在需要添加html标签的位置使用code方式，并且后面紧跟着Gmeek-html，然后才是html标签。

1. 图片

`Gmeek-html<img src="https://picsum.photos/400">`
1. 内嵌框架iframe-网站

`Gmeek-html<iframe style='border-radius:12px' src="https://music.meekdai.com/#35" width="100%" height="150px" frameborder="0" allowfullscreen="true"></iframe>`
3. 内嵌框架iframe-音乐

`Gmeek-html<iframe style='border-radius:12px' src='https://open.spotify.com/embed/track/0U3fV7K4WFfVRgLGEAKh3g?utm_source=generator' width='100%' height='100' frameBorder='0' allowfullscreen='' allow='autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture' loading='lazy'></iframe>`
4. 内嵌框架iframe-视频

`Gmeek-html<iframe style='border-radius:12px' src="//player.bilibili.com/player.html?isOutside=true&aid=1604800941&bvid=BV1qm421M7Xs&cid=1557311907&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="200px"></iframe>`


##　六、static文件夹使用 👀
使用方式：在自己的仓库根目录下新建一个文件夹，名称必须是static。
然后在static文件内上传一些自己的文件，比如avatar.svg文件。
通过手动全局生成一次成功后，你就可以通过 xxx.github.io/avatar.svg 访问了。

> [!CAUTION]
> 需要特别注意区分script head allHead 等这些键的用途
在全局生成的时候，Actions会自动把static文件夹的所有内容拷贝到docs文件夹内。方便用户把docs当成一个目录部署到CF等其他服务器中。

##　七、插件 👀
为了使得Gmeek的功能更加的丰富，添加了插件功能，目前已经有几个插件可以使用。

1. Vercount浏览计数GmeekVercount.js

全站添加，只需要在config.json文件内添加配置

```
"allHead":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekVercount.js'></script>",
```
单个文章页添加，只需要在文章最后一行添加如下

```
<!-- ##{"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekVercount.js'></script>"}## -->
```
2. TOC目录GmeekTOC.js

全站添加，只需要在config.json文件内添加配置

```
"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekTOC.js'></script>",
```
单个文章页添加，只需要在文章最后一行添加如下

```
<!-- ##{"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekTOC.js'></script>"}## -->
```
3. ArticleTOC目录articletoc.js
本插件由Tiengming编写，也是一个非常不错的TOC目录插件。配置方式和上面一样，只需要替换地址为如下地址即可。
```
https://blog.meekdai.com/Gmeek/plugins/articletoc.js
```
4. 灯箱插件lightbox.js
本插件由Tiengming编写，可以放大浏览文章中的图片，适合一些图片较多的文章。

全站添加，只需要在config.json文件内添加配置

```
"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/lightbox.js'></script>",
```
单个文章页添加，只需要在文章最后一行添加如下

```
<!-- ##{"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/lightbox.js'></script>"}## -->
```
5. 多插件使用
   
全站添加，所有文章页使用TOC目录和灯箱插件，需要这样添加配置文件：

```
"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekTOC.js'></script><script src='https://blog.meekdai.com/Gmeek/plugins/lightbox.js'></script>",
```
单个文章页添加，单个文章使用TOC目录和灯箱插件，需要这样添加配置文件：

```
<!-- ##{"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekTOC.js'></script><script src='https://blog.meekdai.com/Gmeek/plugins/lightbox.js'></script>"}## -->
```

> [!CAUTION]
> 需要特别注意区分script head allHead 等这些键的用途
* 单篇文章自定义参数，自定义单篇文章页面的style和script

```
<!-- ##{"style":"<style>#postBody{font-size:20px}</style>"}## -->
<!-- ##{"script":"<script async src='//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js'></script>"}## -->

```
* 单篇文章多种自定义参数，可同时一起添加多种自定义参数：

```
<!-- ##{"script":"<script async src='//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js'></script>","style":"<style>#postBody{font-size:20px}</style>","timestamp":1490764800}## -->

```
* 全局文章自定义参数，添加全局文章页面的style和script，在config.json文件中添加

```
"style":"<style>#postBody{font-size:20px}</style>",
"script":"<script async src='//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js'></script>",

```
##　八、其他设置 👀
1. 导入以前的文章
如需修改发布时间，可以在文章最后一行添加如下代码。里面的时间是采用时间戳的形式，可以用如下时间形式转换网站转换。

```
<!-- ##{"timestamp":1490764800}## -->
<!-- ##{"script":"<script async src='//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js'></script>","style":"<style>#postBody{font-size:20px}</style>","timestamp":1490764800}## -->

```
2. 置顶博客文章
只需要Pin issue后，手动全局生成一次即可。

3. 删除文章
只需要Close issue或者Delete issue后，再手动全局生成一次即可。


