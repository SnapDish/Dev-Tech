# SnapDish Tech Blog

![SnapDish](https://snapdish.co/v3/pc/img/book/book_logo2.png)

## 利用するツール、技術
### [GitHub Pages](https://pages.github.com/)
GitHubが提供するホスティングサービス。  
GitHubのレポジトリを用いて、webページをインターネット上に公開することができる。  
指定のレポジトリにHTML/CSSなどを置けば、サーバの準備なしに自動でwebページが提供される。  
ブランチを切ってバージョン管理したり、プルリクを活用して皆で校正したりできる。  
Gitの利点をそのままwebページ管理に活用できる！
### [Nikola](https://getnikola.com/)  
pythonで動く静的サイトジェネレータライブラリ。  
webページとして機能するために必要なスクリプトを自動生成する。  
また、Markdownなど人間が書きやすい/読みやすい記法のファイルを、
HTMLなど機械が解釈しやすいファイルに変換してくれる。  
サイトのデザインもシンプルかつモダンでクール！    
類似のライブラリとしては [Pelican][1] が有名。

[1]:https://github.com/getpelican/pelican


## 記事公開までの流れ
***社外と共有する価値のある技術的事項*** を見つけたら...
1. ブランチを切る
    1. srcブランチへ移動  
    `git checkout src`  
    1. 新しい記事のタイトルでブランチを切る  
    `git checkout -b "title"`  
    (タイトルの入力を間違えたら...)  ブランチの削除  
    `git checkout src`  
    `git checkout -d "title"`  
1. 記事を作成する(上で生成したタイトルブランチ内)
    1. new postを生成する  
    *nikola_src* ディレクトリ内  
    `nikola new_post -f markdown`  
    *nikola_src/posts* に *"title".md* が生成される  
    1. 記事を書く  
    *nikola_src/posts/title.md* にMarkdown記法で書く
1. マスターにプルリクする  
    1. *"title".md* をコミットする  
    `git add "title".md`  
    `git commit -m "title"`
    1. リモートにプッシュする  
    `git push origin "title"`  
    1. マスターブランチにプルリク
    1. エンジニアチームで検討の後、マスターにマージされる
1. 本番化  
     1. srcブランチでプル  
    `git checkout src`  
    `git pull`  
    1. Github pages にデプロイする  
    `nikola github_deploy`
