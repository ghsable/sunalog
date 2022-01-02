# sunalog
[sunalog](https://ghsable.github.io/sunalog/) is my Blog.

## Workflow
#### Case1
* POST/EDIT : [Netlify CMS](https://sunalog.netlify.app/admin/)
* BUILD/DEPLOY : GitHub Actions

#### Case2
* POST : `Ctrl+c` [archetypes/default.md](https://github.com/ghsable/sunalog/blob/main/archetypes/default.md) -> `Create new file` [content/post/](https://github.com/ghsable/sunalog/blob/main/content/post/)\*.md
* EDIT : `Edit this file` [content/post/](https://github.com/ghsable/sunalog/blob/main/content/post/)\*.md
* BUILD/DEPLOY : GitHub Actions

## Thanks
I used the following tools :
> * [Hugo](https://gohugo.io/) : Static Site Generator
>   * [github-style](https://github.com/MeiK2333/github-style) : Hugo's Theme
>     * ~~[utterances](https://utteranc.es/) : Comments Widget~~
>     * [Google Analytics](https://analytics.google.com/analytics/web/) : Access Analysis Service
> * ~~[freenom](https://freenom.com) : DNS-Resolver~~
> * [GitHub Actions](https://github.co.jp/features/actions) : CI/CD
>   * [actions/checkout](https://github.com/actions/checkout) : Checkout
>   * [peaceiris/actions-hugo](https://github.com/peaceiris/actions-hugo) : Setup Hugo
>   * [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages) : Deploy
> * [Netlify](https://www.netlify.com/) : PaaS
>   * [Netlify CMS](https://www.netlifycms.org/) : CMS

## License
![CC BY-NC-SA 4.0](https://raw.githubusercontent.com/ghsable/sunalog/main/static/images/uploads/by-nc-sa.webp)
