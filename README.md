<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>بطاقة عيد</title>
<style>
  body {
    text-align: center;
    font-family: 'Arial', sans-serif;
    background-color: #fdf6e3;
    direction: rtl;
  }
  input {
    font-size: 18px;
    padding: 10px;
    width: 300px;
    margin-top: 20px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }
  button {
    font-size: 18px;
    padding: 10px 20px;
    margin-left: 10px;
    border-radius: 5px;
    border: none;
    background-color: #ff8c00;
    color: white;
    cursor: pointer;
  }
  canvas {
    margin-top: 30px;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  }
</style>
</head>
<body>

<h2>اكتب اسمك للحصول على بطاقة العيد</h2>

<input type="text" id="name" placeholder="اكتب اسمك هنا">
<button onclick="generate()">إنشاء البطاقة</button>

<br><br>
<canvas id="card" width="1080" height="1080"></canvas>

<br><br>
<button onclick="download()">تحميل البطاقة</button>

<script>
function generate() {
  var name = document.getElementById("name").value || "عيدكم مبارك";
  var canvas = document.getElementById("card");
  var ctx = canvas.getContext("2d");

  var img = new Image();
  img.src = "eid-card.png"; // ضع هنا اسم صورة البطاقة
  img.onload = function() {
    // مسح الكانفس قبل الرسم
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    // رسم الصورة
    ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
    // كتابة الاسم
    ctx.font = "70px Cairo, Arial, sans-serif";
    ctx.fillStyle = "#ffffff";
    ctx.textAlign = "center";
    ctx.fillText(name, canvas.width / 2, canvas.height / 2);
  }
}

function download() {
  var link = document.createElement('a');
  link.download = 'eid-card.png';
  link.href = document.getElementById('card').toDataURL();
  link.click();
}
</script>

</body>
</html>
<img width="468" height="649" alt="image" src="https://github.com/user-attachments/assets/33094300-c49d-488b-9dd2-cc5b6a67a948" />
