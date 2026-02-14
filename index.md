<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>San Valentín 💘</title>

<style>
body {
    margin: 0;
    padding: 40px 20px;
    background: #f8c8dc;
    font-family: 'Arial', sans-serif;
    text-align: center;
    overflow-y: auto;
}

.container {
    max-width: 500px;
    margin: auto;
}

h1 {
    color: #000;
    font-size: 26px;
}

p {
    color: #000;
}

.photo {
    width: 100%;
    max-width: 250px;
    border-radius: 20px;
    margin: 20px 0;
}

.buttons {
    display: flex;
    gap: 15px;
    margin-top: 20px;
}

button {
    flex: 1;
    padding: 15px;
    font-size: 18px;
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
    background: #ffffff;
    color: black;
}

.hidden {
    display: none;
}

#result {
    margin-top: 25px;
    font-weight: bold;
    color: black;
}

.whatsapp-btn {
    display: inline-block;
    margin-top: 15px;
    padding: 12px 20px;
    background: #25D366;
    color: white;
    text-decoration: none;
    border-radius: 10px;
}

/* 🎵 Player */
.player {
    margin-top: 30px;
}

#progress {
    width: 100%;
}

/* 🎉 Confeti */
.confetti {
    position: fixed;
    width: 10px;
    height: 10px;
    top: -10px;
    animation: fall linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
    }
}
</style>
</head>

<body>

<div class="container">

<h1>¿Quieres ser mi San Valentín? U3U 💕</h1>

<p>Tendrás un día lleno de tu música favorita y rica comida chiqui 🥰</p>

<img src="foto.jpg" alt="Nuestra foto" class="photo">

<div class="buttons">
    <button id="yes">Sí 🥰</button>
    <button id="no">No 😅</button>
</div>

<div id="result"></div>

<!-- 🎵 Música -->
<div class="player">
    <audio id="music" src="musica.mp3"></audio>
    <button id="playPause">▶️</button>
    <input type="range" id="progress" value="0" min="0" max="100">
</div>

</div>

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
        <p style="margin-top:20px;">
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
        <p>
            Buena elección jiji 😌💘<br>
            Envía confirmación
        </p>
        <a class="whatsapp-btn" 
           href="https://wa.me/51988096303?text=Confirmo%20mi%20cita%20de%20San%20Valent%C3%ADn%20uwu" 
           target="_blank">
           Enviar confirmación 💌
        </a>
    `;
});

/* 🎵 PLAYER */
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

/* 🎉 Confeti */
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
</script>

</body>
</html>
