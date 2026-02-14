<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>¿Quieres salir conmigo? 💘</title>

<style>
    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: #f8c8dc; /* rosado palo */
        font-family: -apple-system, BlinkMacSystemFont, sans-serif;
        overflow: hidden;
    }

    .card {
        background: white;
        padding: 40px 30px;
        border-radius: 20px;
        text-align: center;
        box-shadow: 0 15px 40px rgba(0,0,0,0.15);
        width: 90%;
        max-width: 400px;
        position: relative;
        z-index: 2;
        animation: fadeIn 1s ease;
    }

    h1 {
        margin-bottom: 10px;
        color: #d63384;
    }

    p {
        margin-bottom: 30px;
        color: #555;
    }

    .buttons {
        display: flex;
        gap: 15px;
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
        color: white;
    }

    #no {
        background: #999;
        color: white;
    }

    .full {
        width: 100% !important;
    }

    .hidden {
        display: none;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* corazones flotando */
    .heart {
        position: absolute;
        font-size: 20px;
        animation: float 6s infinite linear;
        opacity: 0.6;
    }

    @keyframes float {
        from {
            transform: translateY(100vh) scale(1);
        }
        to {
            transform: translateY(-10vh) scale(1.5);
        }
    }
</style>
</head>

<body>

<div class="card">
    <h1>¿Quieres salir conmigo? 💖</h1>
    <p>Prometo buena conversación, risas y algo dulce después 🍫✨</p>

    <div class="buttons">
        <button id="yes">Sí 💕</button>
        <button id="no">No 🙈</button>
    </div>

    <p id="result" style="margin-top:20px; font-weight:bold; color:#d63384;"></p>
</div>

<script>
    const yesBtn = document.getElementById('yes');
    const noBtn = document.getElementById('no');
    const result = document.getElementById('result');

    let scale = 1;

    noBtn.addEventListener('click', () => {
        scale += 0.4;
        yesBtn.style.flex = scale;

        if (scale >= 5) {
            noBtn.classList.add('hidden');
            yesBtn.classList.add('full');
        }
    });

    yesBtn.addEventListener('click', () => {
        result.innerText = "Sabía que dirías que sí 😍🌹 Te escribo para coordinar 💌";
    });

    // Crear corazones flotando
    function createHeart() {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerText = "💗";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = (Math.random() * 3 + 3) + "s";
        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 6000);
    }

    setInterval(createHeart, 800);
</script>

</body>
</html>
