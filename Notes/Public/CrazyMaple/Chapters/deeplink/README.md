# deeplink guide

## go to visual book
<body>
Book Id: <input type="text" id="bookid" value="10064">
<p>Click the button to open visual book</p>
<button type="button" onclick="myFunction()">Open Visual Book</button>
<script>
function myFunction() {
  let deeplinkurl = "chapter://?type=1&storytype=1&bookid=" + document.getElementById("bookid").value + "&bottomid=0"
  console.log(deeplinkurl)
  window.open(deeplinkurl)
}
</script>
</body>
<p><br></p>

## go to avator page
<span style="font-size:1em">[个人信息界面](chapter://?type=3&storytype=0&bookid=0&bottomid=4)</span>
<p></p>

## go to book detail

<body>
Book Id: <input type="text" id="bookid" value="10064">
<p>Click the button to open visual book detail</p>
<button type="button" onclick="myFunction()">Open Book Detail</button>
<script>
function myFunction() {
  let deeplinkurl = "chapter://?type=4&storytype=1&bookid=" + document.getElementById("bookid").value + "&bottomid=0"
  console.log(deeplinkurl)
  window.open(deeplinkurl)
}
</script>
</body>
<p><br></p>

## go to sms 
[短信大厅](chapter://?type=2&storytype=2&bookid=10001&bottomid=0)