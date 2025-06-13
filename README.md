# 液化水素貯槽WG サイト

このリポジトリはGitHub Pagesで公開される研究プロジェクト用Webサイトです。

## ローカルテスト
[https://docs.github.com/ja/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll](Jekyll を使用して GitHub Pages サイトをローカルでテストする)

## カスタマイズ上の留意点

### _includes/head.html

[https://github.com/jekyll/minima/blob/v2.5.1/_includes/head.html] をコピーして修正

+ custom-head.html を読み込むように修正

### _layouts/home.html

[https://github.com/jekyll/minima/blob/v2.5.1/_layouts/home.html] をコピーして修正

+ h1.page-heading を縦横中央ぞろえにするために div.page-heading-wrapper を親に配置
