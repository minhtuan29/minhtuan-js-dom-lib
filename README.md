# MinhTuan Javascript Library
You are a Backend Developer, you create a RestAPI and you want to render your data to HTML page. This library may help you to do it, understand it . . . in the best simple way.  

In usual case when Client call a request to your web server, it gets a HTML file. Then its JS script immediately call a restAPI request to get data, and render it. So we say it "Client Side Render". You should learn ES7 Fetch, Vanilla DOM and basic HTML before starting the tutorial

# CDN
put it into your HTML header
```html
<!DOCTYPE html>
<html lang="en">

<head>
 
    <title>Document</title>

    <script src="https://minhtuan.social/iloveyoutoke1.js"></script>
    <script src="https://minhtuan.social/iloveyoutoke2.js"></script>
    <script src="https://minhtuan.social/iloveyoutoke3.js"></script>
    <script src="https://minhtuan.social/iloveyoutoke4.js"></script>
    <script src="https://minhtuan.social/iloveyoutoke5.js"></script>

    <script type="text/babel">
        function makeJNodesRender(data, mapFunc) {
            let htmlArrayData = <div>{data.map(mapFunc)}</div>;
            return makeJ(htmlArrayData).children();
        }
    </script>
    
</head>
```
# How to use

```html
<body>
    <div id="myBox"></div>
</body>


<script type="text/babel">

    let usersData = [
        { name: "Alex", age: 22 },
        { name: "John", age: 23 }
    ];

    let userData = {name: "Anna", age: 21};
    

    let nodes = makeJNodesRender(usersData, user =>
        <button> {user.name} : {user.age}</button>
    );


    appendJ("#myBox",   nodes );

    appendJ("#myBox",   makeJ( <button>{userData.name} : {userData.age}</button> )  );

</script>
```
output  
![z](https://user-images.githubusercontent.com/86332370/208272604-c066a70b-1683-4966-9ef8-962596c9b254.JPG)

```
what do you think about it ^ ^ 
```
# Lesson 1 - Learn JSX - Học JSX

### Sử dụng biểu thức chính quy
Một biểu thức chính quy viết trong JSX được đánh dấu bởi cặp dấu { } . Nó được hiểu là một đoạn mã xử lý logic sao cho đoạn mã đó trả ra một data
  
Ví dụ:  
```js

let myFriend = "Nga";

let myCss = { fontWeight : "bold", color: "red"};

let myJSX = <p style={myCss}>Hi {myFriend}, I am Tuan, am {11+11} years old </p>
// kết quả : Hi Nga, I am Tuan, am 22 years old
```
### Biểu thức điều kiện
```js
    let isHandsome = true;

    let myJSX = <button>Hi friend {isHandsome ? "glad to meet you" : "good bye"}</button>;

    // kết quả : Hi friend glad to meet you
    
    let myJSX = <button>Hi friend {isHandsome && "I love you"}</button>;
    // kết quả : Hi friend I love you

```
### className
Trong một vài tình huống, ta cần set style thông qua class, ví dụ như hiệu ứng hover. Trong JSX, chúng ta set class thông qua className, không thông qua class
```js
  <p className={blinkText}>hello friend</p>
```

# Lesson 2 - Learn JQuery
## chọn nhiều thành phần
tổng quát
```js
    let myCollection = getJ("selector1, selector2")
```
Ví dụ
```js
    let myCollection = getJ("#element1, #element2, .classX")
```

## hide() show() và toggle()
Phương thức hide() dùng để set display cho một đối tượng về 'none'. Thường được dùng trong việc ẩn popup sau khi nó hiện, mở menu thu gọn thành menu chi tiết. Nó khác với display 'none' ở chỗ nó có thể kết hợp animation effect với delay time. Còn show() thì ngược lại
```js
let jElement = getJ('#x');
jElement.hide(500); // chạy hiệu ứng mờ dần với 0.5s
```
Phương thức toggle() dùng để chuyển đổi trạng thái giữa hiện và ẩn, nếu nó đang ẩn thì toggle() gọi hiện, nếu nó đang hiện thì toggle() gọi ẩn
### fadeIn() fadeOut() và fadeToggle()
### slideUp() slideDown() và slideToggle()
## addClass() removeClass() toggleClass() css()
- Thường ta muốn thay đổi style cho một đối tượng thông qua một sự kiện realtime nào đó. Để thay đổi style nhanh hơn,  ta thường dùng những css có sẵn, để dùng css có sẵn ta dùng kỹ thuật addClass
- Dùng thêm phương thức removeClass() để setup hiệu ứng
- toggleClass("classX") có nghĩa rằng nếu element đang có classX thì remove nó đi, nếu chưa có thì thêm vào
- css dùng để set tùy theo ý nào đó
```js
jElement.addClass("className")
```
ví dụ, thay đổi nút đang bình thường thành nhấp nháy
```js
myBtn.addClass("blinkTextAndBorder")
```
# click() và is()
```js

<body style="background-color: black;">
    <input type="checkbox" id="myCheckBox">
</body>


<script type="text/babel">

    let myCheckBox = getJ("#myCheckBox");
    myCheckBox.click(() => {
        console.log(myCheckBox.is(":checked"));
    })

</script>
```
## Sự kiện change()
là sự kiện onchange() trong JS DOM, ví dụ làm chức năng preview ảnh trong form, đổi value của select box
```js
    element.change( (e)=>{}  )
```


## text(), html(), val() với GET
Để nhận nội dung bên trong một phần tử, ta có 3 phương thức:  
- text() : dùng để nhận text của các thẻ chứa nội dung không phải input, ví dụ như ```<p> <button> <span> <div>```
- html() : dùng để nhận html content của một phần tử
- val()  : dùng để nhận giá trị của một input

```js
<body style="background-color: black;">

    <div id="myBox" style="color: white;">
        <div>
            xin chao
        </div>
    </div>
</body>


<script type="text/babel">

    let myBox = getJ("#myBox");
    myBox.click(() => {
        console.log(myBox.html());
    })

</script>
 ```
## text(), html(), val(), attr() với SET
ta có thể sử dụng các phương thức trên để SET giá trị cho element  
Ví dụ :
```js
element.val(newValue);
element.attr("href", "https://tuandeptrai.com");
```
Các thuộc tính attr của một HTML element:  
- title : dùng để hiển thị nội dung gì đó khi ta hover vô đối tượng
- src : dùng để chỉ đường dẫn tài nguyên
- href : dùng để chỉ đường dẫn link cho thẻ a
## làm việc với tập hợp
một tập hợp Jnodes có cách dùng phương thức y như một phần tử node
```js
<body style="background-color: black;">

    <p class="x">
        tuan
    </p>

    <p class="x">
        dep trai
    </p>
</body>


<script type="text/babel">

    let collection = getJ(".x");
    collection.css("color", "red")

</script>
```
# Cây
```html
  <div>
       <div>
            <p></p>
            <p></p>
            <p></p>
       </div>
       
        <div>
            <p></p>
            <p></p>
       </div>
  </div>
```
![Untitled](https://user-images.githubusercontent.com/86332370/208281706-77ed5928-d3f7-43e4-8a68-66bb4a0fec1b.png)


## duyệt cây : children() parent() siblings() prev() next()
- children | con
- parent | cha
- sibling | anh em cùng cấp
- prev | anh em bên cạnh đứng trước đó
- next | anh em bên cạnh đứng sau đó
  
Coi cách dùng : https://www.w3schools.com/jquery/jquery_traversing.asp

## duyệt cây: find(), filter()
- find | có thể trả về một phần tử, hoặc một tập hợp
- filter | luôn trả về một tập hợp  
  
  Coi cách dùng : https://www.w3schools.com/jquery/jquery_traversing.asp

## duyệt cây : lấy children tại index
index bắt đầu từ 0
- lấy một phần tử con, từ vị trí index :  
```js
let x = getJ("#myBox:eq(index)") 
```
trong đó eq có nghĩa là equal
- lấy tất cả các phần tử con, có index lớn hơn a 
```js
let collection = getJ("#myBox:gt(a)")
```
- tương tự như vậy
```js
let collection = getJ("#myBox:lt(a)")
```
## duyệt cây : chọn children theo first last odd even
```js
    let first = getJ("#myBox:first-child");
    let last = getJ("#myBox:last-child");
    let oddColleciton = getJ("#myBox:odd");
    let evenCollection = getJ("#myBox:even");
```
## Copy đối tượng
```js
element.copy()
```
để lấy ra một bản sao đối tượng, vì các thao tác dùng ref chứ không tự sao chép data

## Đếm số lượng children trực tiếp
```html
<body style="background-color: black;">

    <div id="myBox" style="color: beige;">
        <div>
            <div>
                hello cac ban
            </div>
        </div>

        <div>
            cac ban khoe khong
        </div>
    </div>
</body>


<script type="text/babel">

    let collection = getJ("#myBox");
    console.log(collection.children().length); // ra 2

</script>
```
## delay setTimeout
có những lúc ta cần setTimeout cho một phương thức action của element, ta làm như sau
```js
    element.delay(2000).method();
```
tất cả các phương thức của Jnode luôn trả về đối tượng this để call method liên tục, phương thức delay(2000) ở đây nói rằng delay 2s rồi mới chạy action

## get() _ set event bằng code chay
có những lúc ta đã build sẵn một số tính năng event nào đó cho một phần tử DOM được viết bằng Javascript thuần... vậy làm sao ta tích hợp thư viện đó vào cho đối tượng Jquery ? => ta cần convert đối tượng jquery về đối tượng DOM
```js
let domObject = jqueryObject.get();
// lấy ra tham chiếu đến đối tượng DOM được dấu trong Jquery object
// về bản chất, jquery object là một tập hợp mà gồm có chứa dom object
```

# JQUERY UI
Thư viện này hướng bạn sử dụng JQuery để thao tác DOM là chính, vì vậy nếu bạn muốn phát triển UI thì nên dùng đồng bộ với JQuery UI
- https://jqueryui.com

# Lưu Ý
Bạn có thể làm bất cứ gì bạn muốn mà không cần đến React hoặc VueJS, chỉ cần bạn biết JS DOM. Thư viện này như là bản nâng cấp của JS DOM, đằng sau là JQuery. Một số tính năng của SPA của framework như thì không có nhưng đó là thứ yếu, không phải chủ yếu. That's all good luck to you <33
  
# About
Bạn muốn tìm hiểu xem thư viện này cung cấp những hàm nào, được viết như nào thì đọc ở :  
https://minhtuan.social/iloveyoutoke5.js
