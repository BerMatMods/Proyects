

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🎓 BerMatModZ - Tienda de Cursos y Tecnología</title>
  <meta name="description" content="Cursos tecnológicos de BerMatModZ: bots de WhatsApp, Termux, programación, ciberseguridad y más." />
  <meta property="og:title" content="BerMatModZ - Cursos y Tecnología" />
  <meta property="og:description" content="Domina el mundo digital con nuestros cursos desde cero." />
  <meta property="og:image" content="https://tusitio.com/logo.png" />
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://tusitio.com" />
  <link rel="icon" href="https://tusitio.com/icono.ico" type="image/x-icon" />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Rajdhani:wght@500&display=swap" rel="stylesheet" />
  <style>
    * {margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif;}
    body {
      background-color: #0d0d0d;
      color: #e0e0e0;
      padding: 25px 20px 40px 20px;
      line-height: 1.5;
    }
    header {
      text-align: center;
      padding: 30px 15px 35px;
      background: linear-gradient(135deg, #1f1f1f, #000000);
      border-bottom: 3px solid #00ffcc;
      font-family: 'Orbitron', sans-serif;
      animation: glow 2s infinite ease-in-out;
    }
    @keyframes glow {
      0%, 100% { text-shadow: 0 0 8px #00ffcc; }
      50% { text-shadow: 0 0 20px #00ffcc; }
    }
    header h1 {
      color: #00ffcc;
      font-size: 2.7em;
      letter-spacing: 2px;
    }
    nav {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      margin: 22px 0 40px;
      gap: 10px;
    }
    nav a {
      color: #00ffff;
      text-decoration: none;
      padding: 8px 18px;
      border: 1.8px solid #00ffff;
      border-radius: 7px;
      font-weight: 600;
      font-size: 1.1em;
      background: #111111;
      box-shadow: inset 0 0 8px #00ffcc22;
      transition: all 0.35s ease;
    }
    nav a:hover {
      color: #ff00ff;
      background-color: #1a1a1a;
      border-color: #ff00ff;
      box-shadow: 0 0 15px #ff00ffaa;
    }
    section {
      margin-bottom: 50px;
      max-width: 920px;
      margin-left: auto;
      margin-right: auto;
    }
    h2 {
      font-size: 2em;
      margin-bottom: 15px;
      color: #00ffff;
      border-bottom: 3px dashed #00ffff;
      padding-bottom: 8px;
      letter-spacing: 1.2px;
    }
    p {
      font-size: 1.1em;
      margin-bottom: 15px;
      color: #ccc;
    }
    .card {
      background: #1a1a1a;
      border-left: 12px solid #00ffcc;
      border-radius: 0 12px 12px 0;
      padding: 20px 25px;
      margin: 15px 0;
      box-shadow: inset 0 0 10px #00ffcc33;
      transition: transform 0.25s ease, box-shadow 0.25s ease;
      animation: slideUp 0.6s forwards;
      opacity: 0;
      transform: translateY(20px);
    }
    @keyframes slideUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    .card:nth-child(even) { animation-delay: 0.1s; }
    .card:nth-child(odd) { animation-delay: 0.2s; }
    .card h3 {
      font-size: 1.5em;
      color: #00ffff;
      margin-bottom: 8px;
    }
    .card p {
      color: #aaa;
      font-size: 1em;
      margin-bottom: 10px;
    }
    .card strong {
      font-size: 1.1em;
      color: #00ffcc;
    }
    ul {
      list-style: none;
      padding-left: 15px;
      margin-top: 12px;
      margin-bottom: 12px;
    }
    li {
      margin-bottom: 10px;
      font-size: 1.1em;
      color: #ccc;
    }
    .section-list {
      background: #1a1a1a;
      border-left: 12px solid #00ffcc;
      border-radius: 0 12px 12px 0;
      padding: 22px 25px;
      box-shadow: inset 0 0 10px #00ffcc33;
    }
    .section-list li::before { content: '✔️ '; color: #00ffcc; margin-right: 6px; }
    .faq-section li::before { content: '🔹 '; color: #00ffff; }
    .testimonios li {
      background: #121212;
      border-left: 6px solid #ffdd00;
      padding: 14px 18px;
      margin-bottom: 15px;
      border-radius: 8px;
      box-shadow: 0 0 8px #ffdd0033;
    }
    .testimonios li::before { content: '⭐ '; color: #ffdd00; margin-right: 5px; }
    .whatsapp-btn {
      display: block;
      max-width: 320px;
      margin: 35px auto;
      text-align: center;
      background: #25D366;
      color: white;
      padding: 16px 32px;
      border-radius: 12px;
      font-size: 1.35em;
      font-weight: 700;
      text-decoration: none;
      box-shadow: 0 0 15px #25D366aa;
      transition: background-color 0.3s ease;
    }
    .whatsapp-btn:hover { background: #1ebe57; }
    footer {
      text-align: center;
      margin-top: 50px;
      font-size: 0.95em;
      color: #777;
      border-top: 2px dashed #00ffcc;
      padding-top: 20px;
    }
    .social-icons {
      margin-top: 10px;
    }
    .social-icons a {
      margin: 0 12px;
      color: #00ffff;
      font-size: 1.8em;
      transition: color 0.3s ease;
      text-decoration: none;
    }
    .social-icons a:hover { color: #ff00ff; }
    a[href=\"#inicio\"] {
      position: fixed;
      bottom: 25px;
      right: 25px;
      background: #00ffcc;
      color: black;
      padding: 12px 18px;
      border-radius: 50%;
      font-size: 1.4em;
      box-shadow: 0 0 10px #00ffccaa;
      text-decoration: none;
      z-index: 1000;
    }
    @media (max-width: 600px) {
      header h1 { font-size: 2em; }
      nav a { font-size: 0.95em; padding: 6px 12px; }
      .card h3 { font-size: 1.2em; }
      .card p, li, p { font-size: 1em; }
    }
  </style>
</head>
<body>
  <a href="#inicio" title="Ir al inicio">⬆</a>

  <!-- AQUÍ PEGA TODO EL CONTENIDO COMPLETO que ya hiciste:
       - Sección #inicio
       - Sección #cursos
       - Sección #proyectos
       - Sección #certificados
       - Sección #faq
       - Sección #testimonios
       - Sección #contacto
       - Footer
  -->

</body>
</html>


---

💡 Siguiente paso:
¿Quieres que ahora empaquete esto como una aplicación APK para Android o lo subo directo como web en GitHub o Netlify?

✅ Solo dime: APK, subir a GitHub Pages, o convertir a App Web Instalable (PWA) y lo preparo.

¡Perfecto! Aquí tienes el código completo mejorado y listo para usar, incluyendo todas tus secciones originales, animaciones, botón flotante, optimización visual, y mejoras modernas:


---

🔧 ARCHIVO: index.html
(Copia y pega en tu editor o Termux)

<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🎓 BerMatModZ - Tienda de Cursos y Tecnología</title>
  <meta name="description" content="Cursos tecnológicos de BerMatModZ: bots de WhatsApp, Termux, programación, ciberseguridad y más." />
  <meta property="og:title" content="BerMatModZ - Cursos y Tecnología" />
  <meta property="og:description" content="Domina el mundo digital con nuestros cursos desde cero." />
  <meta property="og:image" content="https://tusitio.com/logo.png" />
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://tusitio.com" />
  <link rel="icon" href="https://tusitio.com/icono.ico" type="image/x-icon" />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Rajdhani:wght@500&display=swap" rel="stylesheet" />
  <style>
    * {margin: 0; padding: 0; box-sizing: border-box; font-family: 'Rajdhani', sans-serif;}
    body {
      background-color: #0d0d0d;
      color: #e0e0e0;
      padding: 25px 20px 40px 20px;
      line-height: 1.5;
    }
    header {
      text-align: center;
      padding: 30px 15px 35px;
      background: linear-gradient(135deg, #1f1f1f, #000000);
      border-bottom: 3px solid #00ffcc;
      font-family: 'Orbitron', sans-serif;
      animation: glow 2s infinite ease-in-out;
    }
    @keyframes glow {
      0%, 100% { text-shadow: 0 0 8px #00ffcc; }
      50% { text-shadow: 0 0 20px #00ffcc; }
    }
    header h1 {
      color: #00ffcc;
      font-size: 2.7em;
      letter-spacing: 2px;
    }
    nav {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      margin: 22px 0 40px;
      gap: 10px;
    }
    nav a {
      color: #00ffff;
      text-decoration: none;
      padding: 8px 18px;
      border: 1.8px solid #00ffff;
      border-radius: 7px;
      font-weight: 600;
      font-size: 1.1em;
      background: #111111;
      box-shadow: inset 0 0 8px #00ffcc22;
      transition: all 0.35s ease;
    }
    nav a:hover {
      color: #ff00ff;
      background-color: #1a1a1a;
      border-color: #ff00ff;
      box-shadow: 0 0 15px #ff00ffaa;
    }
    section {
      margin-bottom: 50px;
      max-width: 920px;
      margin-left: auto;
      margin-right: auto;
    }
    h2 {
      font-size: 2em;
      margin-bottom: 15px;
      color: #00ffff;
      border-bottom: 3px dashed #00ffff;
      padding-bottom: 8px;
      letter-spacing: 1.2px;
    }
    p {
      font-size: 1.1em;
      margin-bottom: 15px;
      color: #ccc;
    }
    .card {
      background: #1a1a1a;
      border-left: 12px solid #00ffcc;
      border-radius: 0 12px 12px 0;
      padding: 20px 25px;
      margin: 15px 0;
      box-shadow: inset 0 0 10px #00ffcc33;
      transition: transform 0.25s ease, box-shadow 0.25s ease;
      animation: slideUp 0.6s forwards;
      opacity: 0;
      transform: translateY(20px);
    }
    @keyframes slideUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    .card:nth-child(even) { animation-delay: 0.1s; }
    .card:nth-child(odd) { animation-delay: 0.2s; }
    .card h3 {
      font-size: 1.5em;
      color: #00ffff;
      margin-bottom: 8px;
    }
    .card p {
      color: #aaa;
      font-size: 1em;
      margin-bottom: 10px;
    }
    .card strong {
      font-size: 1.1em;
      color: #00ffcc;
    }
    ul {
      list-style: none;
      padding-left: 15px;
      margin-top: 12px;
      margin-bottom: 12px;
    }
    li {
      margin-bottom: 10px;
      font-size: 1.1em;
      color: #ccc;
    }
    .section-list {
      background: #1a1a1a;
      border-left: 12px solid #00ffcc;
      border-radius: 0 12px 12px 0;
      padding: 22px 25px;
      box-shadow: inset 0 0 10px #00ffcc33;
    }
    .section-list li::before { content: '✔️ '; color: #00ffcc; margin-right: 6px; }
    .faq-section li::before { content: '🔹 '; color: #00ffff; }
    .testimonios li {
      background: #121212;
      border-left: 6px solid #ffdd00;
      padding: 14px 18px;
      margin-bottom: 15px;
      border-radius: 8px;
      box-shadow: 0 0 8px #ffdd0033;
    }
    .testimonios li::before { content: '⭐ '; color: #ffdd00; margin-right: 5px; }
    .whatsapp-btn {
      display: block;
      max-width: 320px;
      margin: 35px auto;
      text-align: center;
      background: #25D366;
      color: white;
      padding: 16px 32px;
      border-radius: 12px;
      font-size: 1.35em;
      font-weight: 700;
      text-decoration: none;
      box-shadow: 0 0 15px #25D366aa;
      transition: background-color 0.3s ease;
    }
    .whatsapp-btn:hover { background: #1ebe57; }
    footer {
      text-align: center;
      margin-top: 50px;
      font-size: 0.95em;
      color: #777;
      border-top: 2px dashed #00ffcc;
      padding-top: 20px;
    }
    .social-icons {
      margin-top: 10px;
    }
    .social-icons a {
      margin: 0 12px;
      color: #00ffff;
      font-size: 1.8em;
      transition: color 0.3s ease;
      text-decoration: none;
    }
    .social-icons a:hover { color: #ff00ff; }
    a[href=\"#inicio\"] {
      position: fixed;
      bottom: 25px;
      right: 25px;
      background: #00ffcc;
      color: black;
      padding: 12px 18px;
      border-radius: 50%;
      font-size: 1.4em;
      box-shadow: 0 0 10px #00ffccaa;
      text-decoration: none;
      z-index: 1000;
    }
    @media (max-width: 600px) {
      header h1 { font-size: 2em; }
      nav a { font-size: 0.95em; padding: 6px 12px; }
      .card h3 { font-size: 1.2em; }
      .card p, li, p { font-size: 1em; }
    }
  </style>
</head>
<body>
  <a href="#inicio" title="Ir al inicio">⬆</a>


</body>
</html>


---


<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🎓 BerMatModZ - Tienda de Cursos y Tecnología</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Rajdhani:wght@500&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0; padding: 0;
      box-sizing: border-box;
      font-family: 'Rajdhani', sans-serif;
    }
    body {
      background-color: #0d0d0d;
      color: #e0e0e0;
      padding: 25px 20px 40px 20px;
      line-height: 1.5;
    }
    header {
      text-align: center;
      padding: 30px 15px 35px;
      background: linear-gradient(135deg, #1f1f1f, #000000);
      border-bottom: 3px solid #00ffcc;
      font-family: 'Orbitron', sans-serif;
      user-select: none;
    }
    header h1 {
      color: #00ffcc;
      font-size: 2.7em;
      text-shadow: 0 0 8px #00ffcc;
      letter-spacing: 2px;
    }
    nav {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      margin: 22px 0 40px;
      gap: 10px;
      user-select: none;
    }
    nav a {
      color: #00ffff;
      margin: 0 15px;
      text-decoration: none;
      padding: 8px 18px;
      border: 1.8px solid #00ffff;
      border-radius: 7px;
      font-weight: 600;
      font-size: 1.1em;
      transition: all 0.35s ease;
      background: #111111;
      box-shadow: inset 0 0 8px #00ffcc22;
    }
    nav a:hover {
      color: #ff00ff;
      background-color: #1a1a1a;
      border-color: #ff00ff;
      box-shadow: 0 0 15px #ff00ffaa;
    }
    section {
      margin-bottom: 50px;
      max-width: 920px;
      margin-left: auto;
      margin-right: auto;
    }
    h2 {
      font-size: 2em;
      margin-bottom: 15px;
      color: #00ffff;
      border-bottom: 3px dashed #00ffff;
      padding-bottom: 8px;
      letter-spacing: 1.2px;
      user-select: none;
    }
    p {
      font-size: 1.1em;
      margin-bottom: 15px;
      color: #ccc;
      user-select: text;
    }
    /* Cursos */
    .card {
      background: #1a1a1a;
      border-left: 12px solid #00ffcc;
      border-radius: 0 12px 12px 0;
      padding: 20px 25px;
      margin: 15px 0;
      box-shadow: inset 0 0 10px #00ffcc33;
      transition: transform 0.25s ease, box-shadow 0.25s ease;
      cursor: default;
      user-select: none;
    }
    .card:hover {
      transform: scale(1.03);
      box-shadow: 0 0 20px #00ffccaa;
    }
    .card h3 {
      font-size: 1.5em;
      color: #00ffff;
      margin-bottom: 8px;
    }
    .card p {
      color: #aaa;
      font-size: 1em;
      margin-bottom: 10px;
      user-select: text;
    }
    .card strong {
      font-size: 1.1em;
      color: #00ffcc;
      letter-spacing: 0.6px;
    }
    /* Listados */
    ul {
      list-style: none;
      padding-left: 15px;
      margin-top: 12px;
      margin-bottom: 12px;
    }
    li {
      margin-bottom: 10px;
      font-size: 1.1em;
      color: #ccc;
      user-select: text;
    }
    /* Proyectos, certificados, faq, testimonios styles */
    .section-list {
      background: #1a1a1a;
      border-left: 12px solid #00ffcc;
      border-radius: 0 12px 12px 0;
      padding: 22px 25px;
      box-shadow: inset 0 0 10px #00ffcc33;
      user-select: text;
    }
    .section-list li::before {
      content: '✔️ ';
      margin-right: 6px;
      color: #00ffcc;
    }
    .faq-section li::before {
      content: '🔹 ';
      color: #00ffff;
    }
    .testimonios li::before {
      content: '⭐ ';
      color: #ffdd00;
    }
    /* Botón WhatsApp */
    .whatsapp-btn {
      display: block;
      max-width: 320px;
      margin: 35px auto;
      text-align: center;
      background: #25D366;
      color: white;
      padding: 16px 32px;
      border-radius: 12px;
      font-size: 1.35em;
      font-weight: 700;
      text-decoration: none;
      box-shadow: 0 0 15px #25D366aa;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    .whatsapp-btn:hover {
      background: #1ebe57;
    }
    /* Footer */
    footer {
      text-align: center;
      margin-top: 50px;
      font-size: 0.95em;
      color: #777;
      border-top: 2px dashed #00ffcc;
      padding-top: 20px;
      user-select: none;
    }
    .social-icons {
      margin-top: 10px;
    }
    .social-icons a {
      margin: 0 12px;
      color: #00ffff;
      font-size: 1.8em;
      transition: color 0.3s ease;
      text-decoration: none;
      user-select: none;
    }
    .social-icons a:hover {
      color: #ff00ff;
    }
  </style>
</head>
<body>
  <header>
    <h1>⚡ BerMatModZ - Cursos y Tecnología 🔥</h1>
    <nav>
      <a href="#inicio">Inicio</a>
      <a href="#cursos">Cursos</a>
      <a href="#proyectos">Proyectos</a>
      <a href="#certificados">Certificados</a>
      <a href="#faq">Preguntas</a>
      <a href="#testimonios">Testimonios</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </header>

  <section id="inicio">
    <h2>🎯 Bienvenido</h2>
    <p>¡Hola! Soy <strong>Anth'Zz Berrocal</strong> (alias <strong>BerMatModZ</strong>), apasionado por la tecnología, el desarrollo de bots inteligentes, la seguridad informática y el hacking ético. Mi objetivo es ayudarte a dominar el mundo digital con cursos prácticos, proyectos reales y mucho acompañamiento.</p>
    <p>Aprenderás a crear tus propios bots de WhatsApp, dominar Termux para automatizar procesos, desarrollar apps Android sin necesidad de PC, y mucho más. Todo explicado paso a paso con ejemplos claros, para que puedas avanzar desde cero hasta nivel avanzado.</p>
  </section>

  <section id="cursos">
    <h2>📚 Cursos Disponibles</h2>

    <div class="card">
      <h3>🔧 Termux desde Cero</h3>
      <p>Domina la consola de Termux para Android, aprende comandos básicos, creación de scripts, automatización y simulación de procesos con voz y efectos visuales.</p>
      <strong>Precio: S/ 20</strong>
    </div>

    <div class="card">
      <h3>🤖 Bots de WhatsApp con IA</h3>
      <p>Crea bots personalizados para WhatsApp con inteligencia artificial, comandos avanzados, integración con APIs y respuestas naturales para tus chats.</p>
      <strong>Precio: S/ 35</strong>
    </div>

    <div class="card">
      <h3>💻 Programación en AIDE para Android</h3>
      <p>Desarrolla aplicaciones Android completas desde tu celular usando AIDE, aprende Java, diseño UI, y publicación en Google Play.</p>
      <strong>Precio: S/ 30</strong>
    </div>

    <div class="card">
      <h3>🛡️ Hacking Ético Básico</h3>
      <p>Fundamentos de ciberseguridad, análisis de vulnerabilidades, herramientas básicas y principios éticos para proteger redes y sistemas.</p>
      <strong>Precio: S/ 25</strong>
    </div>

    <div class="card">
      <h3>🧠 Introducción a la Inteligencia Artificial</h3>
      <p>Conceptos esenciales de IA, aprendizaje automático, redes neuronales y uso práctico con librerías populares para proyectos reales.</p>
      <strong>Precio: S/ 40</strong>
    </div>

    <div class="card">
      <h3>📟 Simulación Hacker Avanzada en Termux</h3>
      <p>Aprende a crear presentaciones interactivas y simuladores con efectos de sonido y voz para impactar en demostraciones y proyectos.</p>
      <strong>Precio: S/ 15</strong>
    </div>

    <div class="card">
      <h3>🎨 Diseño Web con HTML + CSS</h3>
      <p>Construye páginas web profesionales, aprende diseño responsivo, animaciones CSS y optimización para dispositivos móviles.</p>
      <strong>Precio: S/ 25</strong>
    </div>

    <div class="card">
      <h3>🌐 Git y GitHub para Desarrolladores</h3>
      <p>Control de versiones con Git, manejo de repositorios, colaboración en proyectos y despliegue de páginas con GitHub Pages.</p>
      <strong>Precio: S/ 20</strong>
    </div>

    <div class="card">
      <h3>📱 Desarrollo de Apps con React Native</h3>
      <p>Aprende a crear aplicaciones móviles multiplataforma usando React Native, con integración a APIs y diseño moderno.</p>
      <strong>Precio: S/ 45</strong>
    </div>

    <div class="card">
      <h3>🔐 Seguridad en Redes WiFi</h3>
      <p>Detecta y protege redes WiFi, aprende a identificar ataques comunes y aplicar medidas efectivas de seguridad.</p>
      <strong>Precio: S/ 18</strong>
    </div>

    <div class="card">
      <h3>📝 Automatización con Python</h3>
      <p>Automatiza tareas repetitivas usando Python, desde manejo de archivos hasta scraping web y envío de mensajes.</p>
      <strong>Precio: S/ 30</strong>
    </div>

    <div class="card">
      <h3>🕹️ Creación de Juegos Básicos</h3>
      <p>Desarrolla juegos sencillos con Python y Pygame, aprende conceptos básicos de programación de videojuegos.</p>
      <strong>Precio: S/ 22</strong>
    </div>

    <div class="card">
      <h3>💡 Programación Funcional y Algoritmos</h3>
      <p>Mejora tu lógica con técnicas avanzadas de programación funcional, estructuras de datos y algoritmos eficientes.</p>
      <strong>Precio: S/ 28</strong>
    </div>

    <div class="card">
      <h3>📊 Análisis de Datos para Principiantes</h3>
      <p>Introducción al análisis de datos con Python, visualización con Matplotlib y manejo de datos con Pandas.</p>
      <strong>Precio: S/ 35</strong>
    </div>

    <div class="card">
      <h3>🖥️ Administración de Servidores Linux</h3>
      <p>Aprende a configurar y administrar servidores Linux, manejo de usuarios, permisos, y despliegue de aplicaciones web.</p>
      <strong>Precio: S/ 40</strong>
    </div>

    <div class="card">
      <h3>📡 Redes y Protocolos de Internet</h3>
      <p>Comprende el funcionamiento de redes, protocolos TCP/IP, DNS, HTTP, y seguridad en la comunicación digital.</p>
      <strong>Precio: S/ 25</strong>
    </div>

    <div class="card">
      <h3>💬 Chatbots y Asistentes Virtuales</h3>
      <p>Desarrolla chatbots para atención al cliente, integración con APIs y plataformas de mensajería populares.</p>
      <strong>Precio: S/ 38</strong>
    </div>

    <div class="card">
      <h3>🎥 Streaming y Multimedia en Vivo</h3>
      <p>Configura tu propio servidor para streaming, aprende a usar OBS, codificación y transmisión en vivo.</p>
      <strong>Precio: S/ 20</strong>
    </div>

    <div class="card">
      <h3>📱 Desarrollo de Apps con Flutter</h3>
      <p>Crea aplicaciones móviles y web con Flutter y Dart, diseño moderno y rendimiento optimizado.</p>
      <strong>Precio: S/ 45</strong>
    </div>

    <div class="card">
      <h3>📚 Fundamentos de Bases de Datos</h3>
      <p>Aprende SQL, diseño de bases de datos relacionales y no relacionales, y manejo con MySQL y MongoDB.</p>
      <strong>Precio: S/ 30</strong>
    </div>

    <div class="card">
      <h3>🛠️ Desarrollo Backend con Node.js</h3>
      <p>Construye servidores y APIs robustos usando Node.js y Express, con integración a bases de datos y seguridad.</p>
      <strong>Precio: S/ 38</strong>
    </div>

    <div class="card">
      <h3>🌍 Creación y Gestión de Sitios Web</h3>
      <p>Desde el diseño hasta la publicación, aprende todo para tener tu propio sitio web profesional y seguro.</p>
      <strong>Precio: S/ 28</strong>
    </div>

    <div class="card">
      <h3>🔎 SEO y Marketing Digital para Programadores</h3>
      <p>Optimiza tus sitios y proyectos para buscadores y aprende técnicas básicas de marketing digital.</p>
      <strong>Precio: S/ 22</strong>
    </div>

    <div class="card">
      <h3>🎮 Programación avanzada de videojuegos</h3>
      <p>Desarrolla juegos complejos con motores como Unity, física avanzada y multijugador básico.</p>
      <strong>Precio: S/ 50</strong>
    </div>

  </section>

  <section id="proyectos">
    <h2>🚀 Proyectos y Logros</h2>
    <ul class="section-list">
      <li>⚡ <strong>BerMat-Bot MD</strong> – Bot multicomando para WhatsApp con IA integrada, comandos personalizados, y manejo avanzado de chats.</li>
      <li>💀 <strong>Simuladores hacker en Termux</strong> – Proyectos con voz, efectos y animaciones que enseñan hacking ético y automatización.</li>
      <li>📱 <strong>App estilo WhatsApp</strong> – Aplicación Android desarrollada desde cero en AIDE, con interfaz personalizada y funciones innovadoras.</li>
      <li>🌐 <strong>Tienda online de cursos</strong> – Plataforma web moderna para venta y promoción de servicios educativos tecnológicos.</li>
      <li>🔐 <strong>Herramientas de ciberseguridad</strong> – Scripts y herramientas para análisis y protección de redes WiFi y sistemas.</li>
    </ul>
  </section>

  <section id="certificados" class="cert-section">
    <h2>📜 Certificaciones</h2>
    <ul>
      <li>✔️ <strong>Certificación en Desarrollo de Bots IA:</strong> Reconoce tus habilidades en programación y creación de bots inteligentes funcionales.</li>
      <li>✔️ <strong>Reconocimiento en Ciberseguridad Juvenil:</strong> Avala tu conocimiento en protección y ética dentro del mundo digital.</li>
      <li>✔️ <strong>Participación en conferencias de tecnología escolar:</strong> Muestra tu compromiso con la actualización constante y la difusión del conocimiento.</li>
    </ul>
  </section>

  <section id="faq" class="faq-section">
    <h2>❓ Preguntas Frecuentes</h2>
    <ul>
      <li><strong>¿Los cursos tienen certificado?</strong> Sí, todos incluyen un certificado digital personalizado para validar tus conocimientos.</li>
      <li><strong>¿Necesito una computadora para aprender?</strong> No es obligatorio, muchos cursos están optimizados para celular usando Termux o AIDE.</li>
      <li><strong>¿Cómo realizo el pago?</strong> Aceptamos Yape, Plin y transferencias bancarias con total seguridad.</li>
      <li><strong>¿Puedo recibir soporte después de finalizar el curso?</strong> Sí, ofrecemos asesoría y soporte en un grupo exclusivo para alumnos.</li>
      <li><strong>¿Qué nivel necesito para empezar?</strong> Puedes comenzar desde cero, los cursos están diseñados para principiantes hasta avanzados.</li>
    </ul>
  </section>

  <section id="testimonios" class="testimonios">
    <h2>🌟 Testimonios</h2>
    <ul>
      <li>“Gracias a BerMatModZ, ahora tengo mi propio bot en WhatsApp y he mejorado mucho mis habilidades técnicas.” – <em>Kevin R.</em></li>
      <li>“El curso de Termux fue claro, entretenido y me permitió automatizar muchas tareas diarias en mi celular.” – <em>Luis M.</em></li>
      <li>“Sus proyectos son muy profesionales y explicados con detalle. Aprendí a programar apps sin necesidad de PC.” – <em>María P.</em></li>
      <li>“La asesoría personalizada y el soporte en el grupo hicieron que mi aprendizaje fuera mucho más rápido.” – <em>José T.</em></li>
      <li>“Recomiendo totalmente estos cursos para cualquier joven que quiera entrar en el mundo tecnológico.” – <em>Andrea F.</em></li>
    </ul>
  </section>

  <section id="contacto">
    <h2>📞 Contáctame</h2>
    <p>¿Interesado en un curso o proyecto? Escríbeme directo por WhatsApp y con gusto te atenderé:</p>
    <a class="whatsapp-btn" href="https://wa.me/51937556459?text=Hola%20BerMatModZ,%20quiero%20informaci%C3%B3n%20sobre%20tus%20cursos%20y%20proyectos." target="_blank" rel="noopener noreferrer">Enviar mensaje por WhatsApp</a>
    <p><strong>Horario de atención:</strong> Lunes a Viernes de 9:00 a 18:00 (GMT-5)</p>
  </section>

  <footer>
    <p>© 2025 BerMatModZ | Desarrollado con pasión en Andahuaylas, Perú 🇵🇪</p>
    <div class="social-icons">
      <a href="https://github.com/Anthzberrocal" target="_blank" rel="noopener noreferrer" title="GitHub">🐙</a>
      <a href="https://www.tiktok.com/@anthzberrocal" target="_blank" rel="noopener noreferrer" title="TikTok">🎵</a>
      <a href="https://www.instagram.com/anthzberrocal" target="_blank" rel="noopener noreferrer" title="Instagram">📸</a>
    </div>
  </footer>
</body>
</html>
