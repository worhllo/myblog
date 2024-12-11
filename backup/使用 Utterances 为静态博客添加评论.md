## utterence简介
[utterances](https://github.com/utterance/utterances)是一款基于 GitHub issues 的开源评论插件，类似于 Gitalk，支持 markdown。

网上开源的评论系统很多，例如Disqus和Gitalk，为什么选用utterances呢？

首先 Disqus 的 UI 过于冗余了，而且免费使用有广告，看起来不舒服。

Gitalk 等同样是基于 GitHub issues 的评论插件存在安全性问题。这些评论插件都是通过 OAuth 取得操作 issues 的权限，因此必须将 clientID 和 clientSecret 硬编码入 commit，而这个操作会将二者直接暴露出去。

尽管获得对 repos 的操作权限还需要授权 Token，但是这个可以通过反代 GitHub API 等手段拿到。由于 GitHub 在权限粒度上并没有进一步细分（也就是说不能只操作 issues），所以一旦拿到 Token，对方就可以删光你的 public repos，因此使用它们的风险是非常高的。

而反观Utterances 

1. 通过 GitHub App 实现，可以只对 issues 进行授权，因此没有了安全性风险。
   
2. 不需要初始化，而 Gitalk 等评论插件都是需要作者手动初始化的。
   
3. utterences是该博客系统的最佳方案，因为Gmeek的核心是All in Github

## 配置操作
### 1.安装 Utterances
首先保证自己的博客是 public 仓库。

接着打开 [utterances-GitHub App](https://github.com/apps/utterances) 点击 右上角Configure进入安装页面。

然后在打开的页面中选择 Only select repositories，并在下拉框中选择仓库（可以选择博客的仓库，也可以安装到其他仓库），然后点击 Save。

### 2.进阶配置
完成第一步之后，其实 Utterances 已经在我们的博客上配置好了，这一步是为了生成个性化的 HTML 配置插入博客。喜欢折腾的朋友可以继续。

安装完成后就会自动跳转到配置页面，也可以手动打开 Utterances。

在 repository 中填入仓库名称，按照 用户名/仓库名的格式填写

Blog Post ↔️ Issue Mapping 表示 issues 标题和博客 posts 的映射关系，我选择默认的第一项 Issue title contains page pathname。

Issue Label 表示用于评论的 issues 要不要打上 label，这一项是可选的。我选择为这些 issues 打上 Comment。

最后一项是 Theme 根据自己的喜好选择即可。

![utterances-configuration](https://imgbed.worhllo.us.kg/file/1733893960749_utterances-configuration.png)

然后就会生成一段对应选项的 HTML 配置，应该是类似于这样的：

```
<script src="https://utteranc.es/client.js"
        repo="[ENTER REPO HERE]"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>

```
直接将它插入到你的博客中对应的位置，即对应的 post 文件中即可。

