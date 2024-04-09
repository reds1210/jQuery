# 動畫

jQuery 提供了多種簡單而強大的方法來創建動畫效果，使網頁元素的顯示和隱藏、移動、改變尺寸等操作更加生動和有趣。

## 基本動畫方法

- **.show() / .hide()**
  這兩個方法用於顯示和隱藏選定的元素，可以接受一個時間參數來控制顯示或隱藏的速度。

- **.fadeIn() / .fadeOut()**
  用於讓元素逐漸顯示（淡入）或隱藏（淡出）。也可以指定動畫的持續時間。

- **.slideDown() / .slideUp()**
  這對方法讓選定的元素以滑動的方式顯示（向下）或隱藏（向上）。同樣，可以設置動畫的持續時間。

## 高級動畫 - .animate()

`.animate()` 方法提供了更高級的動畫控制能力，允許對元素的多個樣式屬性同時進行動畫操作。你可以自定義動畫的持續時間、速度曲線（easing function）和完成動畫後的回調函數。

### 範例

#### 使用 .slideDown() 顯示一個隱藏的元素

```html
<button id="showButton">Show Content</button>
<div id="content" style="display:none;">Hello World!</div>

<script>
$("#showButton").click(function(){
  $("#content").slideDown("slow");
});
</script>
```

#### 使用 .animate() 改變元素尺寸

```html
<button id="animateButton">Animate Size</button>
<div id="box" style="background:#98bf21;height:100px;width:100px;position:absolute;"></div>

<script>
$("#animateButton").click(function(){
  $("#box").animate({
    height: "toggle",
    width: "toggle"
  });
});
</script>
```


## `.show()` 

用於顯示被隱藏的匹配元素。它通過設定元素的 CSS `display` 屬性為適當的值來實現，基本上逆轉了 `.hide()` 的效果。如果元素原本的顯示值是 `none`，`.show()` 會將它設置為該元素的默認顯示值。

### 基本使用

```javascript
$(selector).show();
```

- `selector`：用來查找你想要顯示的元素。

### 示例：顯示一個隱藏的段落

HTML：

```html
<p id="hiddenParagraph" style="display: none;">I was hidden, but now I'm shown!</p>
<button id="showButton">Show Paragraph</button>
```

JavaScript：

```javascript
$('#showButton').click(function() {
    $('#hiddenParagraph').show();
});
```

### 進階使用與參數

`.show()` 也可以接受參數，以創造更動態的效果，例如速度、緩動和回調函數。

```javascript
$(selector).show(speed, [easing], [callback])
```

- `speed`：可以是字串（'slow', 'fast'）或毫秒數，定義動畫持續的時間。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩個內置值：`'swing'` 和 `'linear'`。
- `callback`：（可選）顯示操作完成後執行的函數。

### 示例：帶動畫的顯示

```javascript
$('#showButton').click(function() {
    $('#hiddenParagraph').show(500, function() {
        // 這個函數在段落顯示後被調用
        alert('Paragraph is now visible!');
    });
});
```


## `.hide()`

用於隱藏選擇器匹配的元素。它將display所選元素的CSS 屬性變更為none，使它們在頁面上不可見。

### 基本用法

```javascript
$(selector).hide();
```
- `selector`：這是用於尋找要隱藏的元素的 jQuery 選擇器。

### 範例：點擊按鈕時隱藏段落

想像一下，當使用者點擊按鈕時，您想要隱藏一個段落。

HMTL:
```html
<p id="visibleParagraph">I'm visible now, but soon I'll be hidden!</p>
<button id="hideButton">Hide Paragraph</button>
```
JavaScript：

```javascript
$('#hideButton').click(function() {
    $('#visibleParagraph').hide();
});
```


### 帶參數的高階用法

`.hide()`還可以帶參數使隱藏過程動畫化，這樣可以透過使過渡更加平滑來增強使用者體驗。

```javascript
$(selector).hide(speed, [easing], [callback])
```

- `speed`: 可以是字串 ( `'slow'`, `'fast'`) 或代表毫秒的數字。這決定了隱藏動畫需要多長時間。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩個內置值：`'swing'` 和 `'linear'`。
- `callback`：（可選）隱藏操作完成後執行的函數。

### 範例：用動畫隱藏

```javascript
$('#hideButton').click(function() {
    $('#visibleParagraph').hide(500, function() {
        // This function is called after the paragraph is hidden
        alert('Paragraph is now hidden!');
    });
});
```

## `.fadeIn()` 

用於逐漸改變匹配元素的不透明度，從隱藏到可見，創造出一種平滑的淡入效果。這個方法通過動畫改變匹配元素的不透明度，有效地讓它們淡入。

### 基本使用

```javascript
$(selector).fadeIn(duration, [easing], [callback]);
```

- `selector`：用於找到你想要淡入的元素。
- `duration`：動畫的持續時間，以毫秒計或預定義的字串 `'slow'` 或 `'fast'` 表示。這個參數是可選的，如果未指定，預設為 400 毫秒。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩個內置值：`'swing'` 和 `'linear'`。
- `callback`：（可選）動畫完成後調用的函數。

### 示例：淡入一個隱藏的元素

HTML：

```html
<div id="hiddenDiv" style="display: none;">I will fade in!</div>
<button id="fadeInButton">Fade In Div</button>
```

JavaScript：

```javascript
$('#fadeInButton').click(function() {
    $('#hiddenDiv').fadeIn();
});
```

### 進階使用與參數

```javascript
$('#fadeInButton').click(function() {
    $('#hiddenDiv').fadeIn(1000, 'linear', function() {
        alert('The div is now fully visible!');
    });
});
```

## `.fadeOut()`

用於逐漸變淡並隱藏匹配的元素。它通過逐漸減少元素的不透明度來實現，直至達到完全透明，然後將元素的顯示屬性設置為 `none`。這個過程是透過動畫實現的，可以自定義動畫的時長和速度曲線。

### 基本使用

```javascript
$(selector).fadeOut();
```

- `selector`：用來查找你想要隱藏的元素。

### 示例：隱藏一個可見的段落

HTML：

```html
<p id="visibleParagraph">I'm visible now, but soon will be hidden!</p>
<button id="fadeOutButton">Fade Out Paragraph</button>
```

JavaScript：

```javascript
$('#fadeOutButton').click(function() {
    $('#visibleParagraph').fadeOut();
});
```

### 進階使用與參數

`.fadeOut()` 方法也接受參數，以允許更多的自定義，包括動畫的持續時間、緩動效果和完成動畫後的回調函數。

```javascript
$(selector).fadeOut(speed, [easing], [callback])
```

- `speed`：定義動畫持續的時間，可以是毫秒數或以下字串之一：'slow', 'fast'。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩個內置值：`'swing'` 和 `'linear'`。
- `callback`：（可選）動畫完成後執行的函數，可以用來觸發其他動作或通知。

### 示例：帶有完成回調的淡出

```javascript
$('#fadeOutButton').click(function() {
    $('#visibleParagraph').fadeOut(500, function() {
        // 這個函數在段落淡出後被調用
        alert('Paragraph is now hidden!');
    });
});
```

## `.slideDown()`

用於逐漸顯示被隱藏元素的一種動畫效果，通過增加元素的高度來給予滑動向下進入視圖的效果。特別適用於下拉菜單、手風琴效果或簡單地顯示更多內容。

### 基本使用

```javascript
$(selector).slideDown(duration, [easing], [callback]);
```

- `selector`：這是用來查找你想要進行滑動下來顯示的元素的 jQuery 選擇器。
- `duration`：動畫的持續時間，可以是毫秒數或使用預定義的字串 `'slow'` 或 `'fast'`。如果未指定，則默認為 400 毫秒。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩個內置值：`'swing'` 和 `'linear'`。
- `callback`：（可選）動畫完成後調用的函數。

### 示例：滑動下來顯示一個隱藏元素

HTML：

```html
<div id="hiddenContent" style="display: none;">驚喜內容！</div>
<button id="slideDownButton">顯示內容</button>
```

JavaScript：

```javascript
$('#slideDownButton').click(function() {
    $('#hiddenContent').slideDown();
});
```

### 進階使用與參數

```javascript
$('#slideDownButton').click(function() {
    $('#hiddenContent').slideDown(1000, 'linear', function() {
        alert('Hi');
    });
});
```


## `.slideUp()`

用於逐漸隱藏元素，通過動畫減少元素的高度直至為0，從而達到滑動向上並消失的效果。這種方法非常適合於隱藏下拉菜單、手風琴內容或簡單地收起不再需要顯示的信息。

### 基本使用

```javascript
$(selector).slideUp(duration, [easing], [callback]);
```

- `selector`：用於選擇目標元素的 jQuery 選擇器。
- `duration`：動畫的持續時間，可以是毫秒數，或者是預定義的字串 `'slow'` 或 `'fast'`。如果未指定，則默認為 400 毫秒。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩種內建值：`'swing'` 和 `'linear'`。
- `callback`：（可選）一旦動畫完成，就調用這個函數。

### 示例：向上滑動隱藏元素

HTML：

```html
<div id="visibleContent">很快會被隱藏。</div>
<button id="slideUpButton">隱藏內容</button>
```

JavaScript：

```javascript
$('#slideUpButton').click(function() {
    $('#visibleContent').slideUp();
});
```

### 進階使用與參數

```javascript
$('#slideUpButton').click(function() {
    $('#visibleContent').slideUp(1000, 'linear', function() {
        alert('bye');
    });
});
```

## `.toggle()`

切換元素的可見狀態。當被調用時，如果元素是可見的，它會隱藏元素；如果元素是隱藏的，則會顯示元素。這種方法非常適合於用戶交互操作，如點擊按鈕來顯示或隱藏內容。

### 基本使用

```javascript
$(selector).toggle();
```

- `selector`：選擇目標元素的 jQuery 選擇器。

使用 `.toggle()` 方法時不需要指定參數，它會根據元素當前的顯示狀態來自動進行切換。

### 示例：切換元素的可見性

HTML：

```html
<p id="toggleContent">點擊按鈕切換我的可見性。</p>
<button id="toggleButton">切換</button>
```

JavaScript：

```javascript
$('#toggleButton').click(function() {
    $('#toggleContent').toggle();
});
```

### 進階使用與參數

`.toggle()` 方法也支持動畫參數，允許在切換顯示狀態時添加動畫效果。

```javascript
$(selector).toggle(duration, [easing], [callback]);
```

- `duration`：動畫持續時間，可以是毫秒數或預定義的字符串 `'slow'` 或 `'fast'`。
- `easing`：（可選）指定用於過渡的緩動函數。jQuery 提供兩種內建值：`'swing'` 和 `'linear'`。
- `callback`：（可選）動畫完成後執行的函數。

### 示例：帶動畫效果的切換

```javascript
$('#toggleButton').click(function() {
    $('#toggleContent').toggle(500, 'swing', function() {
        alert('切換完成！');
    });
});
```

## `.delay()`

用於設置在執行隊列中的下一個動畫之前的延遲時間。這個方法允許你在連續的 jQuery 效果之間添加暫停，而無需使用複雜的 JavaScript `setTimeout` 函數。

### 基本使用

```javascript
$(selector).delay(duration, [queueName]);
```

- `selector`：選擇目標元素的 jQuery 選擇器。
- `duration`：延遲的時間，以毫秒為單位。
- `queueName`：（可選）指定延遲應用於哪個隊列。如果未指定，則默認為 `fx`，即標準動畫隊列。

### 示例：在動畫之間添加延遲

HTML：

```html
<div id="delayedElement">淡出然後淡入。</div>
```

JavaScript：

```javascript
$('#delayedElement').fadeOut().delay(1000).fadeIn();
```
