
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>¿Quieres ser mi San Valentín, Croqueta? 💘</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: #f8c8dc; /* rosado palo */
        font-family: -apple-system, BlinkMacSystemFont, sans-serif;
        overflow: hidden;
        padding: 20px;
    }

    .card {
        background: white;
        padding: 40px 25px;
        border-radius: 20px;
        text-align: center;
        box-shadow: 0 15px 40px rgba(0,0,0,0.15);
        width: 100%;
        max-width: 420px;
        position: relative;
        z-index: 2;
        animation: fadeIn 1s ease;
    }

    h1 {
        margin-bottom: 15px;
        color: #d63384;
        font-size: 22px;
    }

    p {
        margin-bottom: 30px;
        color: #555;
        font-size: 15px;
    }

    .buttons {
        display: flex;
        gap: 15px;
        width: 100%;
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

    .hidden {
        display: none;
    }

    .whatsapp-btn {
        margin-top: 20px;
        background: #25D366;
        color: white;
        padding: 14px;
        border-radius: 12px;
        display: inline-block;
        text-decoration: none;
        font-weight: bold;
        width: 100%;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(20px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* Corazones */
    .heart {
        position: absolute;
        font-size: 18px;
        animation: float 6s infinite linear;
        opacity: 0.5;
    }

    @keyframes float {
        from { transform: translateY(100vh); }
        to { transform: translateY(-10vh); }
    }

    @media (max-width: 400px) {
        h1 { font-size: 20px; }
        p { font-size: 14px; }
    }
</style>
</head>

<body>

<div class="card">
    <h1>¿Quieres ser mi San Valentín? U3U </h1>
    <p>Tendrás un día llena de tu música favorita jeje y rica comida chiqui 🥵</p>

    <div class="buttons">
        <button id="yes">Sí 🥰</button>
        <button id="no">No 💀</button>
    </div>

    <div id="result"></div>
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
            yesBtn.style.width = "100%";
        }
    });

    yesBtn.addEventListener('click', () => {
        result.innerHTML = `
            <p style="margin-top:20px; font-weight:bold; color:#d63384;">
                Buena elección jiji, envía confirmación mejeje
            </p>
            <a class="whatsapp-btn" 
               href="https://wa.me/51988096303?text=Confirmo%20la%20salida%20de%20San%20Valent%C3%ADn%20uwu" 
               target="_blank">
               Enviar confirmación por WhatsApp 💌
            </a>
        `;
    });

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
