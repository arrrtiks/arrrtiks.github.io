<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>Лебедин Виталий</title>
<style>
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

.card {
    position: relative;
    background: white;
    padding: 30px 40px;
    border-radius: 20px;
    box-shadow: 0 12px 30px rgba(0,0,0,0.12);
    max-width: 500px;
    width: 100%;
    text-align: center;
    z-index: 2;
}

.card h1 {
    margin-bottom: 25px;
    font-size: 28px;
    color: #222;
}

.social-buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
}

.card a.button {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    text-decoration: none;
    padding: 10px 15px;
    border-radius: 12px;
    font-size: 14px;
    color: white;
    background: black;
    transition: transform 0.2s, box-shadow 0.2s;
}

.card a.button:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 15px rgba(0,0,0,0.12);
}

.card a.telegram { background: #229ED9; }
.card a.whatsapp { background: #25D366; }

.card .buttons {
    display: flex;
    flex-direction: column;
    gap: 15px;
    margin-bottom: 20px;
}

footer {
    font-size: 12px;
    color: #888;
}

#matrixCanvas {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 0;
}
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
