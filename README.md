<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Лебедин Виталий</title>
<style>
/* сюда весь CSS из lebedin1st.html */
body {
    font-family: Arial, Helvetica, sans-serif;
    background: #f9f9f9;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
    padding: 20px;
    overflow: hidden;
    position: relative;
}
/* остальной CSS ... */
</style>
</head>
<body>

<canvas id="matrixCanvas"></canvas>

<div class="card">
    <h1>Лебедин Виталий</h1>

    <div class="social-buttons">
        <a class="button telegram" href="https://t.me/svosint" target="_blank">
            📲 Telegram
        </a>
        <a class="button whatsapp" href="https://wa.me/77711143045" target="_blank">
            💬 WhatsApp
        </a>
    </div>

    <div class="buttons">
        <a class="button" href="teacher.html">👩‍🏫 Новая страница</a>
        <a class="button" href="ttt.html">❌⭕ Tic-Tac-Toe</a>
        <a class="button" href="mines.html">💣 Мины</a>
        <a class="button" href="boa.html">🌟 Вдохновитель</a>
    </div>

    <footer>
        Сайт сделан с помощью ChatGPT
    </footer>
</div>

<script>
// JS код с падающими цифрами
const canvas = document.getElementById('matrixCanvas');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const binary = "01";
const fontSize = 18;
const columns = Math.floor(canvas.width / fontSize);
const drops = [];

for(let i = 0; i < columns; i++) drops[i] = Math.random() * canvas.height;

function draw() {
    ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    ctx.fillStyle = "#00FF00";
    ctx.font = fontSize + "px monospace";

    for(let i = 0; i < drops.length; i++) {
        const text = binary.charAt(Math.floor(Math.random() * binary.length));
        const x = i * fontSize;
        const y = drops[i];
        
        if(x < window.innerWidth * 0.1 || x > window.innerWidth * 0.9 || y < canvas.height*0.1 || y > canvas.height*0.9){
            ctx.globalAlpha = 0.7 + Math.random()*0.3;
        } else ctx.globalAlpha = 0.2;

        ctx.fillText(text, x, y);
        drops[i] += fontSize;
        if(drops[i] > canvas.height) drops[i] = -fontSize;
    }

    requestAnimationFrame(draw);
}

draw();
window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
});
</script>

</body>
</html>
