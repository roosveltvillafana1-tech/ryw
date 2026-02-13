<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¿Aceptas?</title>

    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-family: -apple-system, BlinkMacSystemFont, sans-serif;
            background: #f5f5f5;
        }

        h1 {
            margin-bottom: 30px;
        }

        .buttons {
            display: flex;
            gap: 15px;
            width: 90%;
            max-width: 400px;
        }

        button {
            flex: 1;
            padding: 16px;
            font-size: 18px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        #yes {
            background-color: #4CAF50;
            color: white;
        }

        #no {
            background-color: #f44336;
            color: white;
        }
    </style>
</head>
<body>

    <h1>¿Aceptas?</h1>

    <div class="buttons">
        <button id="yes">Sí</button>
        <button id="no">No</button>
    </div>

    <script>
        const yesBtn = document.getElementById('yes');
        const noBtn = document.getElementById('no');

        let yesScale = 1;

        noBtn.addEventListener('click', () => {
            yesScale += 0.3;
            yesBtn.style.flex = yesScale;

            // Cuando el botón Sí ocupa casi todo el ancho
            if (yesScale >= 5) {
                noBtn.style.display = 'none';
                yesBtn.style.flex = '1';
                yesBtn.style.width = '100%';
            }
        });
    </script>

</body>
</html>
