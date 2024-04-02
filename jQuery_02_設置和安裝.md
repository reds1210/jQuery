# 下載 jQuery

1. **到jQuery官方網站**：前往[jQuery官方網站](https://jquery.com/)。
2. **選擇版本**：在官網上，你可以選擇不同的jQuery版本。一般來說，有“壓縮版(有min文字)”和“未壓縮版”可供選擇。壓縮版體積更小，適用於正式環境；未壓縮版適合開發階段，因為它更便於閱讀和調試。
3. **下載**：選擇適合的版本後，下載jQuery文件到你的項目目錄中。

# 本機引用

使用自己的伺服器資源來載入jQuery，優點可以減少CDN主機資安的風險，缺點是增加自己伺服器負擔。

```html
<script src="/js/jquery3.5.1.min.js"></script> <!--放你剛剛下載的jquey位置-->
```

# CDN 引用

使用CDN（Content Delivery Network）載入jQuery，可以提高加載速度，同時減少服務器負擔。以下是使用Google CDN作為示例：

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
```

將上面的Script元素加到你的HTML文件的`<head>`部分或者`<body>`部分的結尾處。

### 檢查 jQuery 是否成功加載

在你的網頁中加載jQuery後，可以透過簡單的JavaScript代碼來檢查是否成功加載。

在你的HTML文件中，加入以下JavaScript代碼：

```html
<script>
  if (window.jQuery) {  
    // jQuery已加載
    console.log("jQuery 已成功加載！");
  } else {
    // jQuery未加載
    console.log("jQuery 加載失敗！");
  }
</script>
```


