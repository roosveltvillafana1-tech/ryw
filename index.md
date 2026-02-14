
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>¿Quieres ser mi San Valentín? 💘</title>

<style>
* { box-sizing: border-box; }

body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f8c8dc;
    font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    overflow: hidden;
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

.photo {
    width: 110px;
    height: 110px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 15px;
    border: 4px solid #ff4d88;
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
    color: white;
}

#no {
    background: #999;
    color: white;
}

.music-btn {
    margin-top: 15px;
    background: #6c5ce7;
    color: white;
    width: 100%;
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

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

/* Confeti */
.confetti {
    position: absolute;
    width: 8px;
    height: 8px;
    background: red;
    top: 0;
    animation: fall 3s linear forwards;
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

<div class="card">
    <img src="bc11ea3c-b387-4662-a2b9-58ebbabbb327.jpeg" class="photo">

    <h1>¿Quieres ser mi San Valentín, Croqueta? U3U </h1>
    <p>Tendrás un día llena de tu música favorita y rica comida chiqui 🥰</p>

    <button class="music-btn" onclick="toggleMusic()">🎵 Activar música</button>

    <div class="buttons">
        <button id="yes">Sí 🥰</button>
        <button id="no">No 🧐💀</button>
    </div>

    <div id="result"></div>
</div>

<audio id="music" loop>
    <source src="musica.mp3" type="audio/mpeg">
</audio>

<script>
const yesBtn = document.getElementById('yes');
const noBtn = document.getElementById('no');
const result = document.getElementById('result');
const music = document.getElementById('music');

let scale = 1;
let musicPlaying = false;

noBtn.addEventListener('click', () => {
    scale += 0.4;
    yesBtn.style.flex = scale;

    if (scale >= 5) {
        noBtn.classList.add('hidden');
        yesBtn.style.width = "100%";
    }
});

yesBtn.addEventListener('click', () => {

    document.body.style.background = "#ff4d88";

    if (navigator.vibrate) {
        navigator.vibrate([200, 100, 200]);
    }

    launchConfetti();

    result.innerHTML = `
        <p style="margin-top:20px; font-weight:bold; color:white;">
            Buena elección jiji 😌💘<br>
            No faltes uwu
        </p>
        <a class="whatsapp-btn" 
           href="https://wa.me/51988096303?text=Confirmo%20mi%20cita%20de%20San%20Valent%C3%ADn%20uwu" 
           target="_blank">
           Enviar confirmación por WhatsApp 💌
        </a>
    `;
});

function toggleMusic() {
    if (!musicPlaying) {
        music.play();
        musicPlaying = true;
    } else {
        music.pause();
        musicPlaying = false;
    }
}

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
