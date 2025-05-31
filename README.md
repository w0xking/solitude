‎layout/includes/inject/body.pug
+2
-4
Original file line number	Diff line number	Diff line change
@@ -50,7 +50,7 @@ div
      script(src=url_for(theme.cdn.medium_zoom))
    if theme.fancybox
      script(src=url_for(theme.cdn.fancyapps_ui))
  if (theme.brevity.home_mini && theme.brevity.enable) || theme.carousel
  if (theme.brevity.home_mini && theme.brevity.enable)
    script(src=url_for(theme.cdn.swiper_js))

  if theme.post_ai.enable
@@ -108,9 +108,7 @@ div
    if theme.mermaid
      script.
        mermaid.run();
    if is_home() && theme.carousel && site.posts.data.filter(item => item.recommend === true).slice(0, 6) || false
      script.
        carousel_swiper()
    if theme.busuanzi && (theme.aside.siteinfo.uv || theme.aside.siteinfo.pv || is_post() && theme.post.meta.pv)
      script(defer pjax src=url_for(theme.cdn.busuanzi_js))
------------------------------------------------------------------------------
‎layout/includes/inject/head.pug
+1
-1
Original file line number	Diff line number	Diff line change
@@ -9,7 +9,7 @@ if theme.capsule.enable || theme.music.enable || theme.brevity.enable && theme.b
    link(rel="stylesheet", href=url_for(theme.cdn.aplayer_css))

// swiper
if (theme.brevity.home_mini && theme.brevity.enable) || theme.carousel
if (theme.brevity.home_mini && theme.brevity.enable)
    link(rel="stylesheet", href=url_for(theme.cdn.swiper_css))

// fancybox ui
------------------------------------------------
‎layout/includes/widgets/home/carousel.pug
-74
This file was deleted.
-----------------------------------------------------
‎layout/index.pug
-2
Original file line number	Diff line number	Diff line change
@@ -14,8 +14,6 @@ block content
            .recent-posts#recent-posts
                if theme.comment.hot_tip.enable
                    include ./includes/widgets/third-party/hot/index.pug
                if theme.carousel && is_home_first_page()
                    include ./includes/widgets/home/carousel.pug
                for post, index in page.posts.sort("-sticky" || "-date").data
                    include ./includes/widgets/home/postList


\layout\includes\footer.pug
//-a.footer-bar-link(href=_p('hexo'))
                        = _p('framework_by') + 'Hexo'
                    //-a.footer-bar-link(href=_p('repo'))
                        = _p('theme_by') + 'Solitude'




