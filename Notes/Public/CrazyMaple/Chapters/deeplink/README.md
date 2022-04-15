## deeplink guide

### go to visual book

Book Id: <input type="text" id="bookid" value="10064">
<p>Click the button to change the default value of the text field.</p>
<button type="button" onclick="myFunction()">Try it</button>
<script>
function myFunction() {
  let deeplinkurl = "chapter://?type=1&storytype=1&bookid=" + document.getElementById("bookid") + "&bottomid=0"
  console.log(deeplinkurl)
  window.open(deeplinkurl,"_system")
}
</script>
</body>
</html>
