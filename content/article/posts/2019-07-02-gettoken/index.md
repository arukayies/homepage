---
title: LINE Messaging APIアクセストークンの取得方法
author: arukayies
type: post
date: 2019-07-02T13:52:19+00:00
excerpt: LINEBOTに必要なトークンの取得方法を画像付きで解説します。
url: /gas/line_bot/gettoken
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
snap_isRpstd579:
  - 1577362791
snap_isAutoPosted:
  - 1
snap_isRpstd2493:
  - 1586644574
last_modified:
  - 2024-11-19 11:34:23
snapEdIT:
  - 1
snapTW:
  - |
    s:393:"a:1:{i:0;a:12:{s:2:"do";s:1:"1";s:9:"msgFormat";s:27:"%TITLE% 
    %URL% 
    
    %HTAGS%";s:8:"attchImg";s:1:"0";s:9:"isAutoImg";s:1:"A";s:8:"imgToUse";s:0:"";s:9:"isAutoURL";s:1:"A";s:8:"urlToUse";s:0:"";s:4:"doTW";i:0;s:8:"isPosted";s:1:"1";s:4:"pgID";s:19:"1249103994514857984";s:7:"postURL";s:56:"https://twitter.com/arukayies/status/1249103994514857984";s:5:"pDate";s:19:"2020-04-11 22:36:14";}}";
categories:
  - LINE BOT
tags:
  - GAS
  - Google Apps Script
  - LINE BOT

archives: ["2019年7月"]
---
こんにちは「くら」です！
</p>
<p>
ツーリングクラブのLINEグループに<a href="https://it-trend.jp/words/chatbot">チャットボット</a>を導入しています。
</p>
<p>
こちらがその動作している様子です。

<div style="height:20px" aria-hidden="true" class="wp-block-spacer">
</div><figure class="wp-block-image aligncenter is-resized">

<img decoding="async" src="https://arukayies.com/wp-content/uploads/2019/12/img_5dfa3293bb113.gif" alt="" style="aspect-ratio:356/237" /> <figcaption class="wp-element-caption">LINEBOTが動いている様子</figcaption></figure> 

運営の手助けやコミュニケーションのきっかけになればと思い、

以下のような機能を実装しています。

<div class="wp-block-cocoon-blocks-icon-box common-icon-box block-box information-box">
  <p>
    「<strong>使い方</strong>」と発言すると、自分ができることを教えてくれます。<br />「<strong>wiki〇〇〇</strong>」と発言すると、wikiの検索結果を教えてくれます。<br />「<strong>画像〇〇〇</strong>」と発言すると、画像検索結果を教えてくれます。<br />「<strong>企画一覧</strong>」と発言すると、今後のツーリング先を教えてくれます。
  </p>
</div>

普段使っている**LINEをさらに便利したい**・[チャットボット][1]に興味がある  
そんな人の手助けになれば嬉しいです。

この記事ではLINE BOTに必要な「**LINE Messaging APIアクセストークンの取得方法**」を説明しています。

<div class="cstmreba">
  <div class="kaerebalink-box">
    <div class="kaerebalink-image">
      <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fe4320d2f4429571200cf25919da31353%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" ><img decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/20010009784798150734_1.jpg" style="border: none;" /></a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
    </div>
    
    <div class="kaerebalink-info">
      <div class="kaerebalink-name">
        <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fe4320d2f4429571200cf25919da31353%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >ＬＩＮＥ　ＢＯＴを作ろう！ Ｍｅｓｓａｇｉｎｇ　ＡＰＩを使ったチャットボットの/翔泳社/立花翔</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        
        <div class="kaerebalink-powered-date">
          posted with <a rel="nofollow noopener" href="https://kaereba.com" target="_blank">カエレバ</a>
        </div>
      </div>
      
      <div class="kaerebalink-detail">
      </div>
      
      <div class="kaerebalink-link1">
        <div class="shoplinkrakuten">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fe4320d2f4429571200cf25919da31353%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >楽天市場</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkamazon">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612578&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3DLINE%2520bot%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612578p_id170pc_id185pl_id4062.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkyahoo">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1615240&#038;p_id=1225&#038;pc_id=1925&#038;pl_id=18502&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2Fsearch.shopping.yahoo.co.jp%2Fsearch%3Fp%3DLINE%2520bot" target="_blank" >Yahooショッピング</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1615240p_id1225pc_id1925pl_id18502.gif" width="1" height="1" style="border:none;" />
        </div>
      </div>
    </div>
    
    <div class="booklink-footer">
    </div>
  </div>
</div>

## 必要なもの

<ul class="wp-block-list">
  <li>
    LINEアカウント
  </li>
</ul>

## LINE Deverlopersにログインする

1　最初に『 **LINE Developers** 』にアクセスします。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-check">
  <a rel="noopener" href="https://developers.line.biz/ja/" title="LINE Developers" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://developers.line.biz/images/ogtags/twitter-ogtag.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://developers.line.biz/images/ogtags/twitter-ogtag.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        LINE Developers
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://developers.line.biz/ja/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://developers.line.biz/ja/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          developers.line.biz
        </div>
      </div>
    </div>
  </div></a>
</div>

2　右上の『 **ログイン** 』を押下します。<figure class="wp-block-image aligncenter size-full">

<img loading="lazy" decoding="async" width="1580" height="780" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developer】ログイン押下.jpg" alt="【LINE Developers】ログイン押下" class="wp-image-2955" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developer】ログイン押下.jpg 1580w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developer】ログイン押下-300x148.jpg 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developer】ログイン押下-1024x506.jpg 1024w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developer】ログイン押下-768x379.jpg 768w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developer】ログイン押下-1536x758.jpg 1536w" sizes="(max-width: 1580px) 100vw, 1580px" /> <figcaption class="wp-element-caption">【LINE Developers】ログイン押下</figcaption></figure> 

3　『 **LINEアカウントでログイン** 』を押下します。<figure class="wp-block-image aligncenter size-full">

<img loading="lazy" decoding="async" width="555" height="605" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】LINEアカウントでログイン.png" alt="【LINE Developers】LINEアカウントでログイン" class="wp-image-2956" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】LINEアカウントでログイン.png 555w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】LINEアカウントでログイン-275x300.png 275w" sizes="(max-width: 555px) 100vw, 555px" /> <figcaption class="wp-element-caption">【LINE Developers】LINEアカウントでログイン</figcaption></figure> 

4　メールアドレスとパスワードを入力して、『 **ログイン** 』を押下します。

※　QRコードをアプリで読み取って **ログイン** することもできます。

<div class="wp-block-cocoon-blocks-column-2 column-wrap column-2 column-2-2-1-1 layout-box">
  <div class="wp-block-cocoon-blocks-column-left column-left">
    <figure class="wp-block-image size-large"><img loading="lazy" decoding="async" width="488" height="523" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】メールアドレスとパスワードでログイン.png" alt="【LINE Developers】メールアドレスとパスワードでログイン" class="wp-image-2957" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】メールアドレスとパスワードでログイン.png 488w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】メールアドレスとパスワードでログイン-280x300.png 280w" sizes="(max-width: 488px) 100vw, 488px" /><figcaption class="wp-element-caption">【LINE Developers】メールアドレスとパスワードでログイン</figcaption></figure>
  </div>
  
  <div class="wp-block-cocoon-blocks-column-right column-right">
    <figure class="wp-block-image size-large"><img loading="lazy" decoding="async" width="491" height="588" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】QRコードでログイン.png" alt="【LINE Developers】QRコードでログイン" class="wp-image-2958" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】QRコードでログイン.png 491w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】QRコードでログイン-251x300.png 251w" sizes="(max-width: 491px) 100vw, 491px" /><figcaption class="wp-element-caption">【LINE Developers】QRコードでログイン</figcaption></figure>
  </div>
</div>

## プロバイダーを作成する

<span class="number">1　</span>『 **作成** 』を押下します。<figure class="wp-block-image aligncenter size-full">

<img loading="lazy" decoding="async" width="1602" height="280" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダーを作成.png" alt="【LINE Developers】プロバイダーを作成.png" class="wp-image-2959" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダーを作成.png 1602w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダーを作成-300x52.png 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダーを作成-1024x179.png 1024w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダーを作成-768x134.png 768w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダーを作成-1536x268.png 1536w" sizes="(max-width: 1602px) 100vw, 1602px" /> <figcaption class="wp-element-caption">【LINE Developers】プロバイダーを作成.png</figcaption></figure> 

<span class="number">2　</span>プロバイダー名を入力し、『 **作成** 』を押下します。<figure class="wp-block-image aligncenter size-full">

<img loading="lazy" decoding="async" width="1318" height="544" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダー名を入力し作成を押下する.png" alt="【LINE Developers】プロバイダー名を入力し作成を押下する.png" class="wp-image-2960" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダー名を入力し作成を押下する.png 1318w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダー名を入力し作成を押下する-300x124.png 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダー名を入力し作成を押下する-1024x423.png 1024w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】プロバイダー名を入力し作成を押下する-768x317.png 768w" sizes="(max-width: 1318px) 100vw, 1318px" /> <figcaption class="wp-element-caption">【LINE Developers】プロバイダー名を入力し作成を押下する</figcaption></figure> 

## LINE Messaging APIのチャンネルを作成する

<span class="number">1　</span>プロバイダーが作成されたら、『 **Messaging API** 』を押下します。<figure class="wp-block-image aligncenter size-full">

<img loading="lazy" decoding="async" width="1337" height="668" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-APIを押下する.png" alt="【LINE Developers】Messaging APIを押下する" class="wp-image-2961" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-APIを押下する.png 1337w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-APIを押下する-300x150.png 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-APIを押下する-1024x512.png 1024w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-APIを押下する-768x384.png 768w" sizes="(max-width: 1337px) 100vw, 1337px" /> <figcaption class="wp-element-caption">【LINE Developers】Messaging APIを押下する</figcaption></figure> 

<span class="number">2　</span>チャンネルの情報を作成します。

<ul class="wp-block-list">
  <li>
    <strong>チャンネルアイコン</strong> を登録する。
  </li>
</ul><figure class="wp-block-image aligncenter size-full is-resized">

<img loading="lazy" decoding="async" width="495" height="272" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアイコンを登録する.png" alt="【LINE Developers】チャンネルアイコンを登録する" class="wp-image-2962" style="aspect-ratio:495/272" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアイコンを登録する.png 495w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアイコンを登録する-300x165.png 300w" sizes="(max-width: 495px) 100vw, 495px" /> <figcaption class="wp-element-caption">【LINE Developers】チャンネルアイコンを登録する</figcaption></figure> 

使用したフリーアイコンはこちらです。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-pickup">
  <a rel="noopener" href="http://flat-icon-design.com/" title="FLAT ICON DESIGN -フラットアイコンデザイン-" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="http://flat-icon-design.com/th01.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="http://flat-icon-design.com/th01.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        FLAT ICON DESIGN -フラットアイコンデザイン-
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        フラットデザインに最適！WEBサイトやDTPですぐ使える商用利用可能なフラットアイコン素材がフリー（無料）ダウンロードできるサイト『FLAT ICON DESIGN』
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=http://flat-icon-design.com" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=http://flat-icon-design.com" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          flat-icon-design.com
        </div>
      </div>
    </div>
  </div></a>
</div>

<ul class="wp-block-list">
  <li>
    <strong>チャンネル名</strong> を入力する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="624" height="187" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネル名を入力する.png" alt="【LINE Developers】チャンネル名を入力する" class="wp-image-2963" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネル名を入力する.png 624w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネル名を入力する-300x90.png 300w" sizes="(max-width: 624px) 100vw, 624px" /> <figcaption class="wp-element-caption">【LINE Developers】チャンネル名を入力する</figcaption></figure> 

<ul class="wp-block-list">
  <li>
    <strong>チャンネル説明</strong> を入力する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="594" height="168" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネル説明を入力する.png" alt="【LINE Developers】チャンネル説明を入力する" class="wp-image-2964" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネル説明を入力する.png 594w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネル説明を入力する-300x85.png 300w" sizes="(max-width: 594px) 100vw, 594px" /> <figcaption class="wp-element-caption">【LINE Developers】チャンネル説明を入力する</figcaption></figure> 

<ul class="wp-block-list">
  <li>
    <strong>大業種</strong> を選択する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="467" height="127" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】大業種を選択する.png" alt="【LINE Developers】大業種を選択する" class="wp-image-2965" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】大業種を選択する.png 467w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】大業種を選択する-300x82.png 300w" sizes="(max-width: 467px) 100vw, 467px" /> <figcaption class="wp-element-caption">【LINE Developers】大業種を選択する</figcaption></figure> 

<ul class="wp-block-list">
  <li>
    <strong>小業種</strong> を選択する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="479" height="128" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】小業種を選択する.png" alt="【LINE Developers】小業種を選択する" class="wp-image-2966" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】小業種を選択する.png 479w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】小業種を選択する-300x80.png 300w" sizes="(max-width: 479px) 100vw, 479px" /> <figcaption class="wp-element-caption">【LINE Developers】小業種を選択する</figcaption></figure> 

<ul class="wp-block-list">
  <li>
    <strong>メールアドレス</strong> を入力する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="458" height="168" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】メールアドレスを入力する.png" alt="【LINE Developers】メールアドレスを入力する" class="wp-image-2967" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】メールアドレスを入力する.png 458w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】メールアドレスを入力する-300x110.png 300w" sizes="(max-width: 458px) 100vw, 458px" /> <figcaption class="wp-element-caption">【LINE Developers】メールアドレスを入力する</figcaption></figure> 

<ul class="wp-block-list">
  <li>
    (任意)<strong>プライバシーポリシーURL</strong> を入力する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="592" height="155" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】任意プライバシーポリシーURLを入力する.png" alt="【LINE Developers】(任意)プライバシーポリシーURLを入力する" class="wp-image-2968" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】任意プライバシーポリシーURLを入力する.png 592w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】任意プライバシーポリシーURLを入力する-300x79.png 300w" sizes="(max-width: 592px) 100vw, 592px" /> <figcaption class="wp-element-caption">【LINE Developers】(任意)プライバシーポリシーURLを入力する</figcaption></figure> 

<ul class="wp-block-list">
  <li>
    (任意)<strong>サービス利用規約URL</strong> を入力する。
  </li>
</ul><figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="523" height="137" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】任意サービス利用規約URLを入力する.png" alt="【LINE Developers】(任意)サービス利用規約URLを入力する" class="wp-image-2969" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】任意サービス利用規約URLを入力する.png 523w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】任意サービス利用規約URLを入力する-300x79.png 300w" sizes="(max-width: 523px) 100vw, 523px" /> <figcaption class="wp-element-caption">【LINE Developers】(任意)サービス利用規約URLを入力する</figcaption></figure> 

3　規約に同意し、『 **作成** 』を押下します。<figure class="wp-block-image aligncenter size-large is-resized">

<img loading="lazy" decoding="async" width="556" height="368" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】規約に同意し、作成を押下する.png" alt="【LINE Developers】規約に同意し、作成を押下する" class="wp-image-2970" style="aspect-ratio:556/368" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】規約に同意し、作成を押下する.png 556w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】規約に同意し、作成を押下する-300x199.png 300w" sizes="(max-width: 556px) 100vw, 556px" /> <figcaption class="wp-element-caption">【LINE Developers】規約に同意し、作成を押下する</figcaption></figure> 

## チャンネルアクセストークンを発行する

<span class="number">1　</span>『 **Messaging API設定** 』を押下します。<figure class="wp-block-image size-large">

<img loading="lazy" decoding="async" width="850" height="467" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-API設定を押下する.png" alt="【LINE Developers】Messaging API設定を押下する" class="wp-image-2971" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-API設定を押下する.png 850w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-API設定を押下する-300x165.png 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】Messaging-API設定を押下する-768x422.png 768w" sizes="(max-width: 850px) 100vw, 850px" /> <figcaption class="wp-element-caption">【LINE Developers】Messaging API設定を押下する</figcaption></figure> 

<span class="number">2　</span>一番下にある『 **チャンネルアクセストークン** 』の『 **発行** 』を押下する。<figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="1024" height="174" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行-1024x174.png" alt="【LINE Developers】チャンネルアクセストークンの発行" class="wp-image-2972" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行-1024x174.png 1024w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行-300x51.png 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行-768x131.png 768w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行.png 1287w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">【LINE Developers】チャンネルアクセストークンの発行</figcaption></figure> 

## まとめ

<img loading="lazy" decoding="async" width="1024" height="142" src="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行完了-1024x142.png" alt="" class="wp-image-2974" srcset="https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行完了-1024x142.png 1024w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行完了-300x41.png 300w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行完了-768x106.png 768w, https://arukayies.com/wp-content/uploads/2020/05/【LINE-Developers】チャンネルアクセストークンの発行完了.png 1294w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">【LINE Developers】チャンネルアクセストークンの発行完了</figcaption></figure> 

取得したトークンはメモ等に控えておいてくださいね！
</p>
<p>
これでLINEBOTの事前準備は完了です！

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-together">
  <a href="https://arukayies.com/gas/line_bot/line-bot-with-gas" title="GASで作る簡単なLINE BOTの作り方" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
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
  
  <br /> <a href="https://arukayies.com/gas/line_bot/action-objects" title="【LINE BOT】GASでBOTが実行できる『アクションタイプ』のまとめ" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2019/11/action_objects-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2019/11/action_objects-160x90.png 160w, https://arukayies.com/wp-content/uploads/2019/11/action_objects-120x68.png 120w, https://arukayies.com/wp-content/uploads/2019/11/action_objects-320x180.png 320w, https://arukayies.com/wp-content/uploads/2019/11/action_objects-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        【LINE BOT】GASでBOTが実行できる『アクションタイプ』のまとめ
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        LINE BOTを作成する機会が増えきた「くら」です！LINE公式ドキュメントを参考にGASを使って各APIを試してみました。今回はユーザーが受け取ったメッセージに対して、Botが実行できるアクションオブジェクトのまとめになります。ＬＩＮＥ...
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
      <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fe4320d2f4429571200cf25919da31353%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" ><img decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/20010009784798150734_1.jpg" style="border: none;" /></a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
    </div>
    
    <div class="kaerebalink-info">
      <div class="kaerebalink-name">
        <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fe4320d2f4429571200cf25919da31353%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >ＬＩＮＥ　ＢＯＴを作ろう！ Ｍｅｓｓａｇｉｎｇ　ＡＰＩを使ったチャットボットの/翔泳社/立花翔</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        
        <div class="kaerebalink-powered-date">
          posted with <a rel="nofollow noopener" href="https://kaereba.com" target="_blank">カエレバ</a>
        </div>
      </div>
      
      <div class="kaerebalink-detail">
      </div>
      
      <div class="kaerebalink-link1">
        <div class="shoplinkrakuten">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612575&#038;p_id=54&#038;pc_id=54&#038;pl_id=616&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fproduct.rakuten.co.jp%2Fproduct%2F-%2Fe4320d2f4429571200cf25919da31353%2F%3Frafcid%3Dwsc_i_ps_1087413314923222742" target="_blank" >楽天市場</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612575p_id54pc_id54pl_id616.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkamazon">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1612578&#038;p_id=170&#038;pc_id=185&#038;pl_id=4062&#038;s_v=b5Rz2P0601xu&#038;url=https%3A%2F%2Fwww.amazon.co.jp%2Fgp%2Fsearch%3Fkeywords%3DLINE%2520bot%26__mk_ja_JP%3D%25E3%2582%25AB%25E3%2582%25BF%25E3%2582%25AB%25E3%2583%258A" target="_blank" >Amazon</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1612578p_id170pc_id185pl_id4062.gif" width="1" height="1" style="border:none;" />
        </div>
        
        <div class="shoplinkyahoo">
          <a rel="noopener" href="//af.moshimo.com/af/c/click?a_id=1615240&#038;p_id=1225&#038;pc_id=1925&#038;pl_id=18502&#038;s_v=b5Rz2P0601xu&#038;url=http%3A%2F%2Fsearch.shopping.yahoo.co.jp%2Fsearch%3Fp%3DLINE%2520bot" target="_blank" >Yahooショッピング</a><img loading="lazy" decoding="async" src="https://arukayies.com/wp-content/uploads/2024/11/impressiona_id1615240p_id1225pc_id1925pl_id18502.gif" width="1" height="1" style="border:none;" />
        </div>
      </div>
    </div>
    
    <div class="booklink-footer">
    </div>
  </div>
</div>

 [1]: https://it-trend.jp/words/chatbot
