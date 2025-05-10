<!DOCTYPE html><html lang="es">
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
        }/* Cuadro superior con el alias */
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
        padding: 15px;
        background-color: rgba(0, 255, 0, 0.3);
        border-radius: 10px;
        border: 3px solid #00ff00;
        box-shadow: 0 0 15px #00ff00;
        text-align: center;
        width: 80%;
        margin-bottom: 20px;
        font-family: 'Orbitron', sans-serif;
    }

    .projects {
        background-color: rgba(0, 255, 0, 0.1);
        padding: 20px;
        margin: 15px auto;
        border: 2px solid #00ff00;
        box-shadow: 0 0 15px #00ff00;
        text-align: center;
        font-size: 1.8em;
        border-radius: 10px;
        animation: glowing 1.5s ease-in-out infinite alternate;
        max-width: 80%;
        font-family: 'Orbitron', sans-serif;
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
        margin: 15px auto;
        border: 2px solid #00ff00;
        box-shadow: 0 0 15px #00ff00;
        text-align: center;
        font-size: 1.5em;
        border-radius: 10px;
        animation: glowing 1.5s ease-in-out infinite alternate;
        max-width: 80%;
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
        padding-top: 200px;
    }
</style>

</head>
<body><!-- Cuadro superior con el alias -->
<div class="banner">
    ⚡ BerMatModZ ⚡
</div>

<!-- Cuadro para Projects -->
<div class="projects">
    Projects
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
</div>

<script>
    let accessCodeVerified = false;

    function verifyCode() {
        const enteredCode = document.getElementById("access-code").value;
        const correctCode = "BerMat123";
        if (enteredCode === correctCode) {
            accessCodeVerified = true;
            alert("Código verificado con éxito.");
        } else {
            alert("Código incorrecto. Intenta nuevamente.");
        }
    }
</script>

</body>
</html>
