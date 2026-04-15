<!DOCTYPE html>
<html>
<head>
<title>SnapEdit Pro</title>

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body{
  margin:0;
  background:#121212;
  color:white;
  font-family:sans-serif;
}

.header{
  padding:15px;
  font-size:20px;
  text-align:center;
  background:#1f1f1f;
}

.container{
  padding:15px;
}

img{
  width:100%;
  border-radius:10px;
  margin-top:10px;
}

.control{
  margin-top:15px;
}

input[type="range"]{
  width:100%;
}

button{
  width:100%;
  padding:12px;
  margin-top:10px;
  border:none;
  border-radius:10px;
  background:#4CAF50;
  color:white;
}
</style>
</head>

<body>

<div class="header">📸 SnapEdit Pro</div>

<div class="container">

<input type="file" id="upload">

<img id="img">

<div class="control">
<p>Brightness</p>
<input type="range" id="brightness" min="0" max="200" value="100">
</div>

<div class="control">
<p>Contrast</p>
<input type="range" id="contrast" min="0" max="200" value="100">
</div>

<div class="control">
<p>Blur</p>
<input type="range" id="blur" min="0" max="10" value="0">
</div>

<button onclick="download()">⬇️ Download</button>

</div>

<script>
let img = document.getElementById("img");

let brightness = document.getElementById("brightness");
let contrast = document.getElementById("contrast");
let blur = document.getElementById("blur");

document.getElementById("upload").onchange = function(e){
  let reader = new FileReader();
  reader.onload = function(){
    img.src = reader.result;
  }
  reader.readAsDataURL(e.target.files[0]);
}

function apply(){
  img.style.filter =
  `brightness(${brightness.value}%)
   contrast(${contrast.value}%)
   blur(${blur.value}px)`;
}

brightness.oninput = apply;
contrast.oninput = apply;
blur.oninput = apply;

function download(){
  let link = document.createElement("a");
  link.download = "edited.png";
  link.href = img.src;
  link.click();
}
</script>

</body>
</html>
