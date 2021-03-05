# MIMEとは

- text/html  
- application/json  
↑テキスト形式のhtml拡張子ファイルです！とかを意味する  
他にはアプリケーション形式（Exelとかある程度固有のもの）の～～とか  

MIMEによって色んな種類のデータがメールで送れるようになった  
メールのプロトコルとしてネットワークの教科書に出現しがちだが、特にメールに限ったプロトコルではない  

curlコマンドでもこういうの出てきたりする（メール固有のプロトコルではない）
node.jsで使いもした

```js
var server = http.createServer(function (request, response) {
    fs.readFile('./index.html', 'utf-8', function (error, data) {
        response.writeHead(200, {'Content-Type' : 'text/html'});
        response.write(data);
        response.end();
    });
});
```

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types
