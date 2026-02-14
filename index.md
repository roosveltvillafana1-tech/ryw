<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>¿Quieres ser mi San Valentín? 💘</title>

<style>
* { box-sizing: border-box; }

body {
    margin: 0;
    min-height: 100vh;   /* antes era height */
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f8c8dc;
    font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    overflow-y: auto;    
    padding: 20px;
    transition: background 0.5s ease;
}

.card {
    background: white;
    padding: 35px 25px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 15px 40px rgba(0,0,0,0.15);
    width: 100%;
    max-width: 420px;
    z-index: 2;
    animation: fadeIn 1s ease;
}

/* ✨ Efecto brillo romántico */
.photo {
    width: 100%;
    max-width: 250px;
    border-radius: 20px;
    margin: 20px 0;
    animation: glow 2s infinite alternate;
}

@keyframes glow {
    from {
        box-shadow: 0 0 10px #ff4d88;
    }
    to {
        box-shadow: 0 0 30px #ff4d88, 0 0 60px #ff99cc;
    }
}

/* ⏳ Contador */
.countdown {
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
    color: #000;
}

h1 {
    color: #d63384;
    font-size: 22px;
}

p {
    color: #555;
    font-size: 15px;
}

.buttons {
    display: flex;
    gap: 15px;
    margin-top: 20px;
}

button {
    flex: 1;
    padding: 15px;
    font-size: 16px;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    transition: all 0.3s ease;
}

#yes {
    background: #ff4d88;
    color: black;
}

#no {
    background: #999;
    color: white;
}

.whatsapp-btn {
    margin-top: 15px;
    background: #25D366;
    color: white;
    padding: 14px;
    border-radius: 12px;
    display: inline-block;
    text-decoration: none;
    font-weight: bold;
    width: 100%;
}

.hidden { display: none; }

/* PLAYER */
.player {
    margin-top: 15px;
    background: #ffe6f0;
    padding: 15px;
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.song-title {
    font-size: 14px;
    color: #d63384;
    font-weight: bold;
}

#playPause {
    background: #ff4d88;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 10px;
    font-size: 18px;
}

#progress {
    width: 100%;
}

/* Confeti */
.confetti {
    position: absolute;
    width: 8px;
    height: 8px;
    top: 0;
    animation: fall 3s linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
    }
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}
</style>
</head>

<body>

<div class="card">
    <img src="IMG_6512.jpeg" class="photo">

    <h1>¿Quieres ser mi San Valentín, Croqueta? U3U</h1>
    <div class="countdown" id="countdown"></div>
    <p>Tendrás un día llena de tu música favorita y rica comida chiqui 🥰</p>

    <div class="player">
        <div class="song-title">🎶 I.L.Y. - The Rose</div>
        <button id="playPause">▶️</button>
        <input type="range" id="progress" value="0" min="0" max="100">
    </div>

    <div class="buttons">
        <button id="yes">Sí 🥰</button>
        <button id="no">No 🧐💀</button>
    </div>

    <div id="result"></div>
</div>

<audio id="music">
    <source src="music.mp3" type="audio/mpeg">
</audio>

<script>
const yesBtn = document.getElementById('yes');
const noBtn = document.getElementById('no');
const result = document.getElementById('result');
const music = document.getElementById('music');
const playPauseBtn = document.getElementById("playPause");
const progress = document.getElementById("progress");

let scale = 1;
let cryCount = 1;

/* BOTÓN NO */
noBtn.addEventListener('click', () => {

    scale += 0.4;
    yesBtn.style.flex = scale;

    let cryingFaces = "😭".repeat(cryCount);
    result.innerHTML = `
        <p style="margin-top:20px; font-weight:bold; color:black;">
            Oye 😡 ${cryingFaces}
        </p>
    `;

    cryCount++;

    if (scale >= 5) {
        noBtn.classList.add('hidden');
        yesBtn.style.width = "100%";
    }
});

/* BOTÓN SÍ */
yesBtn.addEventListener('click', () => {

    document.body.style.background = "#ff4d88";

    if (navigator.vibrate) {
        navigator.vibrate([200, 100, 200]);
    }

    launchConfetti();

    result.innerHTML = `
        <p style="margin-top:20px; font-weight:bold; color:black;">
            Buena elección jiji 😌💘<br>
            No faltes uwu
        </p>
        <a class="whatsapp-btn" 
           href="https://wa.me/51988096303?text=Confirmo%20la%20cita%20de%20San%20Valent%C3%ADn%20uwu" 
           target="_blank">
           Enviar confirmación por WhatsApp 💌
        </a>
    `;
});

/* PLAYER */
playPauseBtn.addEventListener("click", () => {
    if (music.paused) {
        music.play();
        playPauseBtn.textContent = "⏸️";
    } else {
        music.pause();
        playPauseBtn.textContent = "▶️";
    }
});

music.addEventListener("timeupdate", () => {
    const percent = (music.currentTime / music.duration) * 100;
    progress.value = percent;
});

progress.addEventListener("input", () => {
    const time = (progress.value / 100) * music.duration;
    music.currentTime = time;
});

/* Confeti */
function launchConfetti() {
    for (let i = 0; i < 80; i++) {
        const confetti = document.createElement("div");
        confetti.classList.add("confetti");
        confetti.style.left = Math.random() * 100 + "vw";
        confetti.style.background =
            ["#ff4d88", "#ff99cc", "#ffd6e8", "#ffffff"][Math.floor(Math.random()*4)];
        confetti.style.animationDuration = (Math.random() * 2 + 2) + "s";
        document.body.appendChild(confetti);

        setTimeout(() => {
            confetti.remove();
        }, 3000);
    }
}
    /* ⏳ CONTADOR HASTA MAÑANA 3:00 PM */
function updateCountdown() {
    const now = new Date();

    const target = new Date();
    target.setDate(now.getDate() + 1);
    target.setHours(15, 0, 0, 0);

    const diff = target - now;

    if (diff <= 0) {
        document.getElementById("countdown").innerHTML =
            "Es hoyyy 😳💘 ¡Nos vemos a las 3:00!";
        return;
    }

    const hours = Math.floor(diff / (1000 * 60 * 60));
    const minutes = Math.floor((diff / (1000 * 60)) % 60);
    const seconds = Math.floor((diff / 1000) % 60);

    document.getElementById("countdown").innerHTML =
        `Tienes ${hours}h ${minutes}m ${seconds}s para confirmar 🤭`;
}

setInterval(updateCountdown, 1000);
updateCountdown();
</script>

</body>
</html>
