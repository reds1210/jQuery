# 基本格式

jQuery的基本語法是`$(selector).action()`，其中：

- `$`是一個jQuery的別名，表示jQuery函數。
- `selector`是用來查找HTML元素的jQuery選擇器。
- `action()`是要在選擇的元素上執行的jQuery方法。

例如：
```javascript
$(document).ready(function(){
    $("button").click(function(){
        $("p").hide();
    });
});
```
這個例子中，`$(document).ready()`是用來確保HTML檔案完全加載後再執行函數。`$("button").click()`是為所有`<button>`元素綁定點擊事件，當按鈕被點擊時，`$("p").hide()`會隱藏所有`<p>`元素。

## 使用`$(document).ready()`

為了確保DOM完全加載後再執行你的jQuery程式碼，應該將程式碼放在`$(document).ready()`函數內。可以避免在DOM元素可操作之前就試圖操作它們，從而引起的問題。

```javascript
$(document).ready(function(){
    // 你的jQuery程式碼
});
```

或者使用簡化的語法：

```javascript
$(function(){
    // 你的jQuery程式碼
});
```

## 鏈式寫法

jQuery支持鏈式寫法（Chaining），這意味著你可以在一個選擇器上連續調用多個操作，這樣可以使程式碼更加簡潔。

```javascript
$("p").css("color", "red").slideUp(2000).slideDown(2000);
```
這個例子首先將所有`<p>`元素的文字顏色設為紅色，然後執行一個2000毫秒的滑上動畫，接著執行一個2000毫秒的滑下動畫。

## 變數

當你需要多次使用同一個選擇器時，最好是將其存儲在一個變數中。這不僅可以提高性能（通過減少DOM查找次數），也可以使程式碼更加清晰。

```javascript
var paragraphs = $("p");
paragraphs.hide();
```

## 結尾分號

雖然在JavaScript中，某些情況下結尾的分號可以省略，但為了保持程式碼的清晰和一致性，推薦在每個語句的結尾都使用分號。

## 縮排和換行

為了提高程式碼的可讀性，應該使用適當的縮排（通常是2個或4個空格）和換行。特別是在使用鏈式寫法或者寫大量的jQuery語句時，適當的換行和縮排可以讓程式碼更容易閱讀。

# 選擇器
jQuery提供了一組功能強大的選擇器，使得開發者可以便捷地選擇和操作DOM元素。

## 基本選擇器

基本選擇器是這些選擇器中最簡單也是最常用的一部分，它們包括：

### 1. 元素選擇器（Element Selector）

元素選擇器根據元素名來選擇元素。它可以選擇所有給定類型的DOM元素。

**語法**:
```javascript
$("element")
```

**範例**：
```javascript
$("p") // 選擇所有的<p>元素
```

### 2. ID選擇器（ID Selector）

ID選擇器根據元素的ID屬性選擇單個元素。在一個HTML檔案中，每個ID應該是唯一的。

**語法**:
```javascript
$("#id")
```

**範例**：
```javascript
$("#myId") // 選擇ID為myId的元素
```

### 3. 類選擇器（Class Selector）

類選擇器根據元素的class屬性來選擇一組元素。一個元素可以有多個類，同時一個類可以被多個元素使用。

**語法**:
```javascript
$(".class")
```

**範例**：
```javascript
$(".myClass") // 選擇所有class包含myClass的元素
```

### 4. 通用選擇器（Universal Selector）

通用選擇器選擇所有的元素。

**語法**:
```javascript
$("*")
```

**範例**：
```javascript
$("*") // 選擇所有元素
```

### 5. 群組選擇器（Multiple Selector）

群組選擇器可以讓你一次選擇多個元素，元素之間用逗號分隔。

**語法**:
```javascript
$("selector1, selector2, selectorN")
```

**範例**：
```javascript
$("p, .myClass") // 選擇所有的<p>元素和所有class為myClass的元素
```

jQuery的屬性選擇器允許根據元素的屬性及其值來選擇元素。這種選擇器非常有用，尤其是當你想要操作那些具有特定標記或數據屬性的元素時。以下是一些常用的屬性選擇器及其語法和使用範例：

## 屬性選擇器

選擇具有指定屬性的元素，無論屬性的值是什麼。

**語法**:
```javascript
$("[attribute]")
```

**範例**：
```javascript
$("[title]") // 選擇所有具有title屬性的元素
```

### 確切屬性值選擇器

選擇屬性值完全匹配指定值的元素。

**語法**:
```javascript
$("[attribute='value']")
```

**範例**：
```javascript
$("[type='checkbox']") // 選擇所有type屬性值為checkbox的元素
```

### 包含特定字串的屬性值選擇器

選擇屬性值為指定字串的元素。

**語法**:
```javascript
$("[attribute*='value']")
```

**範例**：
```javascript
$("[class*='test']") // 選擇class屬性中為test的所有元素
```

### 屬性值開頭為特定字串的選擇器

選擇屬性值以指定字串開頭的元素。

**語法**:
```javascript
$("[attribute^='value']")
```

**範例**：
```javascript
$("[id^='test']") // 選擇id屬性值以test開頭的所有元素
```

### 屬性值結尾為特定字串的選擇器

選擇屬性值以指定字串結尾的元素。

**語法**:
```javascript
$("[attribute$='value']")
```

**範例**：
```javascript
$("[src$='.jpg']") // 選擇src屬性值以.jpg結尾的所有元素
```

### 屬性值包含多個指定字串的選擇器

選擇屬性值包含多個指定字串的元素（多個值之間用空格分隔）。

**語法**:
```javascript
$("[attribute~='value']")
```

**範例**：
```javascript
$("[title~='image']") // 選擇title屬性中包含單詞image的所有元素
```

### 屬性包含前綴選擇器

選擇具有指定屬性的元素，該屬性的值等於給定字串或以該字串開頭，後面接著連字元 (-)。

**語法**:
```javascript
$("[attribute|='value']")
```

**範例**：
```javascript
$("[hreflang|='en']") // 選擇hreflang屬性值為en或以en-開頭的所有元素
```


## 進階選擇器
除了基本選擇器，jQuery還提供了許多進階選擇器，可以更精確地選擇DOM元素。

### 層次選擇器

- **子元素選擇器** (`parent > child`)：選擇指定父元素的直接子元素。
  
  ```javascript
  $("ul > li") // 選擇<ul>元素的所有直接<li>子元素
  ```
  
- **後代選擇器** (`ancestor descendant`)：選擇指定祖先元素的所有後代元素。
  
  ```javascript
  $("div p") // 選擇<div>元素內所有的<p>後代元素
  ```
  
- **相鄰選擇器** (`prev + next`)：選擇直接跟在另一元素後的元素。
  
  ```javascript
  $("#prev + div") // 選擇ID為prev的元素之後的第一個<div>元素
  ```
  
- **同層選擇器** (`prev ~ siblings`)：選擇在另一元素之後的所有同胞元素。
  
  ```javascript
  $("#prev ~ div") // 選擇ID為prev的元素之後的所有<div>同胞元素
  ```

### 過濾選擇器

- **首元素選擇器** (`:first`)：選擇第一個元素。
  
  ```javascript
  $("p:first") // 選擇第一個<p>元素
  ```
  
- **最後元素選擇器** (`:last`)：選擇最後一個元素。
  
  ```javascript
  $("p:last") // 選擇最後一個<p>元素
  ```
  
- **不包含選擇器** (`:not(selector)`)：排除匹配的元素。
  
  ```javascript
  $("p:not(.exclude)") // 選擇所有不含class為exclude的<p>元素
  ```
  
- **偶數元素選擇器** (`:even`)：選擇索引為偶數的元素，索引從0開始。
  
  ```javascript
  $("tr:even") // 選擇所有索引為偶數的<tr>元素
  ```
  
- **奇數元素選擇器** (`:odd`)：選擇索引為奇數的元素。
  
  ```javascript
  $("tr:odd") // 選擇所有索引為奇數的<tr>元素
  ```

### 子元素過濾選擇器

- **:first-child 選擇器**：選擇所有作為其父元素的第一個子元素的元素。
  
  ```javascript
  $(":first-child") // 選擇所有父元素的第一個子元素
  ```

- **:first-of-type 選擇器**：選擇所有在其兄弟元素中同名的第一個元素。
  
  ```javascript
  $(":first-of-type") // 選擇所有兄弟元素中同名的第一個元素
  ```

- **:last-child 選擇器**：選擇所有作為其父元素的最後一個子元素的元素。
  
  ```javascript
  $(":last-child") // 選擇所有父元素的最後一個子元素
  ```

- **:last-of-type 選擇器**：選擇所有在其兄弟元素中同名的最後一個元素。
  
  ```javascript
  $(":last-of-type") // 選擇所有兄弟元素中同名的最後一個元素
  ```

- **:nth-child() 選擇器**：選擇所有作為其父元素的第n個子元素的元素。
  
  ```javascript
  $(":nth-child(n)") // 選擇所有父元素的第n個子元素
  ```

- **:nth-last-child() 選擇器**：選擇所有作為其父元素的第n個子元素的元素，從最後一個元素開始計數。
  
  ```javascript
  $(":nth-last-child(n)") // 選擇所有父元素的從最後開始的第n個子元素
  ```

- **:nth-last-of-type() 選擇器**：選擇所有在其父元素中與同名兄弟元素相比，從最後一個元素開始計數的第n個元素。
  
  ```javascript
  $(":nth-last-of-type(n)") // 選擇所有父元素中與同名兄弟元素相比從最後開始的第n個元素
  ```

- **:nth-of-type() 選擇器**：選擇所有作為其父元素中與同名兄弟元素相比的第n個元素。
  
  ```javascript
  $(":nth-of-type(n)") // 選擇所有父元素中與同名兄弟元素相比的第n個元素
  ```

- **:only-child 選擇器**：選擇所有作為其父元素唯一子元素的元素。
  
  ```javascript
  $(":only-child") // 選擇所有作為其父元素唯一子元素的元素
  ```

- **:only-of-type 選擇器**：選擇所有沒有同名兄弟元素的元素。
  
  ```javascript
  $(":only-of-type") // 選擇所有沒有同名兄弟元素的元素
  ```


### 表單選擇器

- **按鈕選擇器** (`:button`)：選擇所有`<button>`元素和`type="button"`的`<input>`元素。
  
  ```javascript
  $(":button") // 選擇所有按鈕
  ```
  
- **文本框選擇器** (`:text`)：選擇所有的文本框。
  
  ```javascript
  $(":text") // 選擇所有type為text的<input>元素
  ```
  
- **選中選擇器** (`:checked`)：選擇所有選中的復選框或單選按鈕。
  
  ```javascript
  $(":checked") // 選擇所有選中的checkbox和radio按鈕
  ```


## 練習

### HTML範例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>jQuery Selector Examples</title>
</head>
<body>
    <div class="container">
        <div id="first-child" class="box">First child div</div>
        <div class="box">Second child div</div>
        <p class="box">First child paragraph</p>
        <p class="box">Second child paragraph</p>
        <div class="box only-box">Only child div in another container</div>
    </div>
     <div class="another-container">
        <p class="only-type">Only paragraph in container</p>
    </div>
    <ul>
        <li>First item</li>
        <li class="special">Second item</li>
        <li>Third item</li>
        <li>Fourth item</li>
    </ul>
    <input type="text" value="Text input">
    <input type="button" value="Button input">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</body>
</html>
```

### 選擇器範例

1. **:first-child 選擇器**

   ```javascript
   $(".container > div:first-child").css("border", "2px solid blue"); // 將首個div的邊框設為藍色
   ```

2. **:first-of-type 選擇器**

   ```javascript
   $(".container > p:first-of-type").css("color", "green"); // 將首個段落文字設為綠色
   ```

3. **:last-child 選擇器**

   ```javascript
   $("ul > li:last-child").css("background-color", "yellow"); // 將最後一個列表項目的背景設為黃色
   ```

4. **:last-of-type 選擇器**

   ```javascript
   $(".container > p:last-of-type").css("font-weight", "bold"); // 將最後一個段落文字加粗
   ```

5. **:nth-child(n) 選擇器**

   ```javascript
   $("ul > li:nth-child(2)").css("text-decoration", "underline"); // 將第二個列表項目下劃線
   ```

6. **:nth-last-child(n) 選擇器**

   ```javascript
   $(".container > div:nth-last-child(2)").css("font-style", "italic"); // 將倒數第二個div的文字設為斜體
   ```

7. **:nth-of-type(n) 選擇器**

   ```javascript
   $("ul > li:nth-of-type(2)").css("color", "red"); // 將第二個列表項目的文字顏色設為紅色
   ```

8. **:nth-last-of-type(n) 選擇器**

   ```javascript
   $("ul > li:nth-last-of-type(2)").css("color", "blue"); // 將倒數第二個列表項目的文字顏色設為藍色
   ```

9. **:only-of-type 選擇器**

   ```javascript
   $(".another-container > p:only-of-type").css("font-weight", "bold"); // 將`.another-container`內唯一類型的`p`元素文字加粗
   ```

10. **:only-child 選擇器**
    
     ```javascript
     $(".container > .only-box:only-child").css("background-color", "lightgrey"); // 若`.only-box`是其父元素的唯一子元素，則將其背景設為淺灰色
    ```



## 選擇器原理

工作原理和流程基於其底層選擇器Sizzle引擎。  
Sizzle是一個純JavaScript實現的CSS選擇器引擎，它使jQuery能夠通過CSS選擇語法來查找匹配的元素集合。  

**3.7.0版本後捨棄了Sizzle，把相關程式碼移到jquery.find內**

### 1. 解析選擇器表達式

當你使用jQuery選擇器如`$("selector")`時，首先解析這個選擇器表達式。這一步骤涉及到分析給定的字串，確定它是一個基本選擇器（如ID、類或元素選擇器），還是一個複合或屬性選擇器等。

### 2. 使用原生DOM方法查找元素（如果可能）

為了最大化性能，如果選擇器表達式是比較簡單的，jQuery會使用`document.querySelectedAll()`來直接查找元素。

### 3. 使用Sizzle引擎進行選擇

如果選擇器較為複雜，或者上述原生方法無法應用於特定的選擇器，jQuery則會使用Sizzle引擎來完成選擇任務。Sizzle引擎會遍歷DOM樹，匹配所有符合選擇器標準的元素。它支持所有CSS選擇器標準，以及特定的jQuery擴展選擇器。

### 4. 返回jQuery物件

無論是直接使用DOM方法查找還是通過Sizzle引擎，最終找到的元素都會被封裝成一個jQuery物件。這個物件包含了所有匹配的元素，並且提供了豐富的方法來操作這些元素，比如改變它們的CSS樣式、綁定事件處理器等。


