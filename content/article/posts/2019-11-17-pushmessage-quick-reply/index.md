---
title: 【LINE BOT】GASで『クイックリプライメッセージ』の送り方
author: arukayies
type: post
date: 2019-11-17T01:58:01+00:00
url: /gas/line_bot/pushmessage-quick-reply
share: true
toc: true
comment: true
page_type:
  - default
snap_isAutoPosted:
  - 1
update_level:
  - high
the_review_type:
  - Product
the_review_rate:
  - 5
last_modified:
  - 2024-11-19 10:20:13
snapEdIT:
  - 1
snapTW:
  - |
    s:393:"a:1:{i:0;a:12:{s:2:"do";s:1:"1";s:9:"msgFormat";s:27:"%TITLE% 
    %URL% 
    
    %HTAGS%";s:8:"attchImg";s:1:"1";s:9:"isAutoImg";s:1:"A";s:8:"imgToUse";s:0:"";s:9:"isAutoURL";s:1:"A";s:8:"urlToUse";s:0:"";s:4:"doTW";i:0;s:8:"isPosted";s:1:"1";s:4:"pgID";s:19:"1244656616860839937";s:7:"postURL";s:56:"https://twitter.com/arukayies/status/1244656616860839937";s:5:"pDate";s:19:"2020-03-30 16:03:56";}}";
categories:
  - LINE BOT
tags:
  - GAS
  - Google Apps Script
  - LINE BOT

archives: ["2019年11月"]
---
こんにちは「くら」です！
</p>
<p>
<a href="https://developers.line.biz/ja/docs/messaging-api/">LINE公式ドキュメント</a> を参考に <strong>GAS</strong> を使って各APIを試しています。

その他のアクションについては別記事で紹介しています。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-related">
  <a href="https://arukayies.com/gas/line_bot/action-objects" title="【LINE BOT】GASでBOTが実行できる『アクションタイプ』のまとめ" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
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

今回は「 <strong>クイックリプライボタンメッセージ</strong> 」の送り方を紹介します。
</p>
<p>
公式ドキュメントは <a href="https://developers.line.biz/ja/docs/messaging-api/using-quick-reply/">こちら</a> を参照してください。

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

## 事前準備

LINE Developersで **チャンネルアクセストークン** を取得してください。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-related">
  <a href="https://arukayies.com/gas/line_bot/gettoken" title="LINE Messaging APIアクセストークンの取得方法" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2019/07/gettoken-1-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2019/07/gettoken-1-160x90.png 160w, https://arukayies.com/wp-content/uploads/2019/07/gettoken-1-120x68.png 120w, https://arukayies.com/wp-content/uploads/2019/07/gettoken-1-320x180.png 320w, https://arukayies.com/wp-content/uploads/2019/07/gettoken-1-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        LINE Messaging APIアクセストークンの取得方法
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        LINEBOTに必要なトークンの取得方法を画像付きで解説します。
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

LINEの **ユーザID** の調べ方はこの手順で確認できます。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-related">
  <a href="https://arukayies.com/gas/line_bot/get-userid" title="【LINE BOT】GASでLINEの『ユーザID』の取得方法" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard internal-blogcard ib-left cf">
    <div class="blogcard-label internal-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail internal-blogcard-thumbnail">
    
    <img loading="lazy" decoding="async" width="160" height="90" src="https://arukayies.com/wp-content/uploads/2019/11/get_userid-160x90.png" class="blogcard-thumb-image internal-blogcard-thumb-image wp-post-image" alt="" srcset="https://arukayies.com/wp-content/uploads/2019/11/get_userid-160x90.png 160w, https://arukayies.com/wp-content/uploads/2019/11/get_userid-120x68.png 120w, https://arukayies.com/wp-content/uploads/2019/11/get_userid-320x180.png 320w, https://arukayies.com/wp-content/uploads/2019/11/get_userid-376x212.png 376w" sizes="(max-width: 160px) 100vw, 160px" /></figure>
    
    <div class="blogcard-content internal-blogcard-content">
      <div class="blogcard-title internal-blogcard-title">
        【LINE BOT】GASでLINEの『ユーザID』の取得方法
      </div>
      
      <div class="blogcard-snippet internal-blogcard-snippet">
        くらこんにちは「くら」です！LINE公式ドキュメント を参考に GAS を使って各APIを試しています。くら今回はLINEの「ユーザID」の取得方法を紹介します。ログを見るときによく使っています。ＬＩＮＥ　ＢＯＴを作ろう！ Ｍｅｓｓａｇｉｎ...
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

## 『クイックリプライボタン』を送るコード

1行目のトークンは事前に取得したLINEのチャンネルアクセストークンを入力してください。

2行目のユーザーIDも事前に取得したIDを入力してください。

## 『クイックリプライボタン』を受け取るコード

## ウェブアプリをデプロイする

過去の記事で手順を紹介しているので、そちらを参照お願いします！

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a href="https://arukayies.com/gas/line_bot/line-bot-with-gas#toc6" title="GASで作る簡単なLINE BOTの作り方" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
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

## LINE DevelopersにWebhook URLを設定する

過去の記事で手順を紹介しているので、そちらを参照お願いします！

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

## 『クイックリプライボタン』を送ってみる

**pushmessage\_quick\_reply** を実行します。<figure class="wp-block-image size-large">

<img loading="lazy" decoding="async" width="1024" height="291" src="https://arukayies.com/wp-content/uploads/2021/02/スクリーンショット_2021-02-27_14_32_17-1024x291.png" alt="" class="wp-image-4526" srcset="https://arukayies.com/wp-content/uploads/2021/02/スクリーンショット_2021-02-27_14_32_17-1024x291.png 1024w, https://arukayies.com/wp-content/uploads/2021/02/スクリーンショット_2021-02-27_14_32_17-300x85.png 300w, https://arukayies.com/wp-content/uploads/2021/02/スクリーンショット_2021-02-27_14_32_17-768x219.png 768w, https://arukayies.com/wp-content/uploads/2021/02/スクリーンショット_2021-02-27_14_32_17.png 1388w" sizes="(max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">**pushmessage\_quick\_reply** を実行する</figcaption></figure> 

実行すると、LINEに **クイックリプライボタンメッセージ** が送られます！<figure class="wp-block-image aligncenter">

<img decoding="async" src="https://arukayies.com/wp-content/uploads/2019/12/img_5dfa227d58934.jpg" alt="" /> </figure> 

<div style="height:20px" aria-hidden="true" class="wp-block-spacer">
</div>

「 **寿司** 」を選択すると「 **寿司をタップしました！** 」と返ってきます！<figure class="wp-block-image aligncenter size-large">

<img loading="lazy" decoding="async" width="750" height="278" src="https://arukayies.com/wp-content/uploads/2021/02/LINE_capture_636096477.293758.jpg" alt="" class="wp-image-4523" srcset="https://arukayies.com/wp-content/uploads/2021/02/LINE_capture_636096477.293758.jpg 750w, https://arukayies.com/wp-content/uploads/2021/02/LINE_capture_636096477.293758-300x111.jpg 300w" sizes="(max-width: 750px) 100vw, 750px" /> </figure> 

その他のアクションについては別記事で紹介しています。

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-related">
  <a href="https://arukayies.com/gas/line_bot/action-objects" title="【LINE BOT】GASでBOTが実行できる『アクションタイプ』のまとめ" class="blogcard-wrap internal-blogcard-wrap a-wrap cf" target="_blank">
  
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
