<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Hackeo Oficial</title>
    <style>
        body {
            background-color: #1e1e1e;
            font-family: 'Courier New', Courier, monospace;
            color: #00ff00;
            margin: 0;
            padding: 0;
            overflow: hidden;
        }

        h1 {
            text-align: center;
            font-size: 4em;
            animation: glowing 2s ease-in-out infinite alternate;
            margin-top: 50px;
        }

        .banner {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 3em;
            color: #00ff00;
            font-weight: bold;
            text-transform: uppercase;
            animation: bannerGlow 3s infinite alternate;
        }

        @keyframes glowing {
            0% { text-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00, 0 0 15px #00ff00; }
            100% { text-shadow: 0 0 20px #00ff00, 0 0 30px #00ff00, 0 0 40px #00ff00; }
        }

        @keyframes bannerGlow {
            0% { color: #00ff00; }
            100% { color: #ff00ff; }
        }

        .box {
            background-color: rgba(0, 255, 0, 0.1);
            padding: 20px;
            margin: 15px;
            border: 2px solid #00ff00;
            box-shadow: 0 0 15px #00ff00;
            text-align: center;
            font-size: 1.5em;
            border-radius: 10px;
            animation: glowing 1.5s ease-in-out infinite alternate;
            max-width: 80%;
            margin-left: auto;
            margin-right: auto;
        }

        .input-box {
            background-color: rgba(0, 255, 0, 0.2);
            border: none;
            padding: 10px;
            font-size: 1.5em;
            color: #00ff00;
            width: 80%;
            text-align: center;
            margin: 15px 0;
            border-radius: 10px;
        }

        .submit-button {
            background-color: #00ff00;
            color: #1e1e1e;
            padding: 15px 25px;
            border-radius: 10px;
            font-size: 1.5em;
            cursor: pointer;
            animation: glowing 1.5s ease-in-out infinite alternate;
            transition: all 0.3s ease;
        }

        .submit-button:hover {
            background-color: #1e1e1e;
            color: #00ff00;
        }

        .whatsapp-link {
            font-weight: bold;
            color: #ff00ff;
            text-decoration: none;
            font-size: 1.5em;
            padding: 15px;
            background-color: #00ff00;
            border-radius: 10px;
            transition: all 0.3s ease;
            margin-top: 20px;
            display: inline-block;
        }

        .whatsapp-link:hover {
            background-color: #ff00ff;
            color: #1e1e1e;
        }

        .hover-effect:hover {
            background-color: #ff00ff;
            color: #1e1e1e;
        }

        .floating {
            position: absolute;
            animation: float 5s ease-in-out infinite;
        }

        .floating:nth-child(1) { top: 15%; left: 10%; animation-delay: 0s; }
        .floating:nth-child(2) { top: 30%; right: 5%; animation-delay: 1s; }
        .floating:nth-child(3) { bottom: 10%; left: 25%; animation-delay: 2s; }
        .floating:nth-child(4) { top: 50%; right: 15%; animation-delay: 3s; }

        @keyframes float {
            0% { transform: translateY(0); }
            50% { transform: translateY(-30px); }
            100% { transform: translateY(0); }
        }

        .main-content {
            padding-top: 100px;
        }
    </style>
</head>
<body>

    <!-- Banner superior -->
    <div class="banner">
        ⚡ **BerMatModZ** ⚡
    </div>

    <!-- Contenido principal -->
    <div class="main-content">
        <div class="box">
            <p><strong>Ingreso de Código de Acceso</strong></p>
            <input type="text" id="access-code" class="input-box" placeholder="Ingresa el código aquí..." />
            <button class="submit-button" onclick="verifyCode()">Verificar Código</button>
        </div>

        <div class="box">
            <p><strong>Ingresa el número para hackear</strong></p>
            <input type="text" id="phone-number" class="input-box" placeholder="Ej. 900233784" />
            <button class="submit-button hover-effect" onclick="startHack()">Iniciar Hackeo</button>
        </div>

        <div class="box">
            <p><strong>¿No tienes el código de acceso?</strong></p>
            <p>Si no tienes el código de acceso, puedes obtenerlo contactando a mi dueño.</p>
            <a href="https://wa.me/937556459?text=🔥%20Hola%20AnthZz%20Berrocal,%20quiero%20comprar%20tu%20servicio%20de%20hacker%20VIP%20💀%20-%20⚡%20Dame%20acceso%20al%20mundo%20de%20BerMatModZ%20⚡" class="whatsapp-link" target="_blank">Haz clic aquí para obtener el servicio</a>
        </div>
    </div>

    <!-- Elementos flotantes -->
    <div class="floating">🔒</div>
    <div class="floating">💻</div>
    <div class="floating">👾</div>
    <div class="floating">💥</div>

    <script>
        let accessCodeVerified = false;

        function verifyCode() {
            const enteredCode = document.getElementById("access-code").value;
            const correctCode = "BerMat123";
            if (enteredCode === correctCode) {
                accessCodeVerified = true;
                alert("Código verificado con éxito.");
                document.getElementById("phone-number").style.display = "block";
                document.querySelector(".submit-button").textContent = "Iniciar Hackeo";
            } else {
                alert("Código incorrecto. Intenta nuevamente.");
            }
        }

        function startHack() {
            if (accessCodeVerified) {
                const phoneNumber = document.getElementById("phone-number").value;
                if (phoneNumber) {
                    alert(`Hackeando el número ${phoneNumber}...`);
                    // Aquí podrías agregar animaciones o más detalles del hackeo simulado
                } else {
                    alert("Por favor, ingresa un número de teléfono.");
                }
            } else {
                alert("Necesitas ingresar el código de acceso primero.");
            }
        }
    </script>
</body>
</html>
