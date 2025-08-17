import React, { useState, useEffect } from "react";
import { MapContainer, TileLayer, Marker, Popup } from "react-leaflet";
import "leaflet/dist/leaflet.css";
import L from "leaflet";

// Fix default marker icon issue with React-Leaflet
delete L.Icon.Default.prototype._getIconUrl;
L.Icon.Default.mergeOptions({
  iconRetinaUrl: "https://unpkg.com/leaflet@1.7.1/dist/images/marker-icon-2x.png",
  iconUrl: "https://unpkg.com/leaflet@1.7.1/dist/images/marker-icon.png",
  shadowUrl: "https://unpkg.com/leaflet@1.7.1/dist/images/marker-shadow.png",
});

const App = () => {
  const [currentImageIndex, setCurrentImageIndex] = useState(0);
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [isVisible, setIsVisible] = useState({});

  const services = [
    { name: "Corte Clásico", price: "S/25", description: "Estilo tradicional con líneas precisas", image: "https://placehold.co/400x300/8B4513/FFFFFF?text=Corte+Cl%C3%A1sico" },
    { name: "Corte Moderno", price: "S/30", description: "Tendencias actuales con diseño personalizado", image: "https://placehold.co/400x300/2F4F4F/FFFFFF?text=Corte+Moderno" },
    { name: "Afeitado Premium", price: "S/35", description: "Afeitado con toallas calientes y productos premium", image: "https://placehold.co/400x300/DC143C/FFFFFF?text=Afeitado+Premium" },
    { name: "Ondulaciones", price: "S/40", description: "Definición de ondas con técnicas profesionales", image: "https://placehold.co/400x300/4169E1/FFFFFF?text=Ondulaciones" },
    { name: "Pintado de Cabello", price: "S/50", description: "Coloración profesional con productos premium", image: "https://placehold.co/400x300/9932CC/FFFFFF?text=Pintado+Cabello" },
    { name: "Tratamiento Capilar", price: "S/45", description: "Nutrición profunda para cabello dañado", image: "https://placehold.co/400x300/228B22/FFFFFF?text=Tratamiento+Capilar" },
    { name: "Tratamiento Facial", price: "S/40", description: "Limpieza profunda y cuidado de la piel", image: "https://placehold.co/400x300/FF69B4/FFFFFF?text=Tratamiento+Facial" },
    { name: "Barba Estilizada", price: "S/35", description: "Diseño y mantenimiento de barba profesional", image: "https://placehold.co/400x300/8B0000/FFFFFF?text=Barba+Estilizada" }
  ];

  const galleryImages = [
    "https://placehold.co/300x300/8B4513/FFFFFF?text=Estilo+1",
    "https://placehold.co/300x300/2F4F4F/FFFFFF?text=Estilo+2",
    "https://placehold.co/300x300/DC143C/FFFFFF?text=Estilo+3",
    "https://placehold.co/300x300/4169E1/FFFFFF?text=Estilo+4",
    "https://placehold.co/300x300/9932CC/FFFFFF?text=Estilo+5",
    "https://placehold.co/300x300/228B22/FFFFFF?text=Estilo+6",
    "https://placehold.co/300x300/FF69B4/FFFFFF?text=Estilo+7",
    "https://placehold.co/300x300/8B0000/FFFFFF?text=Estilo+8",
    "https://placehold.co/300x300/4682B4/FFFFFF?text=Estilo+9",
    "https://placehold.co/300x300/2E8B57/FFFFFF?text=Estilo+10",
    "https://placehold.co/300x300/CD5C5C/FFFFFF?text=Estilo+11",
    "https://placehold.co/300x300/4B0082/FFFFFF?text=Estilo+12"
  ];

  const testimonials = [
    { name: "Carlos M.", text: "La mejor barbería de la ciudad. Atención impecable y resultados excepcionales.", rating: 5 },
    { name: "Andrés R.", text: "Siempre que vengo salgo con un corte perfecto. Recomendado al 100%.", rating: 5 },
    { name: "Javier L.", text: "El trato personalizado y la calidad de los productos son incomparables.", rating: 5 }
  ];

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentImageIndex((prev) => (prev + 1) % galleryImages.length);
    }, 3000);
    return () => clearInterval(interval);
  }, [galleryImages.length]);

  useEffect(() => {
    const handleMouseMove = (e) => {
      setMousePosition({ x: e.clientX, y: e.clientY });
    };
    window.addEventListener("mousemove", handleMouseMove);
    return () => window.removeEventListener("mousemove", handleMouseMove);
  }, []);

  useEffect(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          setIsVisible(prev => ({ ...prev, [entry.target.id]: entry.isIntersecting }));
        });
      },
      { threshold: 0.1 }
    );

    document.querySelectorAll('.animate-on-scroll').forEach(el => {
      observer.observe(el);
    });

    return () => observer.disconnect();
  }, []);

  const handleWhatsAppClick = () => {
    const message = `*Reserva en La Magia del Barbero*\n\nHola, quiero reservar un servicio. Por favor indícame disponibilidad.`;
    window.open(`https://wa.me/977355999?text=${encodeURIComponent(message)}`, '_blank');
  };

  const mapPosition = [12.0432, -77.0282]; // Approximate coordinates for Jirón Alfonso Ugarte, Lima

  return (
    <div className="min-h-screen bg-black text-white overflow-x-hidden">
      {/* Animated Background Elements */}
      <div 
        className="fixed w-96 h-96 bg-gradient-to-r from-red-500 to-yellow-500 rounded-full filter blur-3xl opacity-20 -z-10 transition-all duration-1000"
        style={{
          left: mousePosition.x - 192,
          top: mousePosition.y - 192,
        }}
      ></div>
      <div 
        className="fixed w-80 h-80 bg-gradient-to-r from-blue-500 to-purple-500 rounded-full filter blur-3xl opacity-20 -z-10 transition-all duration-1500"
        style={{
          left: mousePosition.x - 300,
          top: mousePosition.y + 100,
        }}
      ></div>

      {/* Header */}
      <header className="relative bg-gradient-to-r from-red-900 via-black to-red-900 border-b-4 border-amber-500">
        <div className="absolute inset-0 bg-black opacity-50"></div>
        <div className="relative container mx-auto px-6 py-8">
          <div className="flex flex-col md:flex-row justify-between items-center">
            <div className="text-center md:text-left mb-6 md:mb-0">
              <h1 className="text-5xl md:text-7xl font-bold bg-gradient-to-r from-amber-400 via-yellow-300 to-amber-400 bg-clip-text text-transparent mb-2 animate-pulse">
                LA MAGIA DEL BARBERO
              </h1>
              <p className="text-xl md:text-2xl text-amber-300 font-semibold">Barber Shop Premium</p>
            </div>
            <div className="text-center md:text-right">
              <div className="bg-black bg-opacity-50 p-4 rounded-lg border border-amber-500">
                <p className="text-lg"><span className="text-amber-400">📞</span> <strong>977 355 999</strong></p>
                <p className="text-lg"><span className="text-amber-400">📞</span> <strong>931 538 059</strong></p>
                <p className="text-lg mt-2"><span className="text-amber-400">📍</span> <strong>Jirón Alfonso Ugarte 3er piso</strong></p>
              </div>
            </div>
          </div>
        </div>

        {/* Navigation */}
        <nav className="bg-black bg-opacity-70 sticky top-0 z-50">
          <div className="container mx-auto px-6">
            <div className="flex justify-center space-x-8 py-4">
              {['Inicio', 'Servicios', 'Galería', 'Promociones', 'Ubicación', 'Contacto'].map((item) => (
                <a
                  key={item}
                  href={`#${item.toLowerCase()}`}
                  className="text-lg font-semibold text-amber-300 hover:text-white transition duration-300 hover:scale-110 relative group"
                >
                  {item}
                  <span className="absolute -bottom-1 left-0 w-0 h-0.5 bg-amber-400 transition-all duration-300 group-hover:w-full"></span>
                </a>
              ))}
            </div>
          </div>
        </nav>
      </header>

      {/* Hero Section */}
      <section id="inicio" className="relative h-screen flex items-center justify-center overflow-hidden">
        <div className="absolute inset-0 bg-gradient-to-b from-transparent to-black"></div>
        <div 
          className="absolute inset-0 bg-cover bg-center filter blur-sm scale-110"
          style={{
            backgroundImage: `url(https://placehold.co/1920x1080/1a1a1a/FFFFFF?text=Barber+Shop+Interior)`
          }}
        ></div>
        <div className="relative z-10 text-center px-6">
          <h2 className="text-6xl md:text-8xl font-bold mb-6 text-transparent bg-clip-text bg-gradient-to-r from-amber-400 to-red-500 animate-bounce">
            BIENVENIDO
          </h2>
          <p className="text-2xl md:text-4xl mb-8 text-white leading-relaxed max-w-4xl">
            Transformamos tu estilo con la <span className="text-amber-400 font-bold">magia</span> de un verdadero barbero profesional
          </p>
          <button
            onClick={handleWhatsAppClick}
            className="bg-gradient-to-r from-amber-500 to-red-600 text-black font-bold text-2xl px-12 py-4 rounded-full hover:from-amber-400 hover:to-red-500 transform hover:scale-105 transition-all duration-300 shadow-2xl hover:shadow-amber-500/50"
          >
            RESERVAR AHORA
          </button>
        </div>
        
        {/* Floating Elements */}
        <div className="absolute top-20 left-10 animate-bounce text-amber-400 text-4xl">✂️</div>
        <div className="absolute top-40 right-20 animate-pulse text-red-400 text-5xl">💈</div>
        <div className="absolute bottom-20 left-20 animate-bounce text-yellow-400 text-3xl">🪒</div>
        <div className="absolute bottom-40 right-10 animate-pulse text-amber-300 text-4xl">🧴</div>
      </section>

      {/* Services Section */}
      <section id="servicios" className="py-20 bg-gradient-to-b from-black to-gray-900">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="servicios-title">
            NUESTROS SERVICIOS
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
            {services.map((service, index) => (
              <div
                key={index}
                className={`bg-gradient-to-b from-gray-800 to-gray-900 p-6 rounded-xl border border-amber-500/30 hover:border-amber-400 transition-all duration-500 transform hover:scale-105 hover:shadow-2xl hover:shadow-amber-500/20 animate-on-scroll`}
                style={{ animationDelay: `${index * 0.1}s` }}
                id={`service-${index}`}
              >
                <img
                  src={service.image}
                  alt={service.name}
                  className="w-full h-48 object-cover rounded-lg mb-4 shadow-lg"
                />
                <h3 className="text-2xl font-bold text-amber-400 mb-2">{service.name}</h3>
                <p className="text-gray-300 mb-3">{service.description}</p>
                <div className="flex justify-between items-center">
                  <span className="text-xl font-bold text-white">{service.price}</span>
                  <button className="bg-amber-500 text-black px-4 py-2 rounded-full font-bold hover:bg-amber-400 transition duration-300">
                    Reservar
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Gallery Section */}
      <section id="galería" className="py-20 bg-black">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="galeria-title">
            GALERÍA DE ESTILOS
          </h2>
          <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
            {galleryImages.map((image, index) => (
              <div
                key={index}
                className="relative group overflow-hidden rounded-lg hover:scale-105 transition-transform duration-300 animate-on-scroll"
                style={{ animationDelay: `${index * 0.05}s` }}
                id={`gallery-${index}`}
              >
                <img
                  src={image}
                  alt={`Estilo ${index + 1}`}
                  className="w-full h-48 object-cover"
                />
                <div className="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-60 transition-all duration-300 flex items-center justify-center">
                  <span className="text-white opacity-0 group-hover:opacity-100 transform translate-y-4 group-hover:translate-y-0 transition-all duration-300 font-bold">
                    Ver estilo
                  </span>
                </div>
              </div>
            ))}
          </div>
          
          {/* Image Carousel */}
          <div className="mt-16 bg-gradient-to-r from-gray-900 to-black p-8 rounded-2xl border border-amber-500/30">
            <h3 className="text-3xl font-bold text-center mb-8 text-amber-400">Estilo Destacado</h3>
            <div className="relative h-96">
              <img
                src={galleryImages[currentImageIndex]}
                alt="Estilo destacado"
                className="w-full h-full object-cover rounded-xl shadow-2xl"
              />
              <div className="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-2">
                {galleryImages.map((_, index) => (
                  <button
                    key={index}
                    className={`w-3 h-3 rounded-full transition-all duration-300 ${
                      index === currentImageIndex ? 'bg-amber-400' : 'bg-gray-600'
                    }`}
                    onClick={() => setCurrentImageIndex(index)}
                  />
                ))}
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Promotions Section */}
      <section id="promociones" className="py-20 bg-gradient-to-b from-gray-900 to-black">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="promociones-title">
            PROMOCIONES
          </h2>
          <div className="max-w-4xl mx-auto">
            <div className="bg-gradient-to-r from-amber-900/50 to-red-900/50 p-12 rounded-2xl border-4 border-amber-500 text-center relative overflow-hidden animate-on-scroll" id="promotion-card">
              <div className="absolute inset-0 bg-gradient-to-r from-amber-400/10 to-red-500/10 animate-pulse"></div>
              <h3 className="text-4xl font-bold mb-6 text-white">PROGRAMA DE LEALTAD</h3>
              <div className="text-6xl font-bold text-amber-400 mb-6">4 + 1 GRATIS</div>
              <p className="text-xl mb-8 text-gray-200">
                Acumula tus cortes y el <strong className="text-amber-400">quinto corte es completamente gratis</strong> después de 4 visitas
              </p>
              <div className="grid grid-cols-5 gap-4 mb-8">
                {[1, 2, 3, 4, 5].map((num) => (
                  <div
                    key={num}
                    className={`w-16 h-16 rounded-full border-4 flex items-center justify-center text-2xl font-bold transition-all duration-500 ${
                      num <= 4 ? 'border-amber-400 bg-amber-400 text-black' : 'border-gray-600 bg-gray-800 text-gray-400'
                    }`}
                  >
                    {num}
                  </div>
                ))}
              </div>
              <p className="text-lg text-amber-300 italic">¡Tu fidelidad tiene recompensa!</p>
            </div>
          </div>
        </div>
      </section>

      {/* Testimonials Section */}
      <section className="py-20 bg-black">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="testimonials-title">
            LO QUE DICEN NUESTROS CLIENTES
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
            {testimonials.map((testimonial, index) => (
              <div
                key={index}
                className="bg-gradient-to-b from-gray-800 to-gray-900 p-8 rounded-xl border border-amber-500/30 animate-on-scroll"
                style={{ animationDelay: `${index * 0.1}s` }}
                id={`testimonial-${index}`}
              >
                <div className="flex mb-4">
                  {[...Array(testimonial.rating)].map((_, i) => (
                    <span key={i} className="text-amber-400 text-2xl">★</span>
                  ))}
                </div>
                <p className="text-lg mb-6 text-gray-200 italic">"{testimonial.text}"</p>
                <p className="font-bold text-amber-400">- {testimonial.name}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Location Section */}
      <section id="ubicación" className="py-20 bg-gradient-to-b from-black to-gray-900">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="location-title">
            UBICACIÓN
          </h2>
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
            <div className="animate-on-scroll" id="location-info">
              <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-8 rounded-2xl border border-amber-500/30">
                <h3 className="text-3xl font-bold mb-6 text-amber-400">Visítanos</h3>
                <div className="space-y-4 text-lg">
                  <p><span className="text-amber-400 font-bold">📍 Dirección:</span> Jirón Alfonso Ugarte 3er piso, Lima</p>
                  <p><span className="text-amber-400 font-bold">📞 Teléfonos:</span> 977 355 999 / 931 538 059</p>
                  <p><span className="text-amber-400 font-bold">🕒 Horario:</span> Lunes a Sábado: 9:00 AM - 8:00 PM</p>
                  <p><span className="text-amber-400 font-bold">🕒 Horario:</span> Domingo: 10:00 AM - 6:00 PM</p>
                </div>
                <button
                  onClick={handleWhatsAppClick}
                  className="mt-6 w-full bg-gradient-to-r from-green-500 to-green-600 text-white font-bold text-xl py-4 rounded-full hover:from-green-400 hover:to-green-500 transition-all duration-300 transform hover:scale-105"
                >
                  📱 RESERVAR POR WHATSAPP
                </button>
              </div>
            </div>
            <div className="animate-on-scroll" id="map-container">
              <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-6 rounded-2xl border border-amber-500/30 h-96">
                <MapContainer
                  center={mapPosition}
                  zoom={17}
                  style={{ height: '100%', width: '100%' }}
                  className="rounded-xl"
                >
                  <TileLayer
                    url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
                    attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
                  />
                  <Marker position={mapPosition}>
                    <Popup>
                      <div className="text-center">
                        <h3 className="font-bold text-lg">La Magia del Barbero</h3>
                        <p>Jirón Alfonso Ugarte 3er piso</p>
                        <p>Tel: 977 355 999</p>
                      </div>
                    </Popup>
                  </Marker>
                </MapContainer>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contacto" className="py-20 bg-black">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="contact-title">
            CONTACTO
          </h2>
          <div className="max-w-4xl mx-auto">
            <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-12 rounded-2xl border border-amber-500 animate-on-scroll" id="contact-form">
              <div className="text-center mb-8">
                <h3 className="text-3xl font-bold mb-4 text-amber-400">¿Listo para tu transformación?</h3>
                <p className="text-xl text-gray-300">Contáctanos para reservar tu cita</p>
              </div>
              <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div className="space-y-6">
                  <div className="flex items-center space-x-4">
                    <div className="w-12 h-12 bg-amber-500 rounded-full flex items-center justify-center">
                      <span className="text-black text-2xl">📞</span>
                    </div>
                    <div>
                      <p className="font-bold text-amber-400">Teléfonos</p>
                      <p className="text-white">977 355 999</p>
                      <p className="text-white">931 538 059</p>
                    </div>
                  </div>
                  <div className="flex items-center space-x-4">
                    <div className="w-12 h-12 bg-amber-500 rounded-full flex items-center justify-center">
                      <span className="text-black text-2xl">📍</span>
                    </div>
                    <div>
                      <p className="font-bold text-amber-400">Dirección</p>
                      <p className="text-white">Jirón Alfonso Ugarte 3er piso</p>
                      <p className="text-white">Lima, Perú</p>
                    </div>
                  </div>
                  <div className="flex items-center space-x-4">
                    <div className="w-12 h-12 bg-amber-500 rounded-full flex items-center justify-center">
                      <span className="text-black text-2xl">🕒</span>
                    </div>
                    <div>
                      <p className="font-bold text-amber-400">Horario</p>
                      <p className="text-white">Lunes a Sábado: 9:00 AM - 8:00 PM</p>
                      <p className="text-white">Domingo: 10:00 AM - 6:00 PM</p>
                    </div>
                  </div>
                </div>
                <div className="space-y-6">
                  <button
                    onClick={handleWhatsAppClick}
                    className="w-full bg-green-500 hover:bg-green-600 text-white font-bold text-2xl py-6 rounded-xl transition-all duration-300 transform hover:scale-105 flex items-center justify-center space-x-3"
                  >
                    <span>📱</span>
                    <span>RESERVAR POR WHATSAPP</span>
                  </button>
                  <div className="bg-black bg-opacity-50 p-6 rounded-xl">
                    <p className="text-center text-gray-300">
                      Al hacer clic en WhatsApp, se abrirá un mensaje preescrito para facilitar tu reserva.
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-gradient-to-r from-red-900 via-black to-red-900 border-t-4 border-amber-500 py-12">
        <div className="container mx-auto px-6">
          <div className="grid grid-cols-1 md:grid-cols-3 gap-8 text-center md:text-left">
            <div>
              <h3 className="text-3xl font-bold bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent mb-4">
                LA MAGIA DEL BARBERO
              </h3>
              <p className="text-gray-300 mb-4">
                Donde el arte del corte se convierte en magia. 
                Profesionalismo, estilo y atención personalizada.
              </p>
              <p className="text-amber-400 font-bold">Propietario: Kennedy, Jr. Juan F. Ramos</p>
            </div>
            <div>
              <h4 className="text-xl font-bold text-amber-400 mb-4">Contacto</h4>
              <div className="space-y-2 text-gray-300">
                <p>📞 977 355 999</p>
                <p>📞 931 538 059</p>
                <p>📍 Jirón Alfonso Ugarte 3er piso</p>
                <p>🕒 Lunes a Sábado: 9:00 AM - 8:00 PM</p>
                <p>🕒 Domingo: 10:00 AM - 6:00 PM</p>
              </div>
            </div>
            <div>
              <h4 className="text-xl font-bold text-amber-400 mb-4">Redes</h4>
              <div className="space-y-4">
                <button
                  onClick={handleWhatsAppClick}
                  className="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-full transition-all duration-300 flex items-center justify-center space-x-2"
                >
                  <span>📱</span>
                  <span>WhatsApp</span>
                </button>
                <div className="bg-black bg-opacity-50 p-4 rounded-lg">
                  <p className="text-sm text-gray-400">
                    Síguenos en nuestras redes sociales para ver nuestros últimos estilos y promociones.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div className="border-t border-amber-500/30 mt-8 pt-8 text-center">
            <p className="text-gray-400">
              © 2024 La Magia del Barbero Barber Shop. Todos los derechos reservados.
            </p>
            <p className="text-amber-400 font-bold mt-2">
              Diseñado por AnthZz Berrocal
            </p>
          </div>
        </div>
      </footer>

      {/* Scroll to Top Button */}
      <button
        onClick={() => window.scrollTo({ top: 0, behavior: 'smooth' })}
        className="fixed bottom-8 right-8 bg-amber-500 text-black p-4 rounded-full shadow-2xl hover:bg-amber-400 transition-all duration-300 transform hover:scale-110 z-50"
      >
        <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M5 15l7-7 7 7" />
        </svg>
      </button>

      <style jsx>{`
        @keyframes float {
          0%, 100% { transform: translateY(0px); }
          50% { transform: translateY(-20px); }
        }
        .animate-float {
          animation: float 3s ease-in-out infinite;
        }
        
        @keyframes shine {
          0% { background-position: -200px; }
          100% { background-position: 200px; }
        }
        .animate-shine {
          background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
          background-size: 200px;
          animation: shine 2s infinite;
        }
        
        .animate-on-scroll {
          opacity: 0;
          transform: translateY(30px);
          transition: all 0.8s ease-out;
        }
        
        .animate-on-scroll.visible {
          opacity: 1;
          transform: translateY(0);
        }
      `}</style>
    </div>
  );
};

export default App;
