# insertBefore()、insertAfter()
エラー: すべての引数をNodeにしてください。  
引数にHTMLCollectionが入っていた。HTMLCollectionからNodeにする場合、何番目かを指定してあげればよい。  
s.insertBefore(divOutSide, bannerArea) -> s.insertBefore(divOutSide, bannerArea[0]);   
MDN: https://developer.mozilla.org/ja/docs/Web/API/Node/insertBefore  
  
  
要素の後に挿入するinserAfter()は存在しない。しかし、以下のようにすれば同じ効果が得られる。  
  s.insertBefore(divOutside, bannerArea[0].nextSibling);  
参考サイト https://www.softel.co.jp/blogs/tech/archives/994  
  
  
# bodyにline-heightはデザイン崩れの原因になる。謎の上余白
https://qiita.com/an_apco/items/87ff859950bc2752ae8c
  
  
# click() と on('click' )の違い　　
上記のようなinsertBeforeなどで、DOM後で追加した場合、  
click()だとイベント発火しない。onを使用することでDOMで追加した要素にクリックイベントを使用できる　  
また、onは複数のイベントを同時に宣言できる。詳しくは参考サイト  
参考サイト https://qiita.com/shizuma/items/d561f37f864c3ebb5096  
  
  
  
# ネガティブマージンとclickイベント
ネガティブマージンを使用すると、コンテンツが上乗せになり、  
下敷きになった要素のクリックイベントが反応しない可能性がある。  
z-indexとposition:relativeで解決できる.  
参考サイト https://webkcampus.com/201706/1369/  
  
  
  
# HTMLCollectionとNodeListの違い。  
NodeListは静的なものなので、DOMでの変更をすることができない。  
HTMLCollectionは、動的でDOMの変更ができる.  
  
  
  
# Uncaught TypeError: Failed to execute 'appendChild' on 'Node': parameter 1 is not of type 'Node'.
追加する要素をノードにしなければ、ならない。なので要素をquerySelectorAllで取得した。
すでにある要素に、条件でDOM変更を行う場合の要素取得方法。　　
 
 
# URLに日本語が入ったとき(IEの文字化け対策)  
日本語のvalue値にencodeURL  
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/encodeURI  
  
   
# ループ内で最後の値変数を設定するときのlength値
max = bannerBox.length; bannerBox[max - 1]   
length値は1からカウントするため、マイナス1を加えないとNodeListに合わない。  
  
  
# slidetoggle()の中身変更とtableについて
slideToggleは、表示の時、display値にblockが設定されている。ほかの値に変更したい場合、 
参考サイトの方法で変更可能。  
参考サイト https://codeday.me/jp/qa/20190115/124023.html  
slideToggleで、テーブル要素をアコーディオンする場合、レイアウト崩れがおこる。  
hideとshowでスムーズをあきらめるか、cssのみ(hight指定必要)で行う。  
 ※06/28 display:flexを使用
  
  
# thisを変数に格納する理由
http://kumao-no-mori.hatenablog.com/entry/2017/06/06/190000  
  
  
# 再帰関数(引数に与えたかずだけ表示する)  
```
var langs = ['Java', 'Ruby', 'Python'];

function cycle(times, array) {
  if(times <= 0) {
    return [];
  } else {
    console.log(array);
    return cycle(times - 1, array);
  }
}
cycle(3, langs); // [ 'Java', 'Ruby', 'Python', 'Java', 'Ruby', 'Python', 'Java', 'Ruby', 'Python' ]
```

# IEでのdisplay:flex
一番上の親要素にwidth:978pxが付いているが、  
IEだとDOMで追加した要素はうまく掴めないのか?謎  
なので、DOMで追加した要素のすぐ上の要素にwidthを指定する。  
  
# smoothScroll.jsはハイフンが付いたID名はうまく認識しない。  
プラグイン内の正規表現を見た限り、特殊文字の対応がされていない。  
  
  
# getMonthをキープし続ける(13月表示対策)
このままだと12月の0が表示される。1つずつif文するしかない.  
```
var date =  new Date();
		date.setMonth(date.getMonth() + 1);
		var MonBt_1 = date.getMonth();
		date.setMonth(date.getMonth() + 1);
		var MonBt_2 = date.getMonth();
		date.setMonth(date.getMonth() + 1);
		var MonBt_3 = date.getMonth();
		date.setMonth(date.getMonth() + 1);
		var MonBt_4 = date.getMonth();
		date.setMonth(date.getMonth() + 1);
		var MonBt_5 = date.getMonth();
		date.setMonth(date.getMonth() + 1);
		var MonBt_6 = date.getMonth();
		date.setMonth(date.getMonth() + 1);
		var MonBt_7 = date.getMonth();
```
  
  
# getElementbyId と　$()の違い  
http://blog.mwsoft.jp/article/36582155.html  
  
  
# クリックイベントが発火しないとき (DOMの後入れ関連)
https://pisuke-code.com/jquery-solution-for-event-unfired/
  
  
# 要素を代入するときに便利なinsertAdjacentHTML　　
https://developer.mozilla.org/ja/docs/Web/API/Element/insertAdjacentHTML   
  
  
# クラスがあるか調べる方法(javascript)  
obj.classList.contains("cs3");  
  
   
# $.cookieから値を取り出すとき、文字列の可能性あり。  
クッキーに保存した真偽値が文字列の可能性が高い。（原因はわからないがおそらく格納時）
```  
var openBox = Array.prototype.slice.call(  
    document.getElementsByClassName('openBox')  
  ).filter(function(v){  
    return  $.cookie(v.id) == "true";  
  });  
```  
  
   
# slideToggleの表示・非表示を判断するとき  
クリックイベントでslidetoggleが行われる前に入れないと状態を取得できない。  
https://stackoverflow.com/questions/1345652/slidetoggle-and-visible (ここの回答欄が役に立つ)  
  
  
# （form）value値が複数の場合
hiddenのinputを用意して、jsで連携した値を送信する
```
var tourConFlg = $('.domtour_search input[class="TourCFlg"]:checked').map(function(){
			return $(this).val();
		}).get().join('-') // 1-2
$('.domtour_search #domtour_search_tour_ConFlg').val(tourConFlg);
```
https://www.sejuku.net/blog/83301  
  
  
# javascriptのみで飛び先リンクを変更する方法　　
https://creatorhyp.com/tips/tips-linkchange/
  
  
# jQueryで特定の要素以外をクリックしたらポップアップを閉じる方法。
https://www.plusdesign.co.jp/blog/?p=5468  
  
  
# val()値の値を変更したのに、changeイベントが発生しない場合の対処法
val()変更後の最後に、change()を追加する　以下のサイトの「changeイベントが発火しない場合」を参照
https://www.sejuku.net/blog/41231 
 
# val()値がからの場合の条件分  
```
val == ""#  nullやundefindedではなくそのまま空指定すればよい  
```

# カレンダーの表示位置(datapicker)を決めたい場合
この方法だとPC、SPで使える。いちいち調整する必要はない。
下記はカレンダーを表示するためのボタンがinputTagの場合
```
$("#startCalenderStation, #endCalenderStation").datepicker({
beforeShow: function(input, inst){
	var $calendar = inst.dpDiv;
	var $input = $(input);
	var rect = $input.offset().top; //ブラウザ上部からinputまでの距離
	var height = $input.height();　// inputTag自体の高さ
	setTimeout(function() {
		$calendar.css({ top: rect + height + 20 }); //カレンダーのcssに適応
	}, 1);
    }
});
```
  
  
# input type の注意点 
type = "number"にしている時、submit時にパラメーター用に  
(文字列)変換した場合空文字になる。検索窓はsubmit時も考慮してtype値を付けなければならない   
  
  
# form serialize()
form内にあるすべての要素をパラメータのようにつなげられる。　　
https://qiita.com/tk3fftk/items/22bf451f3051804b142  
  
  
# on(click)の重複登録に注意
https://qiita.com/nekoneko-wanwan/items/3d3da95f1127f743397d  
addEventListenerを使用する  

# datepickerの初期設定を条件によって変更したい場合
```
if(dataTab == "air"){
	$('#startCalenderStation').datepicker('option', 'minDate', "+7d");
}else if(dataTab == "jr"){
	$('#startCalenderStation').datepicker('option', 'minDate', "+4d");
}
```
  
# jqueryのslimにはanimation系は入っていない。
minかcompuleteを使う。  
  
  
# a tagにクリックイベントを入れると二回発火する
Event.defaultPreventedを使用し、デフォルトの発火を消す。  
slideToggeで確認すると一回開いてすぐに閉じてしまうのがわかる。  
  
  
# スマホサイトで拡大・縮小(ピンチイン・アウト)できない
https://teratail.com/questions/24059
```
<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=2, user-scalable=yes">
```
# checkboxとlabel  
checkboxのid値 と labelのfor値を合わせる  
  
  
# checkboxのカスタマイズ  
元のcheckboxは非表示にする  
labelにrelative labelのbefore,afterにabsolute  
beforeにチェックマーク 初期は透明度0、afterにcheckboxの箱を作成
```
#checkboxStation:checked + .roundTripCheckBoxlabel:before{
  opacity: 1;
  z-index: 100;
}
```  
check時に透明度を1にする

# 一度fadeOutし、もう一度fadeInする方法  
https://teratail.com/questions/221550

# addEventLinstener 第三引数バブリング
そして第三引数には『false』と記載します。これは『イベントバブリング』を行わない、という設定で、『イベントバブリング』とは親要素にイベントを伝播させるかさせないか、という意味です。こちらもちょっと難しいので先の記事で解説させていただきますが、親要素にイベントを伝播させる実装パターンはあまり存在しません。なのでイベントを伝播させない『false』と記述する、と丸暗記してしまいましょう。ちなみにイベントを伝播させたい場合は『true』と記述します。

# JabvaScript の404
大体中の関数や、処理に問題が起きている。  
リンク先をたどって表示されるのであれば問題ない。  
  
  
# Cokkieのパスを指定しないとあてでエラーになる可能性がある。
$.cookie.jQueryの話。

# input tag 16px以下はズームされる
https://qiita.com/skwbr/items/b285cc312587c73a4812

