<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Happy Birthday</title>
<style>
body {
  margin: 0;
  overflow: hidden;
  background: black;
  font-family: Arial, sans-serif;
}

/* MATRIX */
canvas {
  position: absolute;
  top: 0;
  left: 0;
}

/* TEXT */
h1 {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: pink;
  font-size: 50px;
}

/* BUTTON */
button {
  position: absolute;
  top: 60%;
  left: 50%;
  transform: translateX(-50%);
  padding: 15px 30px;
  font-size: 18px;
  background: pink;
  border: none;
  border-radius: 10px;
  cursor: pointer;
}

/* CARD */
.card {
  display: none;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  color: black;
  padding: 20px;
  border-radius: 15px;
  text-align: center;
  width: 300px;
}

.card img {
  width: 100%;
  border-radius: 10px;
}
</style>
</head>
<body>

<canvas id="matrix"></canvas>

<h1>HAPPY BIRTHDAY</h1>

<button onclick="openCard()">Открыть открытку 🎁</button>

<div class="card" id="card">
  <h2>С Днём Рождения 💖</h2>
  <img src="https://via.placeholder.com/300" alt="photo">
  <p>Желаю счастья, успеха и всего самого лучшего ✨</p>
</div>

<script>
const canvas = document.getElementById("matrix");
const ctx = canvas.getContext("2d");

canvas.height = window.innerHeight;
canvas.width = window.innerWidth;

const letters = "01ABCDEFGHIJKLMNOPQRSTUVWXYZ";
const fontSize = 14;
const columns = canvas.width / fontSize;

const drops = [];
for (let i = 0; i < columns; i++) drops[i] = 1;

function draw() {
  ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "#ff4da6";
  ctx.font = fontSize + "px monospace";

  for (let i = 0; i < drops.length; i++) {
    const text = letters.charAt(Math.floor(Math.random() * letters.length));
    ctx.fillText(text, i * fontSize, drops[i] * fontSize);

    if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
      drops[i] = 0;
    }
    drops[i]++;
  }
}

setInterval(draw, 33);

/* OPEN CARD */
function openCard() {
  document.getElementById("card").style.display = "block";
}
</script>

</body>
</html>
