
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>Carta de Amor - 10/11/23</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Playfair+Display:wght@700&family=Poppins:wght@400;500&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fff5f8, #f9e6ff, #ffe6f0);
      color: #444;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 20px;
      overflow-x: hidden;
      position: relative;
    }

    /* Botón del menú (3 rayitas) */
    .menu-btn {
      position: absolute;
      top: 20px;
      left: 20px;
      width: 50px;
      height: 50px;
      background: rgba(233, 30, 99, 0.2);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      z-index: 100;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      transition: all 0.3s;
    }

    .menu-btn span {
      display: block;
      width: 24px;
      height: 3px;
      background: #e91e63;
      margin: 3px 0;
      border-radius: 2px;
      transition: 0.3s;
    }

    .menu-btn:hover {
      transform: scale(1.1);
      background: rgba(233, 30, 99, 0.3);
    }

    /* Menú desplegable */
    .menu {
      position: fixed;
      top: 0;
      left: -300px;
      width: 280px;
      height: 100vh;
      background: rgba(255, 255, 255, 0.98);
      backdrop-filter: blur(10px);
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.1);
      padding: 60px 20px 20px;
      transition: left 0.4s ease;
      z-index: 99;
      border-radius: 0 20px 20px 0;
      border-left: 3px solid #e91e63;
      overflow-y: auto;
    }

    .menu.open {
      left: 0;
    }

    .menu h3 {
      font-family: 'Playfair Display', serif;
      color: #e91e63;
      margin-bottom: 1.2rem;
      font-size: 1.4rem;
      border-bottom: 2px solid #ffb6c1;
      padding-bottom: 0.5rem;
    }

    .menu label {
      display: block;
      margin: 1rem 0 0.5rem;
      color: #777;
      font-size: 0.95rem;
    }

    .menu input {
      width: 100%;
      padding: 0.8rem;
      border: 2px solid #ffb6c1;
      border-radius: 10px;
      font-family: 'Poppins', sans-serif;
      font-size: 1rem;
      background: #fff8fa;
    }

    /* Botón WhatsApp bonito */
    .whatsapp-btn {
      display: block;
      margin: 1.8rem 0 0;
      padding: 1rem 1.4rem;
      background: linear-gradient(45deg, #25D366, #128C7E);
      color: white;
      text-align: center;
      border-radius: 14px;
      text-decoration: none;
      font-weight: 600;
      font-size: 1.1rem;
      box-shadow: 0 6px 15px rgba(37, 211, 102, 0.4);
      transition: all 0.3s;
    }

    .whatsapp-btn:hover {
      transform: scale(1.05);
      box-shadow: 0 8px 20px rgba(37, 211, 102, 0.5);
    }

    .whatsapp-btn i {
      margin-right: 8px;
    }

    /* Cerrar menú */
    .close-menu {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 1.5rem;
      color: #e91e63;
      cursor: pointer;
    }

    /* Animación RGB suave */
    @keyframes rgbPulse {
      0% { box-shadow: 0 0 20px rgba(255, 105, 180, 0.5); }
      33% { box-shadow: 0 0 20px rgba(140, 100, 255, 0.5); }
      66% { box-shadow: 0 0 20px rgba(255, 190, 100, 0.5); }
      100% { box-shadow: 0 0 20px rgba(255, 105, 180, 0.5); }
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    /* Marco RGB animado para GIFs */
    .gif-frame {
      border-radius: 18px;
      padding: 3px;
      margin: 1.4rem 0;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80, #e91e63);
      background-size: 300% 300%;
      animation: rgbPulse 4s infinite alternate, backgroundShift 6s ease-in-out infinite;
      position: relative;
    }

    @keyframes backgroundShift {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }

    .gif-frame img {
      border-radius: 15px;
      display: block;
      width: 100%;
      height: auto;
      border: 4px solid #fff;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }

    /* Pantalla de bloqueo */
    .lock-screen {
      text-align: center;
      padding: 2rem;
      max-width: 420px;
      background: rgba(255, 255, 255, 0.98);
      border-radius: 30px;
      box-shadow: 0 12px 40px rgba(255, 105, 180, 0.3);
      border: 3px solid transparent;
      background-clip: padding-box;
      position: relative;
      z-index: 1;
    }

    .lock-screen::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8, #ffcc80);
      border-radius: 33px;
      z-index: -1;
      animation: backgroundShift 6s ease-in-out infinite;
      opacity: 0.7;
    }

    .lock-screen h2 {
      font-family: 'Playfair Display', serif;
      font-size: 2rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #ff8f00);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin: 1rem 0;
      animation: backgroundShift 6s ease-in-out infinite;
    }

    .lock-screen p {
      color: #d81b60;
      font-size: 1.15rem;
      margin-bottom: 1.4rem;
      font-weight: 500;
    }

    /* Display de clave */
    .key-display {
      font-family: 'Poppins', monospace;
      font-size: 1.8rem;
      color: #e91e63;
      background: linear-gradient(135deg, #fff0f5, #ffe6f0);
      padding: 1rem 1.3rem;
      border-radius: 16px;
      margin: 1.3rem auto;
      width: 90%;
      border: 3px solid #ff80ab;
      letter-spacing: 4px;
      box-shadow: 0 6px 15px rgba(255, 105, 180, 0.2);
    }

    /* Teclado */
    .keypad {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 14px;
      margin: 1.5rem 0;
    }

    .key {
      font-size: 1.45rem;
      font-weight: 600;
      padding: 1.1rem 0;
      background: linear-gradient(135deg, #fff5f8, #ffe6f0);
      color: #e91e63;
      border: 3px solid #ff80ab;
      border-radius: 14px;
      cursor: pointer;
      transition: all 0.25s ease;
      box-shadow: 0 4px 10px rgba(255, 105, 180, 0.2);
    }

    .key:hover {
      background: linear-gradient(135deg, #ffe6f0, #f8dafa);
      transform: translateY(-4px);
      box-shadow: 0 8px 18px rgba(255, 105, 180, 0.35);
    }

    .key:active {
      transform: translateY(-2px);
    }

    /* Botón Iniciar */
    .btn-iniciar {
      margin-top: 1.6rem;
      padding: 1rem 2.2rem;
      font-size: 1.3rem;
      font-weight: 600;
      background: linear-gradient(45deg, #e91e63, #ba68c8, #8e24aa);
      color: white;
      border: none;
      border-radius: 32px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(233, 30, 99, 0.4);
      transition: all 0.3s ease;
      animation: float 3s ease-in-out infinite;
    }

    .btn-iniciar:hover {
      transform: scale(1.08) translateY(-2px);
      box-shadow: 0 10px 25px rgba(233, 30, 99, 0.5);
    }

    /* Texto discreto */
    .dev-text {
      margin-top: 1.5rem;
      font-size: 0.8rem;
      color: #bbb;
      font-style: italic;
    }

    /* Contenedor principal */
    .main-container {
      display: none;
      text-align: center;
      max-width: 95%;
      padding: 2.2rem 1.6rem;
    }

    .letter-frame {
      background: rgba(255, 255, 255, 0.95);
      border-radius: 30px;
      padding: 2.4rem 2rem;
      box-shadow: 0 15px 40px rgba(255, 105, 180, 0.25);
      border: 4px solid transparent;
      background-clip: padding-box;
      position: relative;
    }

    .letter-frame::before {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 30px;
      padding: 4px;
      background: linear-gradient(45deg, #ff80ab, #ba68c8);
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: destination-out;
      mask-composite: subtract;
      pointer-events: none;
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      background: linear-gradient(45deg, #e91e63, #ba68c8);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 1.8rem;
    }

    .letter {
      font-family: 'Dancing Script', 'Poppins', cursive;
      font-size: 1.35rem;
      line-height: 1.55;
      color: #e91e63;
      text-align: left;
      white-space: pre-line;
      letter-spacing: 0.5px;
      margin: 0;
      opacity: 0;
    }

    footer {
      margin-top: 2rem;
      font-style: italic;
      color: #ba68c8;
      font-size: 1.15rem;
    }

    /* Corazones flotando */
    .floating-heart {
      position: absolute;
      font-size: 20px;
      pointer-events: none;
      opacity: 0;
      animation: floatUp 12s ease-in-out infinite, blink 2s ease-in-out infinite;
      z-index: 0;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 0;
      }
      10% { opacity: 0.8; }
      90% { opacity: 0.9; }
      100% {
        transform: translateY(-20vh) rotate(360deg);
        opacity: 0;
      }
    }

    @keyframes blink {
      0%, 100% { opacity: 0.7; }
      50% { opacity: 1; }
    }

    @media (max-width: 480px) {
      .menu-btn { top: 15px; left: 15px; width: 45px; height: 45px; }
      .menu { width: 260px; }
      .menu.open { left: 0; }

      .lock-screen, .main-container {
        padding: 1.5rem;
        max-width: 98%;
      }

      .key-display {
        font-size: 1.6rem;
      }

      h1 {
        font-size: 2.1rem;
      }

      .letter {
        font-size: 1.25rem;
        line-height: 1.5;
      }

      .btn-iniciar {
        font-size: 1.2rem;
        padding: 0.9rem 2rem;
      }
    }
  </style>
</head>
<body>

  <!-- Botón del menú (3 rayitas) -->
  <div class="menu-btn" onclick="toggleMenu()">
    <span></span>
    <span></span>
    <span></span>
  </div>

  <!-- Menú desplegable -->
  <div id="menu" class="menu">
    <div class="close-menu" onclick="toggleMenu()">✕</div>

    <h3>✏️ Personaliza tu Carta</h3>
    <label>Tu Nombre</label>
    <input type="text" id="nombreYo" value="AnthZz Berrocal" oninput="actualizarNombres()">

    <label>Nombre de tu Novia</label>
    <input type="text" id="nombreElla" value="Yorchi" oninput="actualizarNombres()">

    <h3>ℹ️ Información del Proyecto</h3>
    <p>Proyecto creado con amor por:</p>
    <strong>AnthZz Berrocal</strong>
    <small>Desarrollador | BerMatMods</small>
    <br><br>
    <a href="https://wa.me/51937556459" target="_blank" class="whatsapp-btn">
      💬 Contactar por WhatsApp
    </a>
  </div>

  <!-- Pantalla de bloqueo -->
  <div id="lockScreen" class="lock-screen">
    <h2>🔐 Tu Carta de Amor</h2>
    <p>Fecha especial: 10/11/23</p>

    <div class="gif-frame">
      <img src="https://media2.giphy.com/media/v1.Y2lkPTZjMDliOTUyZTAxbHV0Mm1rYmI2emc3ZmdvcGdka2szMGMzMHl4ZXlhcmEzN3A4cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Y62ofc4S1Vst2/giphy.gif" alt="Corazones flotando" width="200" height="200" />
    </div>

    <div id="display" class="key-display"></div>

    <div class="keypad">
      <div class="key" onclick="addDigit('1')">1</div>
      <div class="key" onclick="addDigit('2')">2</div>
      <div class="key" onclick="addDigit('3')">3</div>
      <div class="key" onclick="addDigit('4')">4</div>
      <div class="key" onclick="addDigit('5')">5</div>
      <div class="key" onclick="addDigit('6')">6</div>
      <div class="key" onclick="addDigit('7')">7</div>
      <div class="key" onclick="addDigit('8')">8</div>
      <div class="key" onclick="addDigit('9')">9</div>
      <div class="key" onclick="addDigit('0')">0</div>
      <div class="key" onclick="addDigit('/')">/</div>
      <div class="key" onclick="clearInput()">⌫</div>
    </div>

    <button class="btn-iniciar" onclick="submitKey()">Iniciar</button>

    <div class="gif-frame">
      <img src="https://media0.giphy.com/media/v1.Y2lkPTZjMDliOTUyMzl0NTh2ZHhmOHF1Nm45NHNqcmN1bTVrdHNtbDgwbjZpZTFqMno3diZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11TyfGbDbBv4be/giphy.gif" alt="Bailarina de amor" width="200" height="200" />
    </div>

    <p class="dev-text">Desarrollado por AnthZz Berrocal</p>
  </div>

  <!-- Carta principal -->
  <div id="mainContainer" class="main-container">
    <div class="letter-frame">
      <h1>Para mi Amor 💖</h1>
      <div id="letter" class="letter"></div>
      <footer>Con todo mi corazón, siempre tuyo.</footer>
    </div>

    <div class="gif-frame" style="margin-top: 2.2rem;">
      <img src="https://media4.giphy.com/media/v1.Y2lkPTZjMDliOTUyMHR3Ym5zNjF2emowZnZ5cWltZmJ6ZGRuaDM2ZXU5eDR1bWl6aHd1ZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/OJZZsbgcYvSSz5yA7K/giphy.gif" alt="Explosión de corazones" width="220" height="220" />
    </div>

    <p class="dev-text">Desarrollado por AnthZz Berrocal</p>
  </div>

  <script>
    let input = '';
    const correctKey = '10/11/23';
    let nombreYo = 'AnthZz Berrocal';
    let nombreElla = 'Yorchi';

    function addDigit(digit) {
      if (input.length < 8) {
        input += digit;
        updateDisplay();
      }
    }

    function clearInput() {
      input = '';
      updateDisplay();
    }

    function updateDisplay() {
      document.getElementById('display').textContent = input;
    }

    function submitKey() {
      if (input === correctKey) {
        document.getElementById('lockScreen').style.display = 'none';
        document.getElementById('mainContainer').style.display = 'block';
        typeWriter();
        createHearts();
      } else {
        alert('❌ Fecha incorrecta. Recuerda: 10/11/23');
        clearInput();
      }
    }

    // Abrir/cerrar menú
    function toggleMenu() {
      const menu = document.getElementById('menu');
      menu.classList.toggle('open');
    }

    // Actualizar nombres en la carta
    function actualizarNombres() {
      nombreYo = document.getElementById('nombreYo').value || 'AnthZz Berrocal';
      nombreElla = document.getElementById('nombreElla').value || 'Yorchi';
      if (document.getElementById('letter').textContent) {
        typeWriter(); // Vuelve a escribir con los nuevos nombres
      }
    }

    // Mensaje de amor
    function getMessage() {
      return `Mi amor ${nombreElla},

Hoy quiero que sepas, con cada latido de mi corazón,
que eres la persona más hermosa, dulce y especial
que he tenido la fortuna de conocer.

Desde que llegaste a mi vida, todo tiene más color,
más sentido, más magia. Tus risas son mi melodía favorita,
tu mirada, mi refugio, y tu amor, mi mayor bendición.

Cada día contigo es un regalo que agradezco profundamente.
No hay palabras suficientes para describir lo que siento,
pero si pudiera dibujarlo, sería un cielo lleno de estrellas,
un jardín infinito de flores, y un océano de paz.

Gracias por ser tú, por amarme como soy,
por entenderme sin necesidad de palabras,
por abrazarme incluso cuando no lo merezco.

Te amo más de lo que las palabras pueden decir,
más de lo que el tiempo puede medir,
más de lo que el universo puede contener.

Siempre serás mi hogar, mi sueño, mi razón.

Con todo mi amor,
${nombreYo} 💖`;
    }

    // Efecto de escritura
    function typeWriter() {
      const letterElement = document.getElementById('letter');
      letterElement.textContent = '';
      let i = 0;
      const message = getMessage();
      const speed = 35;

      function type() {
        if (i < message.length) {
          letterElement.textContent += message.charAt(i);
          i++;
          setTimeout(type, speed);
        } else {
          letterElement.style.opacity = 1;
        }
      }

      letterElement.style.opacity = 0;
      setTimeout(type, 300);
    }

    // Corazones flotando
    function createHearts() {
      const hearts = ['❤️', '💖', '💕', '💓', '💗', '💞', '💘'];
      setInterval(() => {
        const heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
        heart.style.left = Math.random() * 90 + 5 + 'vw';
        heart.style.animationDuration = (Math.random() * 6 + 10) + 's';
        document.body.appendChild(heart);

        setTimeout(() => heart.remove(), 15000);
      }, 2000);
    }
  </script>
</body>
</html>
