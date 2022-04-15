## deeplink guide

### go to visual book
<html>
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
</html>
