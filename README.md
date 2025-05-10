<!DOCTYPE html><html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sistema de Hacker Oficial - BerMatModZ</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=VT323&family=Russo+One&display=swap');
    body {
      background: #000000;
      color: #00ff00;
      font-family: 'VT323', monospace;
      margin: 0;
      padding: 0;
      overflow-x: hidden;
    }.container {
  max-width: 1200px;
  margin: auto;
  padding: 20px;
  background-color: #0d0d0d;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0, 255, 0, 0.8);
}

.header {
  background-color: #0f0f0f;
  padding: 30px;
  border-radius: 15px;
  margin-bottom: 30px;
  box-shadow: 0 0 25px rgba(0, 255, 0, 0.9);
}

.header h1 {
  font-size: 48px;
  color: #00ff00;
  margin: 0;
  text-transform: uppercase;
  font-family: 'Russo One', sans-serif;
}

.info-box {
  background-color: #111;
  border: 2px solid #00ff00;
  padding: 30px;
  margin-bottom: 30px;
  border-radius: 15px;
  box-shadow: 0 0 25px rgba(0, 255, 0, 0.8);
  font-family: 'Orbitron', sans-serif;
}

.info-box h2 {
  font-size: 36px;
  color: #00ff00;
  text-transform: uppercase;
}

.info-box p {
  font-size: 20px;
  color: #ffffff;
  margin: 15px 0;
}

.info-box a {
  color: #00ffff;
  text-decoration: none;
  font-weight: bold;
  font-size: 22px;
  transition: color 0.3s ease;
}

.info-box a:hover {
  color: #32cd32;
}

.form-container {
  background-color: #111;
  border: 2px solid #00ff00;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 25px rgba(0, 255, 0, 0.9);
  margin-bottom: 30px;
  text-align: center;
  font-family: 'VT323', monospace;
}

.form-container input[type="text"], .form-container input[type="password"] {
  padding: 15px;
  width: 90%;
  font-size: 22px;
  border: 2px solid #00ff00;
  background-color: #000;
  color: #00ff00;
  border-radius: 10px;
  margin-bottom: 20px;
}

.form-container input[type="submit"] {
  background-color: #00ff00;
  color: #000000;
  border: none;
  padding: 15px 30px;
  font-size: 24px;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.form-container input[type="submit"]:hover {
  background-color: #32cd32;
}

.vip-access {
  background-color: #101010;
  border: 2px solid #00ff00;
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 0 25px rgba(0, 255, 0, 0.9);
  margin-bottom: 30px;
  text-align: center;
  font-family: 'Orbitron', sans-serif;
}

.vip-access h3 {
  font-size: 32px;
  color: #00ff00;
  margin-bottom: 20px;
  font-family: 'Russo One', sans-serif;
}

.vip-access p {
  font-size: 22px;
  color: #ff0000;
  margin-bottom: 20px;
}

.vip-access a {
  color: #00ffff;
  font-weight: bold;
  text-decoration: none;
  font-size: 24px;
}

.vip-access a:hover {
  color: #32cd32;
}

  </style>
</head>
<body>  <div class="container"><div class="header">
  <h1>Sistema de Hacker Oficial por AnthZz Berrocal</h1>
</div>

<div class="info-box">
  <h2>Información de BerMatModZ</h2>
  <p><strong>Creador:</strong> AnthZz Berrocal</p>
  <p><strong>Redes Sociales:</strong></p>
  <p><a href="https://wa.me/937556459" target="_blank">WhatsApp</a></p>
  <p><a href="https://www.instagram.com/anthzzberrocal" target="_blank">Instagram</a></p>
  <p><a href="https://github.com/anthzzberrocal" target="_blank">GitHub</a></p>
</div>

<div class="vip-access">
  <h3>Acceso al Servicio VIP</h3>
  <p>Para ingresar a este sistema VIP, introduce el código de acceso que te brindó mi creador AnthZz Berrocal.</p>
  <form onsubmit="mostrarAdvertencia(event)">
    <input type="password" placeholder="Ingresa tu código de acceso" required><br><br>
    <input type="submit" value="Acceder">
  </form>
  <p>¿No tienes el código? <a href="https://wa.me/937556459?text=Quiero%20comprar%20tu%20servicio%20de%20hackers" target="_blank">Haz clic aquí para comprar</a></p>
</div>

<div class="form-container">
  <h3>Ingrese el número de teléfono para hackear:</h3>
  <form onsubmit="mostrarAdvertencia(event)">
    <input type="text" id="phone" placeholder="Número de teléfono" required><br><br>
    <input type="submit" value="Hackear">
  </form>
</div>

<div id="advertencia" class="warning-message" style="display: none;">
  <p>Aún no has ingresado el código de acceso para obtener toda la información del dicho número. Debes ingresar el código de acceso que compraste para continuar.</p>
  <a href="https://wa.me/937556459?text=Quiero%20comprar%20tu%20servicio%20de%20hackers" target="_blank">Haz clic aquí para comprar</a>
</div>

  </div></body>
</html>
