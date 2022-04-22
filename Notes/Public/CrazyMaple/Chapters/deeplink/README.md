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
<p><br></p>
</body>


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

## iOS open link from Safari
<body>
Appsflyer OneLink: <input type="text" id="af_ios_link" value="https://chaptersapp.onelink.me/Fopm?pid=Share_link&af_dp=chapter%3A%2F%2F&af_force_deeplink=true&deep_link_value=chapter%3A%2F%2F%3Ftype%3D4%26storytype%3D1%26bookid%3D52827%26bottomid%3D2%26fbclid%3DIwAR1s_ywJHQRfkHoH43QoMPnsQq75sFgwhjYz8Vu-9wfXRJXACdh5BdMaxcc" height="100" width="1080">
<p>launch chapters and open visual book detail</p>
<button type="button" onclick="myFunction()">LaunchChapters</button>
<script>
function myFunction() {
  let deeplinkurl =document.getElementById("af_ios_link").value
  console.log(deeplinkurl)
  window.open(deeplinkurl)
}
</script>
</body>
<p><br></p>

<p ><a href="https://chaptersapp.onelink.me/Fopm?pid=Share_link&af_dp=chapter%3A%2F%2F&af_force_deeplink=true&deep_link_value=chapter%3A%2F%2F%3Ftype%3D4%26storytype%3D1%26bookid%3D52827%26bottomid%3D2%26fbclid%3DIwAR1s_ywJHQRfkHoH43QoMPnsQq75sFgwhjYz8Vu-9wfXRJXACdh5BdMaxcc">Launch:with af_force_deeplink=true</a></p>

<p ><a href="https://chaptersapp.onelink.me/Fopm?pid=Share_link&af_dp=chapter%3A%2F%2F&deep_link_value=chapter%3A%2F%2F%3Ftype%3D4%26storytype%3D1%26bookid%3D52827%26bottomid%3D2%26fbclid%3DIwAR1s_ywJHQRfkHoH43QoMPnsQq75sFgwhjYz8Vu-9wfXRJXACdh5BdMaxcc">Launch:with af_dp=chapters://</a></p>


<p ><a href="https://chaptersapp.onelink.me/Fopm?pid=Share_link&deep_link_value=chapter%3A%2F%2F%3Ftype%3D4%26storytype%3D1%26bookid%3D52827%26bottomid%3D2%26fbclid%3DIwAR1s_ywJHQRfkHoH43QoMPnsQq75sFgwhjYz8Vu-9wfXRJXACdh5BdMaxcc">Launch:with no af_dp ,no af_force_deeplink</a></p>


<p ><a href="https://chaptersapp.onelink.me/Fopm?pid=Share_link&deep_link_value=chapter%3A%2F%2F%3Ftype%3D4%26storytype%3D1%26bookid%3D52827%26bottomid%3D2%26fbclid%3DIwAR1s_ywJHQRfkHoH43QoMPnsQq75sFgwhjYz8Vu-9wfXRJXACdh5BdMaxcc&af_ios_url=chapter%3A%2F%2F&">Launch:af_ios_url</a></p>
