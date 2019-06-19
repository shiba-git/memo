# insertBefore()、insertAfter()
エラー: すべての引数をNodeにしてください。  
引数にHTMLCollectionが入っていた。HTMLCollectionからNodeにする場合、何番目かを指定してあげればよい。  
s.insertBefore(divOutSide, bannerArea) -> s.insertBefore(divOutSide, bannerArea[0]); 

MDN: https://developer.mozilla.org/ja/docs/Web/API/Node/insertBefore  
  
要素の後に挿入するinserAfter()は存在しない。しかし、以下のようにすれば同じ効果が得られる。  
  s.insertBefore(divOutside, bannerArea[0].nextSibling);  
参考サイト https://www.softel.co.jp/blogs/tech/archives/994  


