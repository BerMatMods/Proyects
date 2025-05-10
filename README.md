<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>⚡ BerMatModZ - Hackeo en Proceso</title>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Orbitron:wght@700&family=Rubik+Glitch&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #000000;
            color: #00FF00;
            font-family: 'Rubik Glitch', cursive;
            text-align: center;
            overflow-x: hidden;
            margin: 0;
            animation: glitch-bg 5s infinite alternate;
        }
        @keyframes glitch-bg {
            0% { background-color: #000000; }
            50% { background-color: #111111; }
            100% { background-color: #000000; }
        }
        .banner {
            font-size: 3em;
            color: #00FF00;
            text-shadow: 0 0 20px #00FF00, 0 0 40px #00FF00, 0 0 60px #00FF00;
            margin-top: 20px;
            font-family: 'Orbitron', sans-serif;
            animation: glitch 1.5s infinite alternate;
        }
        @keyframes glitch {
            0% { text-shadow: 0 0 20px #00FF00; }
            50% { text-shadow: -5px 0 20px #FF0000, 5px 0 20px #00FFFF; }
            100% { text-shadow: 0 0 40px #00FF00; }
        }
        .container {
            margin: 30px auto;
            padding: 20px;
            background: rgba(0, 0, 0, 0.9);
            border-radius: 15px;
            width: 90%;
            max-width: 800px;
            box-shadow: 0 0 15px #00FF00;
        }
        .info {
            font-size: 1.2em;
            color: #00FF00;
            margin-bottom: 20px;
            background-color: #111;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 0 10px #00FF00;
            font-family: 'Press Start 2P', monospace;
        }
        .social-links img {
            width: 40px;
            margin: 10px;
            transition: 0.3s;
        }
        .social-links img:hover {
            transform: scale(1.2);
            filter: drop-shadow(0 0 10px #00FF00);
        }
        .input-field, .code-input {
            width: 80%;
            padding: 15px;
            margin-bottom: 20px;
            font-size: 1em;
            border-radius: 10px;
            border: none;
            background-color: #111;
            color: #00FF00;
            text-align: center;
            box-shadow: 0 0 10px #00FF00;
            font-family: 'Rubik Glitch', cursive;
        }
        .hack-button, .access-button {
            padding: 15px 30px;
            background-color: #00FF00;
            color: #000000;
            font-size: 1em;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            text-transform: uppercase;
            box-shadow: 0 0 15px #00FF00;
            margin-bottom: 20px;
            font-family: 'Orbitron', sans-serif;
        }
        .hack-button:hover, .access-button:hover {
            background-color: #FF0000;
            color: #FFFFFF;
            box-shadow: 0 0 15px #FF0000;
        }
    </style>
</head>
<body>
    <div class="banner">⚡ BerMatModZ - Fuerza Anónima de Mentes Avanzadas ⚡</div><div class="container" id="phone-container">
    <div class="info">
        <p>Creado por: Anth'Zz Berrocal</p>
        <p>Alias: BerMatModZ</p>
        <p>Especialidad: Hacker Profesional y Desarrollador</p>
        <p>Ubicación: Andahuaylas, Perú</p>
    </div>
    <div class="social-links">
        <a href="https://wa.me/937556459" target="_blank"><img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp"></a>
        <a href="https://github.com/Anthzberrocal" target="_blank"><img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" alt="GitHub"></a>
        <a href="https://www.facebook.com/profile.php?id=100094458102825" target="_blank"><img src="https://upload.wikimedia.org/wikipedia/commons/5/51/Facebook_f_logo_%282019%29.svg" alt="Facebook"></a>
    </div>
    <h2>Ingrese número para hackear</h2>
    <input type="text" placeholder="Número a hackear o investigar" class="input-field" id="phone-input">
    <button class="hack-button" onclick="showAccessScreen()">Iniciar Hackeo</button>
</div>

<div class="container" id="access-container" style="display:none;">
    <h2>⚠️ Acceso al Sistema VIP de BerMatModZ ⚠️</h2>
    <p>Creado por Anth'Zz Berrocal</p>
    <input type="password" placeholder="Ingrese código de acceso" class="code-input" id="access-code">
    <button class="hack-button" onclick="verifyCode()">Ingresar</button>
    <p id="error-message" style="color:#FF0000;"></p>
</div>

<div class="container" id="chat-container" style="display:none;">
    <h2>Simulando hackeo...</h2>
    <p id="chat-output"></p>
</div>

<script>
    function showAccessScreen() {
        const phone = document.getElementById('phone-input').value;
        if (phone) {
            document.getElementById('phone-container').style.display = 'none';
            document.getElementById('access-container').style.display = 'block';
        }
    }

    function verifyCode() {
        const code = document.getElementById('access-code').value;
        if (code === 'BerMat123') {
            document.getElementById('access-container').style.display = 'none';
            document.getElementById('chat-container').style.display = 'block';
            const messages = [
                "Conectando a WhatsApp...",
                "Acceso concedido al sistema VIP de BerMatModZ...",
                "Escaneando mensajes...",
                "IP del objetivo: 192.168.1.45",
                "Ubicación aproximada: Andahuaylas, Perú",
                "Nombre del dispositivo: AnthZz-iPhone",
                "Chats recientes:",
                "Bro, cuándo sale tu nuevo bot de IA? 🤖🔥",
                "Hermano, tu BerMat-Bot MD está rompiendo el código en Termux! 💥😎",
                "Anth'Zz, me ayudas con un script para hackear redes WiFi? 😏🔓"
            ];
            document.getElementById('chat-output').innerHTML = messages.join('<br>');
        } else {
            document.getElementById('error-message').innerText = "⚠️ Código incorrecto. Inténtalo de nuevo.";
        }
    }
</script>

</body>
</html>
