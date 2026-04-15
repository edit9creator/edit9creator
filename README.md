<!DOCTYPE html>
<html>
<head>
<title>SnapEdit AI Pro</title>

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
  margin:0;
  font-family:sans-serif;
  background:#0f0f0f;
  color:white;
}

.topbar{
  background:#1c1c1c;
  padding:12px;
  text-align:center;
  font-size:18px;
}

.workspace{
  padding:10px;
  text-align:center;
}

canvas, img{
  max-width:100%;
  margin-top:10px;
  border-radius:10px;
}

.toolbar{
  position:fixed;
  bottom:0;
  width:100%;
  background:#1c1c1c;
  display:flex;
  justify-content:space-around;
  padding:10px;
}

button{
  background:#333;
  color:white;
  border:none;
  padding:10px;
  border-radius:8px;
}
</style>
</head>

<body>

<div class="topbar">📸 SnapEdit AI Pro (Beta)</div>

<div class="workspace">

<input type="file" id="file">

<img id="img">

</div>

<div class="toolbar">
<button onclick="bright()">Bright</button>
<button onclick="gray()">BW</button>
<button onclick="reset()">Reset</button>
</div>

<script>
let img = document.getElementById("img");

document.getElementById("file").onchange = function(e){
  let reader = new FileReader();
  reader.onload = function(){
    img.src = reader.result;
  }
  reader.readAsDataURL(e.target.files[0]);
}

function bright(){
  img.style.filter = "brightness(150%)";
}

function gray(){
  img.style.filter = "grayscale(100%)";
}

function reset(){
  img.style.filter = "none";
}
</script>

</body>
</html>
