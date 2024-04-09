# 事件

使用 jQuery 處理事件是這個函式庫中最強大的功能之一，它讓事件處理變得更簡單、更一致。

## 1. 綁定事件

綁定事件是指將一個事件處理函式與一個或多個事件關聯起來。最常見的事件包括 `click`、`dblclick`（雙擊）、`mouseenter`、`mouseleave` 等。

### 使用 `.click()` 綁定點擊事件

```javascript
$('#myButton').click(function() {
    alert('Button clicked!');
});
```

### 使用 `.on()` 通用方法綁定事件

`.on()` 方法可以用於綁定所有類型的事件，且可以同時綁定多個事件。

```javascript
$('#myElement').on('click mouseenter', function() {
    console.log('Element clicked or mouse entered!');
});
```

## 2. 事件處理

在事件處理函式內，`this` 關鍵字指向觸發事件的 DOM 元素。可以使用 jQuery 來封裝這個元素，進而使用 jQuery 方法。

```javascript
$('#myElement').click(function() {
    // 使用 $(this) 將 DOM 元素轉換為 jQuery 對象
    $(this).css('color', 'red');
});
```

## 3. 解除事件綁定

如果不再需要某個事件處理器，可以使用 `.off()` 方法來移除它。

### 解除特定事件處理器

```javascript
$('#myElement').off('click');
```

### 解除所有事件處理器

```javascript
$('#myElement').off();
```

## 4. 透過Jquery觸發事件
`.trigger()` 方法用來執行匹配元素上附加的所有處理器和行為，對應給定的事件類型。用。

基本語法長這樣：

```javascript
$(selector).trigger(eventType, [parameters])
```

- `selector`：選擇器，用來找到要觸發事件的元素。
- `eventType`：這是一個表示要觸發的事件類型的字串。可以是標準的 DOM 事件（像是 'click', 'submit' 等）或是自定義事件。
- `parameters`：(選擇性) 一組參數陣列，會傳遞給事件處理函式。

### 範例 1：觸發點擊事件

假設你有一個按鈕，ID 為 `myButton`，你想要以程式化的方式在這個按鈕上觸發點擊事件：

```html
<button id="myButton">點我！</button>
```

```javascript
$('#myButton').click(function() {
    alert('按鈕被點擊了！');
});

// 後來在你的代碼中，你可以這樣觸發點擊事件：
$('#myButton').trigger('click');
```

### 範例 2：帶參數觸發自定義事件

首先，你為你的自定義事件 `myEvent` 綁定一個事件處理器：

```javascript
$(document).on('myEvent', function(event, param1, param2) {
    console.log(`事件被觸發，參數：${param1}, ${param2}`);
});
```

然後，你可以帶著參數這樣觸發 `myEvent`：

```javascript
$(document).trigger('myEvent', ['Hello', 'world']);
```

輸出：`事件被觸發，參數：Hello, world`。


## 5. 實際範例：表單提交事件

```javascript
$('#myForm').submit(function(event) {
    event.preventDefault(); // 阻止表單的默認提交行為
    var name = $('#name').val(); // 獲取輸入框的值
    console.log('Submitting name:', name);
});
```




# 事件列表

## 滑鼠事件

| 事件名稱    | 方法名稱       |用途描述 |
| ----------- | -------------- | ----------------------------------------------------------------------------------- |
| click       | .click()       | 這是最常用於元素點擊的事件。                                                        |
| contextmenu | .contextmenu() | 通常用於自定義右鍵菜單的行為。                                                      |
| dblclick    | .dblclick()    | 用於雙擊元素的特定行為。                                                            |
| hover       | .hover()       | 當滑鼠進入和離開元素時執行。這個方法是 `mouseenter` 和 `mouseleave` 的簡化形式。    |
| mousedown   | .mousedown()   | 用於檢測滑鼠按鍵被按下的時刻。                                                      |
| mouseenter  | .mouseenter()  | 當滑鼠進入元素範圍時觸發。                                                          |
| mouseleave  | .mouseleave()  | 當滑鼠離開元素範圍時觸發。                                                          |
| mousemove   | .mousemove()   | 用於追踪滑鼠在元素上移動的行為。                                                    |
| mouseout    | .mouseout()    | 當滑鼠移出元素或其子元素時觸發。                                                    |
| mouseover   | .mouseover()   | 當滑鼠移入元素或其子元素時觸發。                                                    |
| mouseup     | .mouseup()     | 用於檢測滑鼠按鍵被釋放的時刻。                                                      |
| toggle      | .toggle()      | **已廢棄/移除**。原用於綁定兩個或更多的事件處理器到匹配的元素，以在交替點擊時執行。 |

`.hover()` 和 `.toggle()` 方法在新版本的 jQuery 中已被標記為過時或已移除，推薦
使用 `.on()` 方法來實現類似的功能。

## 鍵盤事件

| 事件名稱     | 方法名稱     | 描述  |
|-----------|------------|--------------------------------------------------------------------------------------|
| keydown   | .keydown() | 當鍵盤上的按鍵被按下時觸發。             |
| keypress  | .keypress()| 當按下可產生字元的按鍵時觸發。但由於跨瀏覽器不一致性及更佳選項（如 `keydown`、`keyup`）的出現，`keypress` 事件已經被淘汰。 |
| keyup     | .keyup()   |當鍵盤上的按鍵被釋放時觸發。               |

### 重點概念與差異

- **.keydown()** 通常用來偵測鍵盤上任何按鍵的按下動作，適合用於捷徑鍵或偵測非字符按鍵。
  
- **.keypress()** 歷史上用來偵測按下可產生字元的按鍵。不過，因為 `keypress` 事件在不同瀏覽器間的行為不一致，加上有了更好的選擇，所以已經被淘汰。

- **.keyup()** 適用於偵測按鍵釋放的情況。它可以與 `keydown` 事件一起使用，以管理按鍵的狀態（例如，追踪長按或確保動作僅在每次按鍵時觸發一次）。

### 使用範例

假設有個場景：當在文字輸入框中按下並釋放 Enter 鍵時，觸發某個函式：

```javascript
$('#textInput').keydown(function(event) {
    if (event.which === 13) { // 13 是 Enter 鍵的代碼
        console.log('按下 Enter 鍵');
    }
});

$('#textInput').keyup(function(event) {
    if (event.which === 13) {
        console.log('釋放 Enter 鍵');
        // 執行動作，比如提交表單
    }
});
```

## 表單事件

| 事件名稱   | 方法名稱   | 描述|
|---------|----------|---------------------------------------------------------------------------------------------|
| blur    | .blur()  | 當元素失去焦點時觸發，常用於表單驗證等場景。               |
| change  | .change()| 當元素的值發生變化且失去焦點時觸發，適用於選擇框、勾選框等元素。|
| focus   | .focus() | 當元素獲得焦點時觸發，可以用於高亮顯示當前操作的輸入框。         |
| focusin | .focusin()| 與 focus 事件類似，但它支持事件冒泡。此 API 已棄用。用`.on( "focusin" [, eventData ], handler )`|
| focusout| .focusout()| 與 blur 事件類似，但它支持事件冒泡。此 API 已棄用。用`.on( "focusout" [, eventData ], handler )`|
| select  | .select()| 當用戶選擇文本框（input/textarea）中的一段文字時觸發。         |
| submit  | .submit()| 當表單提交時觸發，可以用於在提交前進行表單驗證。             |

### 使用範例

#### 1. blur 事件

**.blur()**
當元素失去焦點時觸發。常用於表單欄位驗證。

```javascript
$('#inputField').blur(function() {
  console.log('Input field has lost focus');
});
```

#### 2. change 事件

**.change()**
當元素的值變更並失去焦點後觸發。適合用於下拉選單或勾選框。

```javascript
$('#selectBox').change(function() {
  console.log('The selected value has changed');
});
```

#### 3. focus 事件

**.focus()**
當元素獲得焦點時觸發，可用於高亮顯示當前操作的輸入框。

```javascript
$('#inputField').focus(function() {
  console.log('Input field is focused');
});
```

#### 4. select 事件

**.select()**
當用戶選擇文本框中的文字時觸發。

```javascript
$('#textField').select(function() {
  console.log('Text has been selected');
});
```

#### 5. submit 事件

**.submit()**
當表單提交時觸發，可用於表單驗證。

```javascript
$('#myForm').submit(function(event) {
  event.preventDefault(); // 阻止表單預設提交行為
  console.log('Form is submitted');
});
```

### HTML 完整範例

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<title>jQuery 表單事件示例</title>
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>

<form id="myForm">
  <label for="inputField">姓名：</label>
  <input type="text" id="inputField" name="name"><br><br>
  
  <label for="selectBox">選擇年齡範圍：</label>
  <select id="selectBox" name="ageRange">
    <option value="20-29">20-29</option>
    <option value="30-39">30-39</option>
    <option value="40-49">40-49</option>
  </select><br><br>
  
  <input type="submit" value="提交">
</form>

<script>
$(document).ready(function() {
  // 當元素獲得焦點
  $('#inputField').focus(function() {
    console.log('Input field is focused');
    $(this).css('background-color', '#FFFFCC');
  });
  
  // 當元素失去焦點
  $('#inputField').blur(function() {
    console.log('Input field has lost focus');
    $(this).css('background-color', '#FFFFFF');
  });
  
  // 當下拉選單的選項變更
  $('#selectBox').change(function() {
    console.log('The selected age range has changed to: ' + $(this).val());
  });
  
  // 當表單提交
  $('#myForm').submit(function(event) {
    event.preventDefault(); // 阻止表單預設提交行為
    alert('Form Submitted!');
  });
});
</script>

</body>
</html>
```

#### 功能說明

- **文本輸入框 (`inputField`)**
  - 獲得焦點時，背景顏色變為淺黃色。
  - 失去焦點時，背景顏色恢復為白色。
- **下拉選單 (`selectBox`)**
  - 選項變更時，在控制台打印出當前選擇的值。
- **表單提交 (`myForm`)**
  - 提交表單時，阻止表單的預設提交行為，並顯示一個提示訊息。



