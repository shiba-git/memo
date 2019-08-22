# insertBefore()、insertAfter()
エラー: すべての引数をNodeにしてください。  
引数にHTMLCollectionが入っていた。HTMLCollectionからNodeにする場合、何番目かを指定してあげればよい。  
s.insertBefore(divOutSide, bannerArea) -> s.insertBefore(divOutSide, bannerArea[0]);   
MDN: https://developer.mozilla.org/ja/docs/Web/API/Node/insertBefore  
  
  
要素の後に挿入するinserAfter()は存在しない。しかし、以下のようにすれば同じ効果が得られる。  
  s.insertBefore(divOutside, bannerArea[0].nextSibling);  
参考サイト https://www.softel.co.jp/blogs/tech/archives/994  
  
  
  
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
  
  
# クリックイベントが発火しないとき  
https://pisuke-code.com/jquery-solution-for-event-unfired/
  
  
# 要素を代入するときに便利なinsertAdjacentHTML　　
https://developer.mozilla.org/ja/docs/Web/API/Element/insertAdjacentHTML   
  
  
# クラスがあるか調べる方法(javascript)  
obj.classList.contains("cs3");  



