# 練習題目

假設你有以下HTML結構，請寫出相應的jQuery語句來選擇指定的元素：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>jQuery Selector Practice</title>
</head>
<body>
    <div id="uniqueElement">This is a unique element.</div>
    <div class="common-class">First element with common class.</div>
    <div class="common-class">Second element with common class.</div>
    <p>Paragraph element.</p>
    <ul>
        <li>First item</li>
        <li>Second item</li>
    </ul>

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</body>
</html>
```

## 題目要求實現的jQuery選擇器

1. 使用ID選擇器選擇`id`為`uniqueElement`的`div`元素。
2. 使用類選擇器選擇所有具有`common-class`類的`div`元素。
3. 使用元素選擇器選擇所有`<p>`標籤。
4. 使用後代選擇器選擇`<ul>`元素中的所有`<li>`元素。
5. 使用選擇器過濾方法找到第二個有`common-class`類的`div`元素。

## 解答
<details> <summary>請不要沒練習就看答案</summary>

```javascript
// 1. 使用ID選擇器
$('#uniqueElement');

// 2. 使用類選擇器
$('.common-class');

// 3. 使用元素選擇器
$('p');

// 4. 使用後代選擇器
$('ul li');

// 5. 使用選擇器過濾方法
$('.common-class:eq(1)');
```

</details>

---------------------------  


# 進階練習題目

假定你有以下HTML結構：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>jQuery Selector Advanced Practice</title>
</head>
<body>
    <div class="container">
        <div id="first">First div inside container.</div>
        <div class="second">Second div inside container.</div>
        <div>Third div inside container.</div>
        <div class="special">Special div inside container.</div>
    </div>
    <div class="external">Div outside container.</div>
    <p class="info">Some information here.</p>
    <ul>
        <li class="item">Item 1</li>
        <li>Item 2</li>
        <li class="item special-item">Item 3</li>
        <li>Item 4</li>
    </ul>

    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</body>
</html>
```

## 題目要求實現的jQuery選擇器

1. 使用子選擇器選擇`.container`的直接子`div`元素。
2. 使用相鄰同輩選擇器選擇`id`為`first`的`div`元素旁邊的同輩`div`元素。
3. 使用通用同輩選擇器選擇`.second`類的`div`元素之後的所有同輩`div`元素。
4. 使用多重選擇器結合類和元素選擇器，選擇所有`.item`類的`li`元素和所有`p`元素。
5. 使用子選擇器和過濾類選擇器結合，選擇`.container`中的`.special`類的直接子`div`元素。
6. 使用屬性選擇器選擇所有包含`class`屬性的元素。

### 解答
<details> <summary>請不要沒練習就看答案</summary>

```javascript
// 1. 使用子選擇器
$('.container > div');

// 2. 使用相鄰同輩選擇器
$('#first + div');

// 3. 使用通用同輩選擇器
$('.second ~ div');

// 4. 使用多重選擇器
$('li.item, p');

// 5. 使用子選擇器和過濾類選擇器結合
$('.container > .special');

// 6. 使用屬性選擇器
$('[class]');
```


</details>
