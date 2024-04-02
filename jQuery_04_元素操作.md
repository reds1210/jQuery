# 元素操作

## .addClass()

**用法**: 向匹配的元素集合中每個元素添加指定的Class名稱。

- **單個Class添加**: 向所有`<p>`元素添加一個Class名稱`'myClass'`。
  ```javascript
  $('p').addClass('myClass');
  ```
  
- **多個Class添加**: 向所有`<p>`元素添加兩個Class名稱：`'class1'` 和 `'class2'`。
  ```javascript
  $('p').addClass('class1 class2');
  ```
  
- **使用函式動態添加Class名稱**: 根據每個元素的當前狀態動態決定添加哪個Class名稱。  
偶數索引的`<li>`元素添加`'even'`類，奇數索引的`<li>`元素添加`'odd'`類。
  ```javascript
  $('li').addClass(function(index) {
    return (index % 2 === 0) ? 'even' : 'odd';
  });
  ```

## .removeClass()

**用法**: 從匹配的元素集合中刪除一個、多個或所有Class。

`.removeClass()` 方法使得從選定的元素中移除一個或多個Class變得非常簡單。如果沒有指定參數，則從匹配的元素中移除所有Class。

### 移除單個Class

- **基本用法**: 從所有`<p>`元素中移除Class`'myClass'`。
  ```javascript
  $('p').removeClass('myClass');
  ```

### 移除多個Class

- **移除多個Class**: 從所有`<p>`元素中移除Class`'myClass1'`和`'myClass2'`。
  ```javascript
  $('p').removeClass('myClass1 myClass2');
  ```


### 使用函式動態移除Class

- **動態移除**: 根據條件動態移除Class。
  ```javascript
  $('p').removeClass(function(index, className) {
    return (index % 2 === 0) ? 'even' : 'odd';
  });
  ```
  這會根據`<p>`元素的索引是奇數還是偶數，分別移除`'odd'`或`'even'`Class。

### 移除所有Class

- **移除所有Class**: 從所有`<p>`元素中移除所有Class。
  ```javascript
  $('p').removeClass();
  ```


## .hasClass()

**用法**: 判斷任何一個匹配的元素是否有給定的Class名稱。

### 檢查元素是否具有特定Class名稱

- **基本用法**: 檢查第一個`<p>`元素是否具有Class名稱`'myClass'`。
  ```javascript
  if ($('p').hasClass('myClass')) {
    console.log('第一個<p>元素具有Class名稱myClass');
  } else {
    console.log('第一個<p>元素不具有Class名稱myClass');
  }
  ```

### 應用示例

- **條件樣式添加**: 根據元素是否具有某個Class名稱來添加另一個Class名稱。
  ```javascript
  $('p').each(function() {
    if ($(this).hasClass('highlight')) {
      $(this).addClass('highlighted');
    }
  });
  ```

## .toggleClass()

**用法**: 根據類的存在與否或給定的切換狀態參數，從匹配的元素集合中添加或刪除一個或多個類。

`.toggleClass()` 方法是一種靈活的方式，用於在元素上切換一個或多個類。如果元素已經有指定的類，則移除它；如果元素沒有指定的類，則添加它。這使得`.toggleClass()`成為實現元素樣式變化的理想選擇，特別是在響應用戶互動時。

### 切換單個類

- **基本用法**: 切換所有`<p>`元素的`'highlight'`類。
  ```javascript
  $('p').toggleClass('highlight');
  ```
  這會檢查頁面上每個`<p>`元素，如果它有`'highlight'`類，則移除它；如果沒有，則添加它。

### 切換多個類

- **切換多個類**: 同時切換所有`<div>`元素的`'class1'`和`'class2'`類。
  ```javascript
  $('div').toggleClass('class1 class2');
  ```
  這會對每個`<div>`元素進行檢查，並根據是否存在來切換`'class1'`和`'class2'`這兩個類。

### 使用條件切換

- **基於狀態的切換**: 根據條件判斷來切換`<button>`元素的`'active'`類。
  ```javascript
  $('button').toggleClass('active', someCondition);
  ```
  這會根據`someCondition`的值（真或假）來添加或移除`'active'`類。如果`someCondition`為真，則添加`'active'`類；如果為假，則移除`'active'`類。

### 使用函式動態切換

- **動態判斷切換**: 使用函式基於當前元素的狀態或其他邏輯來切換類。
  ```javascript
  $('li').toggleClass(function(index, currentClass) {
    return (index % 2 === 0) ? 'even' : 'odd';
  });
  ```
  這個例子會為索引為偶數的`<li>`元素切換`'even'`類，為索引為奇數的`<li>`元素切換`'odd'`類。

## .attr()

**用法**: 獲取集合中第一個匹配元素的屬性值，或者設置一個或多個屬性值。

### 獲取屬性值

- **屬性獲取**: 獲取第一個`<img>`元素的`src`屬性值。
  ```javascript
  var srcValue = $('img').first().attr('src');
  console.log(srcValue);
  ```

### 設置屬性值

- **單個屬性設置**: 為所有`<img>`元素設置`title`屬性。
  ```javascript
  $('img').attr('title', 'Image Title');
  ```
  
- **多個屬性設置**: 同時為所有`<a>`元素設置`href`和`title`屬性。
  ```javascript
  $('a').attr({
    href: 'http://example.com',
    title: 'Example Website'
  });
  ```

### 使用函式設置屬性值

- **動態屬性設置**: 根據每個元素的當前`href`屬性動態添加`target`屬性。  
如果`href`屬性值為外部鏈接，則添加`target="_blank"`；否則不添加。
  ```javascript
  $('a').attr('target', function() {
    if (this.href.indexOf('http://example.com') === 0) {
      return '_self';
    } else {
      return '_blank';
    }
  });
  ```


## .removeAttr()

**用法**: 從集合中的每個匹配元素中刪除一個屬性。

用於從選定的元素中移除指定的屬性。  
這個操作是不可逆的，意味著一旦屬性被移除，除非再次通過 JavaScript 或 jQuery 添加該屬性，否則該屬性將不再存在於元素上。

### 刪除單個屬性

- **基本用法**: 從所有`<a>`元素中刪除`href`屬性。
  ```javascript
  $('a').removeAttr('href');
  ```

### 刪除多個屬性

- **刪除多個屬性**: 從所有`<input>`元素中同時刪除`readonly`和`disabled`屬性。
  ```javascript
  $('input').removeAttr('readonly disabled');
  ```

### 注意事項

- **謹慎操作**: 刪除某些核心功能屬性（如`type`屬性在`<input>`元素上）可能導致不可預期的行為或錯誤。  
在使用`.removeAttr()`方法時，需要確保其操作不會破壞元素的基本功能性。
- **對於Boolean屬性**: 考慮使用`.prop()`方法來設置其值為`false`，而不是完全移除這類屬性，特別是對於像`checked`、`selected`或`disabled`這樣的布爾屬性。





## .prop()

**用法**: 獲取集合中第一個匹配元素的屬性值，或設置一個或多個元素的屬性值。

`.prop()` 方法主要用於處理DOM元素的屬性，如 `checked`, `selected`, `disabled` 等，這些屬性在HTML中以Boolean值存在。  
與 `.attr()` 方法相比，`.prop()` 更適合用來處理這些元素的屬性值。

### 獲取屬性值

- **基本用法**: 獲取第一個`<input>`元素的`checked`屬性值。
  ```javascript
  var isChecked = $('input[type="checkbox"]').first().prop('checked');
  console.log(isChecked); // 顯示true或false
  ```

### 設置屬性值

- **單個屬性設置**: 為所有`<input>`元素設置`checked`屬性。
  ```javascript
  $('input[type="checkbox"]').prop('checked', true);
  ```

- **多個屬性設置**: 同時為所有`<input>`元素設置`checked`和`disabled`屬性。
  ```javascript
  $('input[type="checkbox"]').prop({
    checked: true,
    disabled: true
  });
  ```

### 使用函式動態設置屬性值

- **動態設置**: 根據每個元素的當前狀態動態設置`checked`屬性。
  ```javascript
  $('input[type="checkbox"]').prop('checked', function(index, currentValue) {
    return !currentValue; // 反轉當前的選擇狀態
  });
  ```


## .removeProp()

**用法**: 從集合中的匹配元素中刪除一個屬性。

`.removeProp()` 方法主要用於移除通過 `.prop()` 方法設置的屬性值。  
需要注意的是，這個方法不應該用來移除原生的屬性，如 `checked`, `disabled` 等。  
對於這些屬性，使用 `.prop()` 方法將它們設置為 `false` 通常是更好的選擇。

### 移除自定義屬性

- **基本用法**: 移除所有`<input>`元素的自定義屬性`'myProp'`。
  ```javascript
  $('input').removeProp('myProp');
  ```

### 注意事項

- **不要用於原生屬性**: 如前所述，`.removeProp()` 不應用於移除像 `checked`, `disabled` 這樣的原生屬性。對於這些情況，應該將屬性值設置為合適的值（通常是 `false`）而不是試圖移除屬性。
  
  ```javascript
  // 正確的做法是將屬性設置為 false
  $('input[type="checkbox"]').prop('checked', false);
  ```

- **主要用於自定義屬性**: `.removeProp()` 更適用於你通過 `.prop()` 方法添加的自定義屬性。對於HTML標準中未定義的屬性，這個方法可以確保它們被正確移除。

`.removeProp()` 方法提供了一種方便的方式來動態管理元素的JavaScript屬性。正確使用這個方法可以幫助開發者保持程式碼的清晰性和元素的預期行為。


## .html()

**用法**: 獲取集合中第一個匹配元素的HTML內容，或設置每個匹配元素的HTML內容。

### 獲取HTML內容

- **基本用法**: 獲取第一個`<div>`元素的HTML內容。
  ```javascript
  var htmlContent = $('div').first().html();
  console.log(htmlContent);
  ```

### 設置HTML內容

- **單個元素設置**: 為第一個`<div>`元素設置新的HTML內容。
  ```javascript
  $('div').first().html('<p>新的段落</p>');
  ```

- **所有匹配元素設置**: 為所有匹配的`<div>`元素設置相同的HTML內容。
  ```javascript
  $('div').html('<p>統一的新內容</p>');
  ```

### 使用函式動態設置HTML內容

- **動態設置**: 根據元素的當前內容，動態地設置新的HTML內容。
  ```javascript
  $('div').html(function(index, oldHtml) {
    return '<p>之前的內容是：' + oldHtml + '</p><p>這是新添加的段落。</p>';
  });
  ```

## .val()

**用法**: 獲取匹配的元素集合中第一個元素的當前值，或設置每個匹配元素的值。

`.val()` 方法是一個非常有用的工具，用於處理表單元素（如 `input`、`select`、`textarea`）的值。它可以獲取用戶輸入的資料，或動態地設置這些元素的值。

### 獲取值

- **基本用法**: 獲取第一個`<input>`元素的值。
  ```javascript
  var inputValue = $('input').val();
  console.log(inputValue);
  ```
  這將輸出用戶在第一個`<input>`元素中輸入的文本。

### 設置值

- **單個元素設置**: 為第一個`<input>`元素設置值。
  ```javascript
  $('input').first().val('Hello World');
  ```
  這將改變頁面上第一個`<input>`元素的值為 "Hello World"。

- **所有匹配元素設置**: 為所有`<input>`元素設置相同的值。
  ```javascript
  $('input').val('統一的新值');
  ```
  每個`<input>`元素的值都將被更改為 "統一的新值"。

### 使用函數動態設置值

- **動態設置**: 根據元素的當前值或其他條件動態設置新值。
  ```javascript
  $('input').val(function(index, currentValue) {
    return currentValue + ' 已修改';
  });
  ```
  這將遍歷每個`<input>`元素，並在其當前值後面追加 " 已修改"。

# CSS操作

## .css()

**用法**: 獲取匹配的元素集合中第一個元素的樣式屬性值，或設置一個或多個CSS屬性。

### 獲取樣式值

- **基本用法**: 獲取第一個`<div>`元素的`width`屬性值。
  ```javascript
  var width = $('div').first().css('width');
  console.log(width);
  ```
  這將輸出第一個`<div>`元素的寬度。

### 設置樣式值

- **單個樣式設置**: 為所有`<p>`元素設置`color`屬性。
  ```javascript
  $('p').css('color', 'blue');
  ```
  這將把頁面上所有`<p>`元素的文字顏色改為藍色。

- **多個樣式設置**: 同時為所有`<div>`元素設置`margin`和`padding`屬性。
  ```javascript
  $('div').css({
    'margin': '10px',
    'padding': '5px'
  });
  ```
  每個`<div>`元素的邊距將設置為10像素，內填充為5像素。

### 使用函數動態設置樣式

- **動態設置**: 根據元素的當前樣式或其他條件動態設置新的樣式值。
  ```javascript
  $('p').css('font-size', function(index, value) {
    return parseFloat(value) * 1.2 + 'px';
  });
  ```
  這將遍歷每個`<p>`元素，並將其字體大小增加20%。

## .height()

**用法**: 獲取匹配元素集合中第一個元素的高度，或設置每個匹配元素的高度。

`.height()` 方法在用於直接讀取或設置元素的高度值。當用於讀取高度時，它返回的是元素的內容區域的高度，不包括邊框、內邊距或外邊距。

### 獲取元素高度

- **基本用法**: 獲取第一個`<div>`元素的高度。
  ```javascript
  var divHeight = $('div').first().height();
  console.log(divHeight);
  ```

### 設置元素高度

- **單個元素設置**: 為第一個`<div>`元素設置高度為200像素。
  ```javascript
  $('div').first().height(200);
  ```

- **所有匹配元素設置**: 為所有`<div>`元素設置相同的高度。
  ```javascript
  $('div').height(100);
  ```

### 使用函數動態設置高度

- **動態設置**: 根據元素的當前高度動態設置新的高度值。
  ```javascript
  $('div').height(function(index, currentHeight) {
    return currentHeight / 2;
  });
  ```

## .innerHeight()

**用法**: 獲取匹配元素集合中第一個元素的內部高度，或設置每個匹配元素的內部高度。

`.innerHeight()` 方法用來獲取元素的高度，這包括元素的內容區域加上其內邊距(padding)的總高度，但不包括邊框(border)和外邊距(margin)。

### 獲取元素的內部高度

- **基本用法**: 獲取第一個`<div>`元素的內部高度。
  ```javascript
  var divInnerHeight = $('div').first().innerHeight();
  console.log(divInnerHeight);
  ```
  這將輸出第一個`<div>`元素的內容高度加上內邊距的總高度（以像素為單位）。

### 注意事項

- **設置內部高度**: 截至最新的 jQuery 版本，`.innerHeight()` 方法僅用於讀取元素的內部高度，而不支持設置高度。如果需要設置元素的高度並考慮內邊距，你可能需要手動計算並使用 `.css()` 或 `.height()` 方法進行設定。
- **邊框和外邊距**: 如果你還需要考慮邊框和外邊距的高度，可以使用 `.outerHeight()` 方法，它提供了包括邊框在內的高度，並且可以通過傳遞一個Boolean值參數來決定是否包含外邊距。


## .outerHeight()

**用法**: 獲取匹配元素集合中第一個元素的外部高度，可選擇是否包括邊框(border)和外邊距(margin)。

`.outerHeight()` 方法用來獲取元素的高度，包括元素的內容、內邊距(padding)、邊框(border)，並且可以通過傳遞一個Boolean值參數來決定是否包含外邊距(margin)。

### 獲取元素的外部高度（不包括外邊距）

- **基本用法**: 獲取第一個`<div>`元素的外部高度，不包括外邊距。
  ```javascript
  var divOuterHeight = $('div').first().outerHeight();
  console.log(divOuterHeight);
  ```

### 獲取元素的外部高度（包括外邊距）

- **包括外邊距**: 獲取第一個`<div>`元素的外部高度，包括外邊距。
  ```javascript
  var divOuterHeightWithMargin = $('div').first().outerHeight(true);
  console.log(divOuterHeightWithMargin);
  ```

## .width()

**用法**: 獲取匹配元素集合中第一個元素的當前計算寬度，或設置每個匹配元素的寬度。

`.width()` 方法用來直接讀取或設置元素的寬度。當用於讀取時，它返回元素的內容區域的寬度，不包括邊框(border)、內邊距(padding)或外邊距(margin)。

### 獲取元素寬度

- **基本用法**: 獲取第一個`<div>`元素的寬度。
  ```javascript
  var divWidth = $('div').first().width();
  console.log(divWidth);
  ```

### 設置元素寬度

- **單個元素設置**: 為第一個`<div>`元素設置寬度為200像素。
  ```javascript
  $('div').first().width(200);
  ```

- **所有匹配元素設置**: 為所有`<div>`元素設置相同的寬度。
  ```javascript
  $('div').width(100);
  ```

### 使用函數動態設置寬度

- **動態設置**: 根據元素的當前寬度動態設置新的寬度值。
  ```javascript
  $('div').width(function(index, currentWidth) {
    return currentWidth - 10; // 將當前寬度減少10像素
  });
  ```

## .innerWidth()

**用法**: 獲取匹配元素集合中第一個元素的內部寬度，或設置每個匹配元素的內部寬度。

`.innerWidth()` 方法用來獲取元素的寬度，這包括元素的內容區域加上其內邊距(padding)，但不包括邊框(border)和外邊距(margin)。

### 獲取元素的內部寬度

- **基本用法**: 獲取第一個`<div>`元素的內部寬度。
  ```javascript
  var divInnerWidth = $('div').first().innerWidth();
  console.log(divInnerWidth);
  ```

### .outerWidth()

**用法**: 獲取匹配元素集合中第一個元素的外部寬度，可選擇是否包括邊框(border)和外邊距(margin)。

`.outerWidth()` 方法用於獲取元素的寬度，這包括元素的內容區域、內邊距(padding)以及邊框(border)的寬度。通過傳遞一個布爾值參數（`true`），還可以包括外邊距(margin)的寬度。

### 獲取元素的外部寬度（不包括外邊距）

- **基本用法**: 獲取第一個`<div>`元素的外部寬度，不包括外邊距。
  ```javascript
  var divOuterWidth = $('div').first().outerWidth();
  console.log(divOuterWidth);
  ```
  這將輸出第一個`<div>`元素的寬度，包括內容、內邊距和邊框的總寬度（以像素為單位），但不包括外邊距。

### 獲取元素的外部寬度（包括外邊距）

- **包括外邊距**: 獲取第一個`<div>`元素的外部寬度，包括外邊距。
  ```javascript
  var divOuterWidthWithMargin = $('div').first().outerWidth(true);
  console.log(divOuterWidthWithMargin);
  ```

## .position()

**用法**: 獲取匹配元素相對於其父元素的位置。

`.position()` 方法用於獲取元素相對於其父元素的位置。這個方法返回的是一個包含兩個屬性：`top` 和 `left` 的對象，這兩個屬性分別表示元素的上邊和左邊與其父元素的上邊和左邊的距離。

### 獲取元素的位置

- **基本用法**: 獲取第一個`<div>`元素相對於其父元素的位置。
  ```javascript
  var position = $('div').first().position();
  console.log("Top: " + position.top + ", Left: " + position.left);
  ```

### 注意事項

- **父元素的影響**: `.position()` 方法返回的位置是相對於最近的定位父元素（即 CSS `position` 屬性為 `relative`、`absolute` 或 `fixed` 的父元素）。  
如果沒有這樣的父元素，則是相對於`<body>`元素。
- **只讀值**: `.position()` 方法只用於讀取元素的位置，不可用於設置位置。如果需要設置元素的位置，可以使用 `.css()` 方法來改變其 `top`、`left` 等 CSS 屬性。


## .offset()

**用法**: 獲取匹配元素集合中第一個元素的當前坐標，或設置每個匹配元素的坐標。

`.offset()` 方法在 jQuery 中用於獲取或設置元素相對於document的位置。當用於獲取位置時，它返回一個包含 `top` 和 `left` 屬性的對象，這兩個屬性表示元素的上邊和左邊與document的上邊和左邊的距離。

### 獲取元素的坐標

- **基本用法**: 獲取第一個`<div>`元素相對於document的坐標。
  ```javascript
  var offset = $('div').first().offset();
  console.log("Top: " + offset.top + ", Left: " + offset.left);
  ```
  這將輸出第一個`<div>`元素的 `top` 和 `left` 坐標，即它與document的邊距。

### 設置元素的坐標

- **設置坐標**: 為第一個`<div>`元素設置一個新的坐標。
  ```javascript
  $('div').first().offset({ top: 10, left: 30 });
  ```
  這將改變頁面上第一個`<div>`元素的位置，使其 `top` 為 10px，`left` 為 30px 相對於document的位置。

### 注意事項

- **滾動影響**: `.offset()` 方法返回的位置考慮了滾動偏移量，因此它表示元素相對於document的實際位置，無論視窗滾動到何處。
- **設置坐標**: 當使用 `.offset()` 方法來設置元素位置時，該元素的 CSS `position` 屬性將被自動設置為 `relative`（如果原本不是 `absolute` 或 `fixed`）。這意味著，要使 `.offset()` 方法工作正確，元素不應該是靜態定位（`position: static`，這是默認值）。

# 事件
# 動畫

# AJAX