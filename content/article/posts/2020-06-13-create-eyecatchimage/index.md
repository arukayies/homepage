---
title: GASでアイキャッチ画像を自動生成させるツールを作ってみた
author: arukayies
type: post
date: 2020-06-12T17:03:37+00:00
excerpt: 誰でも作れるように詳細な解説付きです！背景画像と文字入り画像を合成して、Wordpressにアップロードまで自動化しています。
url: /gas/wordpress-rest-api/create-eyecatchimage
share: true
toc: true
comment: true
page_type:
  - default
update_level:
  - high
the_review_type:
  - Product
the_review_rate:
  - 5
snap_isAutoPosted:
  - 1591981419
snapEdIT:
  - 1
snapTW:
  - |
    s:214:"a:1:{i:0;a:8:{s:2:"do";s:1:"0";s:9:"msgFormat";s:27:"%TITLE% 
    %URL% 
    
    %HTAGS%";s:8:"attchImg";s:1:"0";s:9:"isAutoImg";s:1:"A";s:8:"imgToUse";s:0:"";s:9:"isAutoURL";s:1:"A";s:8:"urlToUse";s:0:"";s:4:"doTW";i:0;}}";
last_modified:
  - 2024-11-19 13:19:19
categories:
  - WordpressAPI
tags:
  - GAS
  - Google Apps Script
  - WordPress
  - WordpressAPI
  - スプレッドシート

archives: ["2020年6月"]
---
ブロガーの皆さんはアイキャッチ画像をどのように作成しているでしょうか。
</p>
<p>
私は<strong><span class="bold-red">無料</span></strong>でおしゃれに画像をデザインできる<strong>Canva</strong>で作成しています。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-check">
  <a rel="noopener" href="https://www.canva.com/" title="Just a moment..." class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://s.wordpress.com/mshots/v1/https%3A%2F%2Fwww.canva.com%2F?w=160&#038;h=90" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://s.wordpress.com/mshots/v1/https%3A%2F%2Fwww.canva.com%2F?w=160&#038;h=90" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        Just a moment...
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://www.canva.com/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://www.canva.com/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          www.canva.com
        </div>
      </div>
    </div>
  </div></a>
</div>

<strong>Canva</strong>は操作がとても簡単で素材もたくさんあり、不満はないのですが
</p>
<p>
それでも<span class="fz-22px"><strong>毎回画像を作成するのは手間です。</strong></span>
</p>
<p>
そこで今回はGASで作る
</p>
<p>
<strong><span class="fz-32px"><span class="bold-green">アイキャッチ画像自動生成ツール</span> </span></strong>
</p>
<p>
の作り方を紹介します！
</p>
<p>
ブログで使用するので、<strong><span class="bold-green">WordPress自動アップロード機能</span></strong> もあります！

<div class="wp-block-cocoon-blocks-iconlist-box iconlist-box blank-box list-check-circle block-box has-border-color has-icon-color has-red-border-color has-red-icon-color">
  <div class="iconlist-title">
    ツールで出来ること！
  </div>
  
  <ul class="wp-block-list">
    <li>
      背景画像にメイン・サブタイトル文字を重ねて合成することできます！
    </li>
    <li>
      重ねる位置は自由に設定できます！
    </li>
    <li>
      画像をWordpressにアップロードすることができます！
    </li>
    <li>
      アップロードする画像の詳細情報も設定できます！
    </li>
  </ul>
</div>

ツールの全体像はこんな動きになります。<figure class="wp-block-embed is-type-rich is-provider-twitter wp-block-embed-twitter">

<div class="wp-block-embed__wrapper">
  <blockquote class="twitter-tweet" data-width="550" data-dnt="true">
    <p lang="ja" dir="ltr">
      GASを使ってアイキャッチ画像を自動生成させるツールを作ってみた！<br /><br />背景画像と文字入り画像を合成して、Wordpressにアップロードまで自動化しています。<br /><br />①Canvasで画像合成<br />②PhantomJSで合成した画像をキャプチャ<br />③Wordpressにアップロード<br /><br />こんな流れです！<a href="https://twitter.com/hashtag/%E8%87%AA%E5%8B%95%E5%8C%96?src=hash&ref_src=twsrc%5Etfw">#自動化</a> <a href="https://twitter.com/hashtag/GAS?src=hash&ref_src=twsrc%5Etfw">#GAS</a> <a href="https://twitter.com/hashtag/GoogleAppsScript?src=hash&ref_src=twsrc%5Etfw">#GoogleAppsScript</a> <a href="https://t.co/ytJnbMHxWr">pic.twitter.com/ytJnbMHxWr</a>
    </p>&mdash; arukayies (@arukayies) 
    
    <a href="https://twitter.com/arukayies/status/1267800221796274177?ref_src=twsrc%5Etfw">June 2, 2020</a>
  </blockquote>
</div></figure> 

コードだけ見れればいい！って方は<a href="https://github.com/arukayies/create-eyecatchImage">こちら</a>をどうぞ！

<div class="cstmreba">
  <div class="kaerebalink-box">
    <div class="kaerebalink-image">
      <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F2735ffa9683d4fe24bd8643fa95fab2a%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" ><img decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/20010009784798064741_1.jpg" style="border: none;" /></a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
    </div>
    
    <div class="kaerebalink-info">
      <div class="kaerebalink-name">
        <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F2735ffa9683d4fe24bd8643fa95fab2a%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >詳解！Ｇｏｏｇｌｅ　Ａｐｐｓ　Ｓｃｒｉｐｔ完全入門 ＧｏｏｇｌｅアプリケーションとＧｏｏｇｌｅ　Ｗｏｒ 第３版/秀和システム/高橋宣成</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        
        <div class="kaerebalink-powered-date">
          posted with <a rel="nofollow noopener" href="https://kaereba.com" target="_blank">カエレバ</a>
        </div>
      </div>
      
      <div class="kaerebalink-detail">
      </div>
      
      <div class="kaerebalink-link1">
        <div class="shoplinkrakuten">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F2735ffa9683d4fe24bd8643fa95fab2a%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >楽天市場</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkamazon">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612578&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3Dgoogle%2520apps%2520script%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612578p_id170pc_id185pl_id4062.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkyahoo">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1615240&#038;p_id=1225&#038;pc_id=1925&#038;pl_id=18502&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2Fsearch.shopping.yahoo.co.jp%2Fsearch%3Fp%3Dgoogle%2520apps%2520script" target="_blank" >Yahooショッピング</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1615240p_id1225pc_id1925pl_id18502.gif" width="1" height="1" style="border:none;" />
        </div>
      </div>
    </div>
    
    <div class="booklink-footer">
    </div>
  </div>
</div>

## 作業の流れ

<div class="wp-block-cocoon-blocks-iconlist-box iconlist-box blank-box list-hand-o-right block-box has-border-color has-icon-color has-key-color-border-color has-key-color-icon-color">
  <div class="iconlist-title">
    作り方の流れ
  </div>
  
  <ul class="wp-block-list">
    <li>
      Googleドライブに画像合成用のスクリプトを作成
    </li>
    <li>
      画像合成用のスクリプトを公開
    </li>
    <li>
      アイキャッチ画像の設定を入力するスプレッドシートを作成
    </li>
    <li>
      スプレッドシートにスクリプトを作成する
    </li>
  </ul>
</div>

## Googleドライブに画像合成用のスクリプトを作成

### 新規でGoogle Apps Scriptを作成

以前の記事で手順を紹介しているので、参考にしてください。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a href="https://arukayies.com/gas/line_bot/line-bot-with-gas#toc2" title="GASで作る簡単なLINE BOTの作り方" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-160x90.png 160w, https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-120x68.png 120w, https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-320x180.png 320w, https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        GASで作る簡単なLINE BOTの作り方
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        GASで作るLINE BOTの簡単な作り方を紹介します！
      </div>
    </div>
    
    <div class="blogcard-footer internal-blogcard-footer cf">
      <div class="blogcard-site internal-blogcard-site">
        <div class="blogcard-favicon internal-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain internal-blogcard-domain">
          arukayies.com
        </div>
      </div>
      
      <div class="blogcard-date internal-blogcard-date">
        <div class="blogcard-post-date internal-blogcard-post-date">
          2024.11.19
        </div>
      </div>
    </div>
  </div></a>
</div><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="1024" height="368" src="https://arukayies.com/wp-content/uploads/2020/06/新規でGoogle-Apps-Scriptを作成-1024x368.png" alt="新規でGoogle Apps Scriptを作成" class="wp-image-3722" srcset="https://arukayies.com/wp-content/uploads/2020/06/新規でGoogle-Apps-Scriptを作成-1024x368.png 1024w, https://arukayies.com/wp-content/uploads/2020/06/新規でGoogle-Apps-Scriptを作成-300x108.png 300w, https://arukayies.com/wp-content/uploads/2020/06/新規でGoogle-Apps-Scriptを作成-768x276.png 768w, https://arukayies.com/wp-content/uploads/2020/06/新規でGoogle-Apps-Scriptを作成.png 1129w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">作成直後</figcaption></figure> 

### doGet.js のコードを貼り付ける

コード.gs に以下を貼り付けます。<figure class="wp-block-image aligncenter size-large is-resized">

<img loading="lazy" decoding="async" width="1024" height="659" src="https://arukayies.com/wp-content/uploads/2020/06/doGet.js-のコードを貼り付ける-1024x659.png" alt="doGet.js のコードを貼り付ける" class="wp-image-3723" style="aspect-ratio:714/459" srcset="https://arukayies.com/wp-content/uploads/2020/06/doGet.js-のコードを貼り付ける-1024x659.png 1024w, https://arukayies.com/wp-content/uploads/2020/06/doGet.js-のコードを貼り付ける-300x193.png 300w, https://arukayies.com/wp-content/uploads/2020/06/doGet.js-のコードを貼り付ける-768x494.png 768w, https://arukayies.com/wp-content/uploads/2020/06/doGet.js-のコードを貼り付ける.png 1036w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">**doGet.js**を貼り付ける</figcaption></figure> 

### index.html のコードを貼り付ける

『ファイル』→『New』→『HTMLファイル』を選択します。ファイル名は『index』にします。<figure class="wp-block-image aligncenter size-large is-resized">

<img loading="lazy" decoding="async" width="524" height="357" src="https://arukayies.com/wp-content/uploads/2020/06/HTMLファイルを選択.png" alt="HTMLファイルを選択" class="wp-image-3725" style="aspect-ratio:524/357" srcset="https://arukayies.com/wp-content/uploads/2020/06/HTMLファイルを選択.png 524w, https://arukayies.com/wp-content/uploads/2020/06/HTMLファイルを選択-300x204.png 300w" sizes="(max-width: 524px) 100vw, 524px" /> <figcaption class="wp-element-caption">HTMLファイルを作成</figcaption></figure> 

index.htmlに以下を貼り付けます<figure class="wp-block-image aligncenter size-large is-resized">

<img loading="lazy" decoding="async" width="874" height="523" src="https://arukayies.com/wp-content/uploads/2020/06/index.html-のコードを貼り付ける.png" alt="index.html のコードを貼り付ける" class="wp-image-3727" style="aspect-ratio:714/427" srcset="https://arukayies.com/wp-content/uploads/2020/06/index.html-のコードを貼り付ける.png 874w, https://arukayies.com/wp-content/uploads/2020/06/index.html-のコードを貼り付ける-300x180.png 300w, https://arukayies.com/wp-content/uploads/2020/06/index.html-のコードを貼り付ける-768x460.png 768w" sizes="(max-width: 874px) 100vw, 874px" /> <figcaption class="wp-element-caption">index.htmlを貼り付ける</figcaption></figure> 

#### **width と height**を変更する

<span class="bold-red">背景画像のサイズによって、4行目のwidth と height は変更してください。</span>

1200と630の数値を変更してください。

## 画像合成用のスクリプトを公開

以前の記事で手順を紹介しているので、参考にしてください。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a href="https://arukayies.com/gas/line_bot/line-bot-with-gas#toc7" title="GASで作る簡単なLINE BOTの作り方" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-160x90.png 160w, https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-120x68.png 120w, https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-320x180.png 320w, https://arukayies.com/wp-content/uploads/2019/07/line-bot-with-gas-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        GASで作る簡単なLINE BOTの作り方
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        GASで作るLINE BOTの簡単な作り方を紹介します！
      </div>
    </div>
    
    <div class="blogcard-footer internal-blogcard-footer cf">
      <div class="blogcard-site internal-blogcard-site">
        <div class="blogcard-favicon internal-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain internal-blogcard-domain">
          arukayies.com
        </div>
      </div>
      
      <div class="blogcard-date internal-blogcard-date">
        <div class="blogcard-post-date internal-blogcard-post-date">
          2024.11.19
        </div>
      </div>
    </div>
  </div></a>
</div>

取得したURLは次の手順で使います！<figure class="wp-block-image aligncenter size-large is-resized">

<img loading="lazy" decoding="async" width="513" height="310" src="https://arukayies.com/wp-content/uploads/2020/06/スクリプトを公開.png" alt="スクリプトを公開" class="wp-image-3728" style="aspect-ratio:513/310" srcset="https://arukayies.com/wp-content/uploads/2020/06/スクリプトを公開.png 513w, https://arukayies.com/wp-content/uploads/2020/06/スクリプトを公開-300x181.png 300w" sizes="(max-width: 513px) 100vw, 513px" /> <figcaption class="wp-element-caption">スクリプトを公開</figcaption></figure> 

## アイキャッチ画像の設定を入力するスプレッドシートを作成

公開しているスプレッドシートにアクセスします。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-detail">
  <a rel="noopener" href="https://docs.google.com/spreadsheets/d/1PukL2_BbWfTHvxlKHnap0LpAgv4jveFS_H7aJtv0Xpk/edit?usp=sharing" title="アイキャッチ画像生成ツール(外部公開用)" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://lh7-us.googleusercontent.com/docs/AHkbwyID8mZbojXMm3KggCBIqy3-Vk6QqwJm8VryX-NX1xmpOj_EHCX3a1KBx_6k93JuCaKNPwVapfa3P1o-5EZQ0yvoNakEzFih8PtoHvHn3KWQxDNsuOt6=w1200-h630-p" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://lh7-us.googleusercontent.com/docs/AHkbwyID8mZbojXMm3KggCBIqy3-Vk6QqwJm8VryX-NX1xmpOj_EHCX3a1KBx_6k93JuCaKNPwVapfa3P1o-5EZQ0yvoNakEzFih8PtoHvHn3KWQxDNsuOt6=w1200-h630-p" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        アイキャッチ画像生成ツール(外部公開用)
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://docs.google.com/spreadsheets/d/1PukL2_BbWfTHvxlKHnap0LpAgv4jveFS_H7aJtv0Xpk/edit?usp=sharing&#038;usp=embed_facebook" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://docs.google.com/spreadsheets/d/1PukL2_BbWfTHvxlKHnap0LpAgv4jveFS_H7aJtv0Xpk/edit?usp=sharing&#038;usp=embed_facebook" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          docs.google.com
        </div>
      </div>
    </div>
  </div></a>
</div>

『ファイル』→『コピーを作成』からマイドライブにコピーします。<figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="1024" height="620" src="https://arukayies.com/wp-content/uploads/2020/06/マイドライブにコピー-1024x620.png" alt="マイドライブにコピー" class="wp-image-3731" srcset="https://arukayies.com/wp-content/uploads/2020/06/マイドライブにコピー-1024x620.png 1024w, https://arukayies.com/wp-content/uploads/2020/06/マイドライブにコピー-300x182.png 300w, https://arukayies.com/wp-content/uploads/2020/06/マイドライブにコピー-768x465.png 768w, https://arukayies.com/wp-content/uploads/2020/06/マイドライブにコピー-1536x930.png 1536w, https://arukayies.com/wp-content/uploads/2020/06/マイドライブにコピー.png 1840w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">マイドライブにコピー</figcaption></figure> 

## スプレッドシートにスクリプトを作成する

コピーしたスプレッドシートを開き、スクリプトエディタを開きます。<figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="788" height="459" src="https://arukayies.com/wp-content/uploads/2020/06/スクリプトエディタを開く.png" alt="スクリプトエディタを開く" class="wp-image-3732" srcset="https://arukayies.com/wp-content/uploads/2020/06/スクリプトエディタを開く.png 788w, https://arukayies.com/wp-content/uploads/2020/06/スクリプトエディタを開く-300x175.png 300w, https://arukayies.com/wp-content/uploads/2020/06/スクリプトエディタを開く-768x447.png 768w" sizes="(max-width: 788px) 100vw, 788px" /> <figcaption class="wp-element-caption">スクリプトエディタを開く</figcaption></figure> 

### createEyecatchImage.js のコードを貼り付ける

コード.gs に以下を貼り付けます<figure class="wp-block-image aligncenter size-large is-resized">

<img loading="lazy" decoding="async" width="1024" height="458" src="https://arukayies.com/wp-content/uploads/2020/06/createEyecatchImage.js-のコードを貼り付ける-1024x458.png" alt="createEyecatchImage.js のコードを貼り付ける" class="wp-image-3734" style="aspect-ratio:716/320" srcset="https://arukayies.com/wp-content/uploads/2020/06/createEyecatchImage.js-のコードを貼り付ける-1024x458.png 1024w, https://arukayies.com/wp-content/uploads/2020/06/createEyecatchImage.js-のコードを貼り付ける-300x134.png 300w, https://arukayies.com/wp-content/uploads/2020/06/createEyecatchImage.js-のコードを貼り付ける-768x344.png 768w, https://arukayies.com/wp-content/uploads/2020/06/createEyecatchImage.js-のコードを貼り付ける.png 1184w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">createEyecatchImage.jsを貼り付ける</figcaption></figure> 

### シートIDとシート名を書き換える

３行目「シートID」と４行目「シート名」をコピーしたスプレッドシートの情報に書き換えます。<figure class="wp-block-image size-large is-resized">

<img loading="lazy" decoding="async" width="962" height="1024" src="https://arukayies.com/wp-content/uploads/2020/06/シートIDとシート名を書き換える-962x1024.png" alt="シートIDとシート名を書き換える" class="wp-image-3737" style="aspect-ratio:714/760" srcset="https://arukayies.com/wp-content/uploads/2020/06/シートIDとシート名を書き換える-962x1024.png 962w, https://arukayies.com/wp-content/uploads/2020/06/シートIDとシート名を書き換える-282x300.png 282w, https://arukayies.com/wp-content/uploads/2020/06/シートIDとシート名を書き換える-768x817.png 768w, https://arukayies.com/wp-content/uploads/2020/06/シートIDとシート名を書き換える-1444x1536.png 1444w, https://arukayies.com/wp-content/uploads/2020/06/シートIDとシート名を書き換える.png 1720w" sizes="(max-width: 962px) 100vw, 962px" /> <figcaption class="wp-element-caption">シートIDとシート名の例</figcaption></figure> 

### GASの公開URLを書き換える

30行目の部分を[前の手順で取得したURL][1]に書き換えます。

### width と heightを変更する

<span class="bold-red">PhantomJsCloudでキャプチャする位置を背景画像のサイズによって変えてください。</span>

32行目から47行目の数字をキャプチャする位置によって調整します。

1200と630の数値の変更と59はGoogleで表示されるヘッダー部分です。

### PhantomJsCloudのAPIキーを書き換える

50行目の部分を[PhantomJsCloud][2]で取得したAPIキーに書き換えます。

APIキーの取得方法はこちらの記事が参考になりました！

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a rel="noopener" href="https://tonari-it.com/scraping-javascript-gas-phantomjscloud/#toc1" title="GASでPhantomJS Cloudを利用してWebページをスクレイピング" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://tonari-it.com/wp-content/uploads/ad8592f68f50d130b9c6921206f01db4.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://tonari-it.com/wp-content/uploads/ad8592f68f50d130b9c6921206f01db4.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        GASでPhantomJS Cloudを利用してWebページをスクレイピング
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        「JavaScriptで動作するWebページ（動的サイト)を色々な言語でスクレイピング」することをシリーズでお伝えしています。今回はGoogle Apps ScriptとPhantomJS Cloudでスクレイピングします！
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://tonari-it.com/scraping-javascript-gas-phantomjscloud/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://tonari-it.com/scraping-javascript-gas-phantomjscloud/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          tonari-it.com
        </div>
      </div>
    </div>
  </div></a>
</div>

### WordPressのユーザー名、パスワードを書き換える

57行目の部分をWordpressのユーザー名、パスワードに書き換えます。

WordPressAPIのユーザー名、パスワードは以前の記事を参考にしてください。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a href="https://arukayies.com/gas/wordpress-rest-api/postreport#toc2" title="GASを使ってWordPressに自動投稿する方法" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2020/02/postreport-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2020/02/postreport-160x90.png 160w, https://arukayies.com/wp-content/uploads/2020/02/postreport-120x68.png 120w, https://arukayies.com/wp-content/uploads/2020/02/postreport-320x180.png 320w, https://arukayies.com/wp-content/uploads/2020/02/postreport-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        GASを使ってWordPressに自動投稿する方法
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        WordPress を使って広告収入を得たい！でもサラリーマンで毎日記事を書いてる時間はない！だったら、自動化だ！と思い立って、年末からいろいろ試していました「くら」です。まずはメインである。記事の自動投稿をGASを使って自動化します。プロ...
      </div>
    </div>
    
    <div class="blogcard-footer internal-blogcard-footer cf">
      <div class="blogcard-site internal-blogcard-site">
        <div class="blogcard-favicon internal-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain internal-blogcard-domain">
          arukayies.com
        </div>
      </div>
      
      <div class="blogcard-date internal-blogcard-date">
        <div class="blogcard-post-date internal-blogcard-post-date">
          2024.11.19
        </div>
      </div>
    </div>
  </div></a>
</div>

### WordPressのURLを書き換える

67行目の部分をWordpressのURLに書き換えます。

このブログだったら『**https://arukayies.com**』に書き換えます。

## 使い方

### 『画像生成』ボタンにスクリプトを割り当てる

ボタンにスクリプトを割り当てます。『**main**』と割り当ててください。

<div class="wp-block-cocoon-blocks-column-2 column-wrap column-2 column-2-2-1-1 layout-box">
  <div class="wp-block-cocoon-blocks-column-left column-left">
    <figure class="wp-block-image aligncenter size-large"><img loading="lazy" decoding="async" width="706" height="437" src="https://arukayies.com/wp-content/uploads/2020/06/ボタンにスクリプトを割り当て.png" alt="ボタンにスクリプトを割り当て" class="wp-image-3741" srcset="https://arukayies.com/wp-content/uploads/2020/06/ボタンにスクリプトを割り当て.png 706w, https://arukayies.com/wp-content/uploads/2020/06/ボタンにスクリプトを割り当て-300x186.png 300w" sizes="(max-width: 706px) 100vw, 706px" /><figcaption class="wp-element-caption">ボタンにスクリプトを割り当て</figcaption></figure>
  </div>
  
  <div class="wp-block-cocoon-blocks-column-right column-right">
    <p>
      　
    </p><figure class="wp-block-image size-large">
    
    <img loading="lazy" decoding="async" width="1024" height="445" src="https://arukayies.com/wp-content/uploads/2020/06/mainを割り当て-1024x445.png" alt="mainを割り当て" class="wp-image-3742" srcset="https://arukayies.com/wp-content/uploads/2020/06/mainを割り当て-1024x445.png 1024w, https://arukayies.com/wp-content/uploads/2020/06/mainを割り当て-300x130.png 300w, https://arukayies.com/wp-content/uploads/2020/06/mainを割り当て-768x334.png 768w, https://arukayies.com/wp-content/uploads/2020/06/mainを割り当て.png 1091w" sizes="(max-width: 1024px) 100vw, 1024px" /><figcaption class="wp-element-caption">mainを割り当て</figcaption></figure>
  </div>
</div>

### アイキャッチ画像の設定を入力

#### 背景画像のURLを設定

シートのB2セルには**背景画像のURL**を設定します。

<div class="wp-block-cocoon-blocks-column-2 column-wrap column-2 column-2-2-1-1 layout-box">
  <div class="wp-block-cocoon-blocks-column-left column-left">
    <p>
      背景画像のURLはこちらです。
    </p><figure class="wp-block-image size-large">
    
    <img decoding="async" src="https://arukayies.com/wp-content/uploads/2020/06/gas-background.png" alt="背景画像" /><figcaption class="wp-element-caption">背景画像</figcaption></figure>
  </div>
  
  <div class="wp-block-cocoon-blocks-column-right column-right">
    <p>
      生成された画像はこちらです。
    </p><figure class="wp-block-image size-large">
    
    <img decoding="async" src="https://arukayies.com/wp-content/uploads/2020/06/create-eyecatchimage-sample.png" alt="合成された画像" /><figcaption class="wp-element-caption">合成された画像</figcaption></figure>
  </div>
</div>

#### メインタイトル・サブタイトルの設定

シートのB3・B4セルには**メインタイトル・サブタイトルの文字列**を設定します。

ダミー画像生成、モックアップ用画像作成ツールの <https://placehold.jp/> を使って、文字入りの画像を生成しています。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-official">
  <a rel="noopener" href="https://placehold.jp/" title="placehold.jp | 簡単！ダミー画像作成" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://placehold.jp/eeeeee/666666/200x200.png?text=placehold.jp" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://placehold.jp/eeeeee/666666/200x200.png?text=placehold.jp" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        placehold.jp | 簡単！ダミー画像作成
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        簡単！ダミー画像生成、モックアップ用画像作成ツール。文字やサイズ、メモを入れた仮の画像を簡単に作成できます。
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://placehold.jp/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://placehold.jp/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          placehold.jp
        </div>
      </div>
    </div>
  </div></a>
</div>

以下のコード部分で文字入りの画像を生成しています。

<span class="bold-red">画像サイズ・レイアウトはコードの21行目と22行目の数値を変えて使ってください。</span>

生成された画像はこんな感じです。これを背景に合成しています。

<div class="wp-block-cocoon-blocks-column-2 column-wrap column-2 column-2-2-1-1 layout-box">
  <div class="wp-block-cocoon-blocks-column-left column-left">
    <figure class="wp-block-image size-large"><img decoding="async" src="https://arukayies.com/wp-content/uploads/2020/06/5_1200x250.png" alt="メインタイトルの画像" /><figcaption class="wp-element-caption">メインタイトルの画像</figcaption></figure>
  </div>
  
  <div class="wp-block-cocoon-blocks-column-right column-right">
    <figure class="wp-block-image size-large"><img decoding="async" src="https://arukayies.com/wp-content/uploads/2020/06/5_500x130.png" alt="サブタイトルの画像" /><figcaption class="wp-element-caption">サブタイトルの画像</figcaption></figure> 
    
    <p>
    </p>
  </div>
</div>

#### 画像の合成位置の設定

シートのB6〜B9はメインタイトル・サブタイトルの画像の合成位置の設定になります。

背景画像のサイズ・合成画像のサイズを意識した位置関係で設定してください。

何度か試してみて、納得いく合成位置を試してみてください。

#### 画像の詳細設定

WordPressのメディアライブラリに反映される情報を事前に設定できます。<figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="706" height="316" src="https://arukayies.com/wp-content/uploads/2020/06/アイキャッチ画像の設定例.png" alt="アイキャッチ画像の設定例" class="wp-image-3753" srcset="https://arukayies.com/wp-content/uploads/2020/06/アイキャッチ画像の設定例.png 706w, https://arukayies.com/wp-content/uploads/2020/06/アイキャッチ画像の設定例-300x134.png 300w" sizes="(max-width: 706px) 100vw, 706px" /> <figcaption class="wp-element-caption">アイキャッチ画像の設定例</figcaption></figure> <figure class="wp-block-image aligncenter size-large"><img loading="lazy" decoding="async" width="1024" height="441" src="https://arukayies.com/wp-content/uploads/2020/06/画像情報の設定-1024x441.jpg" alt="メディアライブラリ" class="wp-image-3751" srcset="https://arukayies.com/wp-content/uploads/2020/06/画像情報の設定-1024x441.jpg 1024w, https://arukayies.com/wp-content/uploads/2020/06/画像情報の設定-300x129.jpg 300w, https://arukayies.com/wp-content/uploads/2020/06/画像情報の設定-768x331.jpg 768w, https://arukayies.com/wp-content/uploads/2020/06/画像情報の設定-1536x662.jpg 1536w, https://arukayies.com/wp-content/uploads/2020/06/画像情報の設定-2048x882.jpg 2048w" sizes="(max-width: 1024px) 100vw, 1024px" /><figcaption class="wp-element-caption">メディアライブラリ</figcaption></figure> 

### 『画像生成』ボタンを押下する

すべての設定が設定できたら、『画像生成』ボタンを押下します！

<span class="fz-36px"><strong><span class="fz-20px">これが生成される画像です！！！！！</span></strong></span><figure class="wp-block-image aligncenter size-large is-resized">

<img decoding="async" src="https://arukayies.com/wp-content/uploads/2020/06/create-eyecatchimage-sample.png" alt="合成された画像" style="aspect-ratio:714/374" /> <figcaption class="wp-element-caption">合成された画像</figcaption></figure> 

## まとめ

<div class="wp-block-cocoon-blocks-balloon-ex-box-1 speech-wrap sb-id-1 sbs-stn sbp-l sbis-cb cf block-box cocoon-block-balloon">
  <div class="speech-person">
    <figure class="speech-icon"><img decoding="async" src="https://arukayies.com/wp-content/uploads/2019/12/icon-1.png" alt="くら" class="speech-icon-image" /></figure>
    

  </div>
  
  <div class="speech-balloon">
    <p>
      構想から完成まで4ヶ月ぐらいかかってしまいました。。。
    </p><figure class="wp-block-image size-large is-resized">
    
    <img loading="lazy" decoding="async" width="833" height="315" src="https://arukayies.com/wp-content/uploads/2020/06/フラグ.png" alt="2月の記事内容" class="wp-image-3760" style="aspect-ratio:496/187" srcset="https://arukayies.com/wp-content/uploads/2020/06/フラグ.png 833w, https://arukayies.com/wp-content/uploads/2020/06/フラグ-300x113.png 300w, https://arukayies.com/wp-content/uploads/2020/06/フラグ-768x290.png 768w" sizes="(max-width: 833px) 100vw, 833px" /><figcaption class="wp-element-caption">2月の記事・・・。</figcaption></figure>
  </div>
</div>

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a href="https://arukayies.com/gas/wordpress-rest-api/postreport-thumbnail#toc8" title="GASを使ってアイキャッチ画像付でWordPressに自動投稿する方法" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2020/02/postreport-thumbnail-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2020/02/postreport-thumbnail-160x90.png 160w, https://arukayies.com/wp-content/uploads/2020/02/postreport-thumbnail-120x68.png 120w, https://arukayies.com/wp-content/uploads/2020/02/postreport-thumbnail-320x180.png 320w, https://arukayies.com/wp-content/uploads/2020/02/postreport-thumbnail-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        GASを使ってアイキャッチ画像付でWordPressに自動投稿する方法
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        以前の記事でこんなことを紹介しました。この記事ではタイトルと内容を自動投稿させるのみでしたが、今回はアイキャッチ画像付きで自動投稿させます！前回同様にプログラム未経験者でもコピペで実現できるように手順を紹介します。詳解！Ｇｏｏｇｌｅ　Ａｐｐ...
      </div>
    </div>
    
    <div class="blogcard-footer internal-blogcard-footer cf">
      <div class="blogcard-site internal-blogcard-site">
        <div class="blogcard-favicon internal-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://arukayies.com" alt="" class="blogcard-favicon-image internal-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain internal-blogcard-domain">
          arukayies.com
        </div>
      </div>
      
      <div class="blogcard-date internal-blogcard-date">
        <div class="blogcard-post-date internal-blogcard-post-date">
          2024.11.19
        </div>
      </div>
    </div>
  </div></a>
</div>

<div class="cstmreba">
  <div class="kaerebalink-box">
    <div class="kaerebalink-image">
      <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F2735ffa9683d4fe24bd8643fa95fab2a%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" ><img decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/20010009784798064741_1.jpg" style="border: none;" /></a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
    </div>
    
    <div class="kaerebalink-info">
      <div class="kaerebalink-name">
        <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F2735ffa9683d4fe24bd8643fa95fab2a%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >詳解！Ｇｏｏｇｌｅ　Ａｐｐｓ　Ｓｃｒｉｐｔ完全入門 ＧｏｏｇｌｅアプリケーションとＧｏｏｇｌｅ　Ｗｏｒ 第３版/秀和システム/高橋宣成</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        
        <div class="kaerebalink-powered-date">
          posted with <a rel="nofollow noopener" href="https://kaereba.com" target="_blank">カエレバ</a>
        </div>
      </div>
      
      <div class="kaerebalink-detail">
      </div>
      
      <div class="kaerebalink-link1">
        <div class="shoplinkrakuten">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2F2735ffa9683d4fe24bd8643fa95fab2a%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >楽天市場</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkamazon">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612578&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3Dgoogle%2520apps%2520script%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612578p_id170pc_id185pl_id4062.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkyahoo">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1615240&#038;p_id=1225&#038;pc_id=1925&#038;pl_id=18502&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2Fsearch.shopping.yahoo.co.jp%2Fsearch%3Fp%3Dgoogle%2520apps%2520script" target="_blank" >Yahooショッピング</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1615240p_id1225pc_id1925pl_id18502.gif" width="1" height="1" style="border:none;" />
        </div>
      </div>
    </div>
    
    <div class="booklink-footer">
    </div>
  </div>
</div>

 [1]: https://arukayies.com/gas/wordpress-rest-api/create-eyecatchImage#toc6
 [2]: https://phantomjscloud.com/index.html
