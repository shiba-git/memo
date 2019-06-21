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
