---
title: GASでスプレッドシートのセル書式を一括クリアする方法
author: arukayies
type: post
date: 2020-03-14T07:37:29+00:00
excerpt: GASでスプレッドシートの指定範囲の書式のみを削除する方法を紹介します！
url: /gas/clearformat
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
  - 1
snapEdIT:
  - 1
snapTW:
  - |
    s:393:"a:1:{i:0;a:12:{s:2:"do";s:1:"1";s:9:"msgFormat";s:27:"%TITLE% 
    %URL% 
    
    %HTAGS%";s:8:"attchImg";s:1:"0";s:9:"isAutoImg";s:1:"A";s:8:"imgToUse";s:0:"";s:9:"isAutoURL";s:1:"A";s:8:"urlToUse";s:0:"";s:4:"doTW";i:0;s:8:"isPosted";s:1:"1";s:4:"pgID";s:19:"1247589990772518913";s:7:"postURL";s:56:"https://twitter.com/arukayies/status/1247589990772518913";s:5:"pDate";s:19:"2020-04-07 18:20:07";}}";
last_modified:
  - 2025-03-07 22:44:55
categories:
  - GAS
tags:
  - clearFormat()
  - GAS
  - Google Apps Script
  - スプレッドシート

archives: ["2020年3月"]
---
こんにちは！Google Apps Script（GAS）でスプレッドシートを使っているあなたに、便利なメソッド「`clearFormat()`」の使い方を紹介するばい。これを使うことで、スプレッドシートの書式設定をリセットできるんじゃ。データの視覚的な装飾を一括で消したいときや、定型フォーマットを整えたいときにすごく役立つんだ。

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

<hr class="wp-block-separator has-alpha-channel-opacity" />

## clearFormat()メソッドって何？

簡単に言うと、`clearFormat()`はスプレッドシートの**セルの書式設定**を消すメソッドばい。でもね、値や数式には影響を与えないんだよ。たとえば、赤い背景色や太字で表示された数字があったとしても、これを使うと背景色や太字だけが消えて、数字自体はそのまま残るってわけ。

<pre class="wp-block-code"><code>// A1からC10の範囲の書式をクリアするサンプルコード
const sheet = SpreadsheetApp.getActiveSheet();
sheet.getRange("A1:C10").clearFormat();
</code></pre>

このコードを実行すれば、A1からC10の範囲に適用されている書式が全てクリアされるけど、データ自体はそのままだよ。

<hr class="wp-block-separator has-alpha-channel-opacity" />

## 他のメソッドとの違い

`clearFormat()`とよく似たメソッドに、`clear()`や`clearContent()`があるんじゃけど、それぞれの違いを理解しておくと便利だよ。

### 1. clear()

<ul class="wp-block-list">
  <li>
    <strong>作用対象</strong>: データも書式も両方クリア
  </li>
  <li>
    <strong>使用例</strong>: テンプレートの完全リセット
  </li>
</ul>

<pre class="wp-block-code"><code>range.clear(); // 値と書式の完全削除
</code></pre>

### 2. clearContent()

<ul class="wp-block-list">
  <li>
    <strong>作用対象</strong>: データ（値や数式）のみクリア
  </li>
  <li>
    <strong>使用例</strong>: データだけ更新したいとき
  </li>
</ul>

<pre class="wp-block-code"><code>range.clearContent(); // 値だけ削除
</code></pre>

### 3. clearFormat()

<ul class="wp-block-list">
  <li>
    <strong>作用対象</strong>: 書式設定のみクリア
  </li>
  <li>
    <strong>使用例</strong>: 視覚的なリセットだけしたいとき
  </li>
</ul>

<pre class="wp-block-code"><code>range.clearFormat(); // 書式だけ削除
</code></pre>

それぞれ、用途によって使い分けるといいけんね。

<hr class="wp-block-separator has-alpha-channel-opacity" />

## 動的範囲指定での活用法

固定範囲ではなく、動的に範囲を設定して書式をクリアする方法もあるけん。例えば、データが増減するシートの場合、`getLastRow()`メソッドを使うことで、最新のデータ範囲を自動で取得できるんよ。

<pre class="wp-block-code"><code>function dynamicClearFormat() {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('SalesData');
  const lastRow = sheet.getLastRow();
  const lastColumn = sheet.getLastColumn();

  // ヘッダー行を除いて、データ範囲の書式をクリア
  if(lastRow &gt; 1) {
    sheet.getRange(2, 1, lastRow-1, lastColumn).clearFormat();
  }
}
</code></pre>

これで、データが追加されても自動で範囲を取得して書式リセットができるんじゃ。

<hr class="wp-block-separator has-alpha-channel-opacity" />

## 他のメソッドとの組み合わせ

`clearFormat()`を使うだけでも便利だけど、他のメソッドと組み合わせることで、もっと便利に使えるけんね。たとえば、月次レポートを更新する場合、データを消したり書式をリセットしたりするだけでなく、新しい書式を一括で設定できるんじゃ。

<pre class="wp-block-code"><code>function monthlyReportReset() {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('MonthlyReport');
  const dataRange = sheet.getRange("B2:M50");
  
  // 段階的なクリア処理
  dataRange.clearContent();  // 既存データ削除
  dataRange.clearFormat();   // 書式リセット
  
  // 新規書式設定
  dataRange.setBackground('#ffffff');
  dataRange.setFontFamily('Arial');
  dataRange.setHorizontalAlignment('center');
}
</code></pre>

このように、データと書式を分けてクリアした後、必要な書式を新たに設定できるけん、効率的だよ。

<hr class="wp-block-separator has-alpha-channel-opacity" />

## パフォーマンス最適化

大量のデータを扱う場合、パフォーマンスが気になることがあるけん、最適化を考える必要があるんよ。たとえば、バッチ処理を使って一度に大量の書式を処理することで、スクリプトの実行速度が向上するんだ。

<pre class="wp-block-code"><code>function optimizePerformance() {
  const sheet = SpreadsheetApp.getActiveSheet();
  const range = sheet.getRange("A1:Z1000");
  
  // 書式プロパティの一括取得
  const formats = range.getTextStyles();
  
  // 変更処理（例：太字の解除）
  formats.forEach(row =&gt; row.forEach(cell =&gt; cell.setBold(false)));
  
  // 一括設定
  range.setTextStyles(formats);
}
</code></pre>

<hr class="wp-block-separator has-alpha-channel-opacity" />

## 実践的なユースケース

例えば、販売データの書式を統一したいときなんかに`clearFormat()`は大活躍するんよ。

<pre class="wp-block-code"><code>function standardizeSalesReport() {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Sales');
  const reportRange = sheet.getRange("A2:M" + sheet.getLastRow());
  
  reportRange.clearFormat();
  reportRange.setNumberFormat("#,##0");
  reportRange.setBorder(true, true, true, true, true, true);
}
</code></pre>

これで、毎月新しいデータが追加されても、書式が統一されるから便利だね。

<hr class="wp-block-separator has-alpha-channel-opacity" />

## 結論

`clearFormat()`は、Google Apps Scriptでスプレッドシートを効率的に管理するために欠かせないメソッドばい。データの視覚的一貫性を保ちながら、書式のリセットや最適化を行えるから、プロジェクトの運営やレポート作成の効率がグッと上がるよ。

これを活用すれば、作業がラクになるし、スプレッドシートの管理がしやすくなるけん、ぜひ試してみてけ！

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

<hr class="wp-block-separator has-alpha-channel-opacity" />

<div class="wp-block-cocoon-blocks-blogcard blogcard-type bct-reference">
  <a rel="noopener" href="https://tonari-it.com/gas-spreadsheet-range-clear-clearcontent/" title="【初心者向けGAS】スプレッドシートのセル範囲をクリアするいくつかの方法" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://tonari-it.com/wp-content/uploads/clear.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://tonari-it.com/wp-content/uploads/clear.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        【初心者向けGAS】スプレッドシートのセル範囲をクリアするいくつかの方法
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        Google Apps ScriptでBotを作りながらその基本を学んでいくシリーズです。今回はスプレッドシートのセル範囲をクリアする方法としてclearメソッド、clearContentメソッドを紹介します。
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://tonari-it.com/gas-spreadsheet-range-clear-clearcontent/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://tonari-it.com/gas-spreadsheet-range-clear-clearcontent/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          tonari-it.com
        </div>
      </div>
    </div>
  </div></a> 
  
  <br /> <a rel="noopener" href="https://developers.google.com/apps-script/reference/spreadsheet/sheet?hl=ja" title="Class Sheet  |  Apps Script  |  Google for Developers" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://www.gstatic.com/devrel-devsite/prod/v90b15eef664021f94a1ab8a4ca14c533325a9006d6183b165fb79714a6fcd6a0/developers/images/opengraph/white.png" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://www.gstatic.com/devrel-devsite/prod/v90b15eef664021f94a1ab8a4ca14c533325a9006d6183b165fb79714a6fcd6a0/developers/images/opengraph/white.png" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        Class Sheet  |  Apps Script  |  Google for Developers
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://developers.google.com/apps-script/reference/spreadsheet/sheet?hl=ja" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://developers.google.com/apps-script/reference/spreadsheet/sheet?hl=ja" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          developers.google.com
        </div>
      </div>
    </div>
  </div></a> 
  
  <br /> <a rel="noopener" href="https://technical.verybestcbp.com/gas4/" title="【GAS基礎講座 4. 】セルの値や属性をサクッと削除(clearFormat)" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://technical.verybestcbp.com/wp-content/uploads/2020/09/gas-4-1-e1677029257233.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://technical.verybestcbp.com/wp-content/uploads/2020/09/gas-4-1-e1677029257233.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        【GAS基礎講座 4. 】セルの値や属性をサクッと削除(clearFormat)
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        GAS(Google Apps Script)でデータの削除や属性のみの削除ができるようになります。
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://technical.verybestcbp.com/gas4/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://technical.verybestcbp.com/gas4/" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          technical.verybestcbp.com
        </div>
      </div>
    </div>
  </div></a> 
  
  <br /> <a rel="noopener" href="https://ytakeuchi.jp/?p=555" title="GASでスプレッドシートの内容をクリアするclear系メソッド一覧 - ytakeuchi.jp" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://ytakeuchi.jp/wp-content/uploads/2020/05/eyecatch_gas.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://ytakeuchi.jp/wp-content/uploads/2020/05/eyecatch_gas.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        GASでスプレッドシートの内容をクリアするclear系メソッド一覧 - ytakeuchi.jp
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        clearメソッド シート内の文字だけでなく、文字色・背景色・罫線などの書式などもすべてクリア var ss
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://ytakeuchi.jp/?p=555" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://ytakeuchi.jp/?p=555" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          ytakeuchi.jp
        </div>
      </div>
    </div>
  </div></a> 
  
  <br /> <a rel="noopener" href="https://auto-worker.com/blog/?p=1648" title="Google Apps Script(GAS) でスプレッドシートのセル削除方法まとめ～clearとdeleteCellsメソッドの違い | AutoWorker〜Google Apps Script(GAS)とSikuliで始める業務改善入門" class="blogcard-wrap external-blogcard-wrap a-wrap cf" target="_blank">
  
  <div class="blogcard external-blogcard eb-left cf">
    <div class="blogcard-label external-blogcard-label">
      <span class="fa"></span>
    </div><figure class="blogcard-thumbnail external-blogcard-thumbnail">
    
    <img data-src="https://auto-worker.com/blog/wp-content/uploads/2020/09/20200925_auto_006.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image lozad lozad-img" loading="lazy" width="160" height="90" />
    
    <noscript>
      <img loading="lazy" decoding="async" src="https://auto-worker.com/blog/wp-content/uploads/2020/09/20200925_auto_006.jpg" alt="" class="blogcard-thumb-image external-blogcard-thumb-image" width="160" height="90" />
    </noscript></figure>
    
    <div class="blogcard-content external-blogcard-content">
      <div class="blogcard-title external-blogcard-title">
        Google Apps Script(GAS) でスプレッドシートのセル削除方法まとめ～clearとdeleteCellsメソッドの違い | AutoWorker〜Google Apps Script(GAS)とSikuliで始める業務改善入門
      </div>
      
      <div class="blogcard-snippet external-blogcard-snippet">
        Google Apps Script(GAS)ではスプレッドシートのセルに書き込まれた値を削除することができます。 今回GASのコードでシート上のセルの値・書式を削除する方法とセル...
      </div>
    </div>
    
    <div class="blogcard-footer external-blogcard-footer cf">
      <div class="blogcard-site external-blogcard-site">
        <div class="blogcard-favicon external-blogcard-favicon">
          <img data-src="https://www.google.com/s2/favicons?domain=https://auto-worker.com/blog/?p=1648" alt="" class="blogcard-favicon-image external-blogcard-favicon-image lozad lozad-img" loading="lazy" width="16" height="16" />
          
          <noscript>
            <img loading="lazy" decoding="async" src="https://www.google.com/s2/favicons?domain=https://auto-worker.com/blog/?p=1648" alt="" class="blogcard-favicon-image external-blogcard-favicon-image" width="16" height="16" />
          </noscript>
        </div>
        
        <div class="blogcard-domain external-blogcard-domain">
          auto-worker.com
        </div>
      </div>
    </div>
  </div></a>
</div>
