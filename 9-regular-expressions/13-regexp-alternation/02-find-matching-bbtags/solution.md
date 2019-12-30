
<<<<<<< HEAD
開始タグは `pattern:\[(b|url|quote)\]` です.

次に、閉じタグまでの内容を見つけるため -- 改行を含む任意の文字にマッチするパターン `pattern:[\s\S]*?` を追加し、その後閉じタグへの後方参照を追加しましょう。

完全なパターンは: `pattern:\[(b|url|quote)\][\s\S]*?\[/\1\]`.

動作:

```js run
let reg = /\[(b|url|quote)\][\s\S]*?\[\/\1\]/g;
=======
Opening tag is `pattern:\[(b|url|quote)\]`.

Then to find everything till the closing tag -- let's use the pattern `pattern:.*?` with flag `pattern:s` to match any character including the newline and then add a backreference to the closing tag.

The full pattern: `pattern:\[(b|url|quote)\].*?\[/\1\]`.

In action:

```js run
let regexp = /\[(b|url|quote)\].*?\[\/\1\]/gs;
>>>>>>> 28ed5a3f7df9e015cf81c126423c76c9408d7117

let str = `
  [b]hello![/b]
  [quote]
    [url]http://google.com[/url]
  [/quote]
`;

<<<<<<< HEAD
alert( str.match(reg) ); // [b]hello![/b],[quote][url]http://google.com[/url][/quote]
```

閉じタグ `pattern:[/\1]` ではスラッシュをエスケープしなければならないことに注意してください。通常、スラッシュはパターンの終了を意味するためです。
=======
alert( str.match(regexp) ); // [b]hello![/b],[quote][url]http://google.com[/url][/quote]
```

Please note that besides escaping `pattern:[` and `pattern:]`, we had to escape a slash for the closing tag `pattern:[\/\1]`, because normally the slash closes the pattern.
>>>>>>> 28ed5a3f7df9e015cf81c126423c76c9408d7117