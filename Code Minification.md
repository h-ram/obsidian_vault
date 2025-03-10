**Code minification** is removing unnecessary characters without changing it functionality. The primary goal is to reduce the size of the code to improve load times and reduce bandwidth usage, especially in web development.
```js
// Example 
function sayHello(name) {
    console.log("Hello, " + name); // Logging the greeting
}
// Minified Code
function sayHello(n){console.log("Hello, "+n);}
```

```
NOTE: The Minified code is writen in one line.
```
---
### **Minification Steps**
1. **Whitespace Removal** – Spaces, tabs, and newlines.
2. **Comment Removal** – Both single-line and multi-line comments.
3. **Shortening Variable and Function Names** (e.g., `longFunctionName` to `l`).
4. **Eliminating Unused Code** – Unused functions, variables, and dead code.
5. **String and Number Compression** – In some cases, string literals and numbers can be shortened.
---
### **Why Minify Code?**
- **Faster Load Times** – Smaller files load faster.
- **Reduced Bandwidth Usage** – Minified code reduces the amount of data transferred.
- **Improved Performance** – For web pages, faster loading contributes to better user experience and SEO rankings.
---
### **Minification Tools**
- **JavaScript**: UglifyJS, Terser
- **CSS**: clean-css, CSSO
- **HTML**: HTMLMinifier
---