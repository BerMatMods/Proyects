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
        .info, .social, .chat {
            margin: 20px 0;
            padding: 15px;
            border-radius: 10px;
            background: #111;
            box-shadow: 0 0 10px #00FF00;
        }
        .chat p {
            color: #00FF00;
            text-align: left;
            margin-bottom: 15px;
            background: #111;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 0 5px #00FF00;
            font-family: 'Press Start 2P', monospace;
        }
        a {
            color: #00FF00;
            text-decoration: none;
            font-size: 1.2em;
            font-family: 'Rubik Glitch', cursive;
        }
        a:hover {
            color: #FF0000;
        }
        .input-field {
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
        .hack-button {
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
        .hack-button:hover {
            background-color: #FF0000;
            color: #FFFFFF;
            box-shadow: 0 0 15px #FF0000;
        }
    </style>
</head>
<body>
    <div class="banner">⚡ BerMatModZ - Fuerza Anónima de Mentes Avanzadas ⚡</div><div class="container">
    <div class="info">
        <h2>Información Personal</h2>
        <p>Nombre: Anth'Zz Berrocal</p>
        <p>Alias: BerMatModZ - Hacker Profesional</p>
        <p>Ubicación: Andahuaylas, Perú</p>
        <p>Especialidades: Hacking ético, automatización, inteligencia artificial, tecnología avanzada</p>
    </div>

    <div class="social">
        <h2>Redes Sociales</h2>
        <p><a href="https://www.facebook.com/AnthZzBerrocal">Facebook 👤</a></p>
        <p><a href="https://www.instagram.com/AnthZzBerrocal">Instagram 📸</a></p>
        <p><a href="https://www.github.com/AnthZzBerrocal">GitHub 💻</a></p>
        <p><a href="https://www.tiktok.com/@AnthZzBerrocal">TikTok 🎥</a></p>
        <p><a href="https://wa.me/51937556459">WhatsApp 💬</a></p>
    </div>

    <div class="chat">
        <h2>Hackeando... Espere un momento...</h2>
        <input type="text" placeholder="Ingrese número para investigar" class="input-field" id="phone-input">
        <button class="hack-button" onclick="hackNow()">Iniciar Hackeo</button>
        <p id="chat-output"></p>
    </div>
</div>

<script>
    function hackNow() {
        const phone = document.getElementById('phone-input').value;
        if (phone) {
            const messages = [
                "Conectando a WhatsApp...",
                `Número ingresado: +51 ${phone}`,
                "Escaneando mensajes...",
                "IP del objetivo: 192.168.1.45",
                "Ubicación aproximada: Andahuaylas, Perú",
                "Nombre del dispositivo: AnthZz-iPhone",
                "Chats recientes:",
                "Bro, cuándo sale tu nuevo bot de IA? 🤖🔥",
                "Hermano, tu BerMat-Bot MD está rompiendo el código en Termux! 💥😎",
                "Anth'Zz, me ayudas con un script para hackear redes WiFi? 😏🔓",
                "Maestro, eres una leyenda en ciberseguridad 💯👑"
            ];
            document.getElementById('chat-output').innerHTML = messages.join('<br>');
        }
    }
</script>

</body>
</html>
