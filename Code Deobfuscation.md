Code deobfuscation is simplifying [[Code Obfuscation|obfuscated code]] to make it more readable and understandable.
```js
// Obfuscated Code
eval(function(p,a,c,k,e,d){e=function(c){return c};if(!''.replace(/^/,String)){while(c--){d[c]=k[c]||c}k=[function(e){return d[e]}];e=function(){return'\\w+'};c=1};while(c--){if(k[c]){p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c])}}return p}('5.4(\'3 2 1 0\');',6,6,'Module|Deobfuscation|JavaScript|HTB|log|console'.split('|'),0,{}))

// Deobfuscated Code
console.log('HTB JavaScript Deobfuscation Module');
```
---
### Tools
- https://matthewfl.com/unPacker.html
