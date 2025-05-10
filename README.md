<!DOCTYPE html><html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Hackeo Oficial</title>
    <style>
        body {
            background-color: #0d0d0d;
            color: #00ff00;
            font-family: 'Orbitron', sans-serif;
            margin: 0;
            padding: 0;
            overflow: hidden;
        }.banner {
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
    }

    .projects, .info-box {
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
    }

    @keyframes glowing {
        0% { text-shadow: 0 0 5px #00ff00, 0 0 10px #00ff00, 0 0 15px #00ff00; }
        100% { text-shadow: 0 0 20px #00ff00, 0 0 30px #00ff00, 0 0 40px #00ff00; }
    }

    @keyframes bannerGlow {
        0% { color: #00ff00; }
        100% { color: #ff00ff; }
    }

    .main-content {
        padding-top: 200px;
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

<!-- Información detallada -->
<div class="info-box">
    <h2>Información del Creador</h2>
    <p><strong>Nombre:</strong> AnthZz Berrocal</p>
    <p><strong>Alias:</strong> BerMatModZ</p>
    <p><strong>Proyectos:</strong> Bots de WhatsApp, Seguridad Cibernética, Programación Avanzada</p>
    <p><strong>Intereses:</strong> Hacking, Inteligencia Artificial, Tecnología Avanzada</p>
    <p><strong>Servicios:</strong> Bots Personalizados, Scripts de Hacking, Sistemas de Seguridad</p>
    <p><strong>Contactos:</strong></p>
    <a href="https://wa.me/937556459?text=🔥%20Hola%20AnthZz%20Berrocal,%20quiero%20comprar%20tu%20servicio%20de%20hacker%20VIP%20💀%20-%20⚡%20Dame%20acceso%20al%20mundo%20de%20BerMatModZ%20⚡" style="color: #00ff00; text-decoration: none;">WhatsApp</a><br>
    <a href="https://github.com/Anthzberrocal" style="color: #00ff00; text-decoration: none;">GitHub</a><br>
    <a href="https://www.instagram.com/anthzberrocal" style="color: #00ff00; text-decoration: none;">Instagram</a>
</div>

<!-- Cuadro para Código de Acceso -->
<div class="info-box">
    <h2>Ingreso de Código de Acceso</h2>
    <input type="text" id="access-code" placeholder="Ingresa el código aquí..." style="width: 80%; padding: 10px;" />
    <button onclick="verifyCode()" style="margin-top: 10px; padding: 10px 20px;">Verificar Código</button>
</div>

<!-- Cuadro para Ingreso de Número -->
<div class="info-box">
    <h2>Ingresa el Número para Hackear</h2>
    <input type="text" id="phone-number" placeholder="Ej. 900233784" style="width: 80%; padding: 10px;" />
    <button onclick="startHack()" style="margin-top: 10px; padding: 10px 20px;">Iniciar Hackeo</button>
</div>

</body>
</html>
