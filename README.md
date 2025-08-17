```jsx
import React, { useState, useEffect, useRef } from "react";

const App = () => {
  const [currentImageIndex, setCurrentImageIndex] = useState(0);
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [isVisible, setIsVisible] = useState({});
  const [activeTestimonial, setActiveTestimonial] = useState(0);
  const [scrollY, setScrollY] = useState(0);
  const heroRef = useRef(null);

  const services = [
    { 
      name: "Corte Clásico", 
      description: "Dominamos el arte del corte tradicional con líneas precisas y definidas. Nuestra técnica ha sido perfeccionada a lo largo de años, combinando la elegancia del pasado con la precisión del presente. Ideal para quienes valoran la tradición y el estilo atemporal.",
      image: "https://placehold.co/600x400/8B4513/FFFFFF?text=Corte+Cl%C3%A1sico",
      features: ["Líneas precisas", "Estilo atemporal", "Técnica tradicional", "Definición perfecta"]
    },
    { 
      name: "Corte Moderno", 
      description: "Innovación y tendencia en cada corte. Nuestros estilistas están constantemente actualizados con las últimas tendencias internacionales, creando looks únicos que reflejan tu personalidad. Desde fades extremos hasta diseños personalizados, tu cabello será nuestra obra de arte.",
      image: "https://placehold.co/600x400/2F4F4F/FFFFFF?text=Corte+Moderno",
      features: ["Tendencias actuales", "Diseño personalizado", "Innovación", "Estilo único"]
    },
    { 
      name: "Afeitado Premium", 
      description: "Una experiencia de lujo para tu rostro. Nuestro afeitado premium incluye toallas calientes, productos premium de alta gama y técnicas milenarias que dejan tu piel suave y rejuvenecida. Más que un afeitado, es un ritual de bienestar masculino.",
      image: "https://placehold.co/600x400/DC143C/FFFFFF?text=Afeitado+Premium",
      features: ["Toallas calientes", "Productos premium", "Técnicas milenarias", "Piel rejuvenecida"]
    },
    { 
      name: "Ondulaciones", 
      description: "Domina el arte de las ondas perfectas. Nuestra técnica especializada define y realza tus ondas naturales con productos específicos y herramientas profesionales. Cada sesión es una transformación que realza tu textura capilar única.",
      image: "https://placehold.co/600x400/4169E1/FFFFFF?text=Ondulaciones",
      features: ["Definición de ondas", "Técnica especializada", "Productos específicos", "Textura realzada"]
    },
    { 
      name: "Pintado de Cabello", 
      description: "Transformación cromática con productos de alta gama. Desde sutiles reflejos hasta cambios radicales, nuestro proceso garantiza resultados duraderos y saludables. Utilizamos solo productos que nutren mientras transforman.",
      image: "https://placehold.co/600x400/9932CC/FFFFFF?text=Pintado+Cabello",
      features: ["Productos de alta gama", "Resultados duraderos", "Nutrición capilar", "Transformación segura"]
    },
    { 
      name: "Tratamiento Capilar", 
      description: "Terapia intensiva para cabello dañado. Nuestros tratamientos profesionales restauran la salud de tu cabello con keratinas, aceites esenciales y técnicas avanzadas. Ideal para cabellos castigados por tintes, calor o condiciones ambientales.",
      image: "https://placehold.co/600x400/228B22/FFFFFF?text=Tratamiento+Capilar",
      features: ["Restauración profunda", "Keratinas premium", "Aceites esenciales", "Salud capilar"]
    },
    { 
      name: "Tratamiento Facial", 
      description: "Ritual de limpieza profunda y rejuvenecimiento. Nuestro tratamiento facial premium combina exfoliación, extracción de impurezas y mascarillas nutritivas para dejar tu rostro renovado. La piel masculina merece cuidados especiales.",
      image: "https://placehold.co/600x400/FF69B4/FFFFFF?text=Tratamiento+Facial",
      features: ["Limpieza profunda", "Exfoliación", "Rejuvenecimiento", "Piel renovada"]
    },
    { 
      name: "Barba Estilizada", 
      description: "Escultura facial con precisión milimétrica. Diseñamos y mantenemos tu barba según tu estructura facial, creando armonía y definición. Desde barbas completas hasta diseños geométricos, tu rostro será nuestra obra maestra.",
      image: "https://placehold.co/600x400/8B0000/FFFFFF?text=Barba+Estilizada",
      features: ["Diseño personalizado", "Precisión milimétrica", "Armonía facial", "Mantenimiento profesional"]
    },
    {
      name: "Corte Infantil",
      description: "Experiencia amigable para los más pequeños. Nuestro espacio infantil y paciencia infinita hacen que el primer corte sea una experiencia positiva. Técnicas especiales para cabellos sensibles y atención personalizada.",
      image: "https://placehold.co/600x400/4682B4/FFFFFF?text=Corte+Infantil",
      features: ["Espacio infantil", "Técnicas especiales", "Paciencia infinita", "Experiencia positiva"]
    },
    {
      name: "Peinado de Eventos",
      description: "Estilo impecable para ocasiones especiales. Desde bodas hasta presentaciones importantes, creamos looks duraderos y fotogénicos que complementan tu atuendo y ocasión. Nuestra atención al detalle garantiza perfección.",
      image: "https://placehold.co/600x400/2E8B57/FFFFFF?text=Peinado+Eventos",
      features: ["Ocasiones especiales", "Looks duraderos", "Atención al detalle", "Estilo fotogénico"]
    }
  ];

  const galleryImages = [
    "https://placehold.co/600x600/8B4513/FFFFFF?text=Estilo+1",
    "https://placehold.co/600x600/2F4F4F/FFFFFF?text=Estilo+2",
    "https://placehold.co/600x600/DC143C/FFFFFF?text=Estilo+3",
    "https://placehold.co/600x600/4169E1/FFFFFF?text=Estilo+4",
    "https://placehold.co/600x600/9932CC/FFFFFF?text=Estilo+5",
    "https://placehold.co/600x600/228B22/FFFFFF?text=Estilo+6",
    "https://placehold.co/600x600/FF69B4/FFFFFF?text=Estilo+7",
    "https://placehold.co/600x600/8B0000/FFFFFF?text=Estilo+8",
    "https://placehold.co/600x600/4682B4/FFFFFF?text=Estilo+9",
    "https://placehold.co/600x600/2E8B57/FFFFFF?text=Estilo+10",
    "https://placehold.co/600x600/CD5C5C/FFFFFF?text=Estilo+11",
    "https://placehold.co/600x600/4B0082/FFFFFF?text=Estilo+12",
    "https://placehold.co/600x600/800080/FFFFFF?text=Estilo+13",
    "https://placehold.co/600x600/008080/FFFFFF?text=Estilo+14",
    "https://placehold.co/600x600/FF4500/FFFFFF?text=Estilo+15",
    "https://placehold.co/600x600/9ACD32/FFFFFF?text=Estilo+16"
  ];

  const testimonials = [
    { 
      name: "Carlos Mendoza", 
      text: "Desde que descubrí La Magia del Barbero, mi vida ha cambiado. No solo por el corte impecable, sino por la experiencia completa. Kennedy y su equipo no solo cortan cabello, crean confianza. Cada visita es un ritual que me prepara para enfrentar cualquier desafío con estilo.",
      rating: 5,
      image: "https://placehold.co/100x100/8B4513/FFFFFF?text=CM"
    },
    { 
      name: "Andrés Ramírez", 
      text: "He estado en muchas barberías, pero ninguna se compara con el nivel de excelencia aquí. La atención al detalle, la calidad de los productos y el ambiente exclusivo hacen de cada visita una experiencia de lujo. Mi barba nunca ha lucido mejor, y el tratamiento facial ha rejuvenecido mi rostro.",
      rating: 5,
      image: "https://placehold.co/100x100/2F4F4F/FFFFFF?text=AR"
    },
    { 
      name: "Javier López", 
      text: "Como hombre de negocios, mi apariencia es crucial. La Magia del Barbero entiende esto perfectamente. Sus cortes modernos me hacen destacar en reuniones importantes, y su programa de lealtad demuestra su compromiso con la excelencia continua. No es solo una barbería, es una inversión en mi imagen profesional.",
      rating: 5,
      image: "https://placehold.co/100x100/DC143C/FFFFFF?text=JL"
    },
    {
      name: "Roberto Torres",
      text: "Lo que más admiro es su dominio del corte clásico. En un mundo de tendencias fugaces, mantener viva la tradición con tanta maestría es admirable. Cada línea, cada detalle, refleja años de experiencia y pasión por el oficio. Realmente son artistas del cabello.",
      rating: 5,
      image: "https://placehold.co/100x100/4169E1/FFFFFF?text=RT"
    }
  ];

  const team = [
    {
      name: "Kennedy, Jr. Juan F. Ramos",
      role: "Fundador & Master Barber",
      image: "https://placehold.co/300x300/000000/FFFFFF?text=Kennedy",
      bio: "Con más de 15 años de experiencia, Kennedy es un verdadero maestro del oficio. Su pasión por la barbería comenzó en la barbería de su abuelo y ha evolucionado en una filosofía de vida. Cree que un buen corte no solo transforma la apariencia, sino la confianza y la actitud.",
      specialties: ["Corte Clásico", "Barba Estilizada", "Consultoría de Imagen"]
    },
    {
      name: "Alejandro Martínez",
      role: "Stylist Senior",
      image: "https://placehold.co/300x300/333333/FFFFFF?text=Alejandro",
      bio: "Especialista en tendencias modernas y diseños innovadores. Alejandro ha representado al Perú en competencias internacionales de barbería, trayendo técnicas avanzadas y perspectivas globales a nuestro equipo. Su enfoque es crear estilos únicos que reflejen la personalidad de cada cliente.",
      specialties: ["Corte Moderno", "Diseños Personalizados", "Peinado de Eventos"]
    },
    {
      name: "Daniel Rojas",
      role: "Tratamientos Capilares",
      image: "https://placehold.co/300x300/444444/FFFFFF?text=Daniel",
      bio: "Experto en salud capilar y tratamientos regenerativos. Daniel combina conocimientos científicos con técnicas tradicionales para ofrecer soluciones efectivas para todo tipo de problemas capilares. Su enfoque holístico considera factores internos y externos que afectan la salud del cabello.",
      specialties: ["Tratamiento Capilar", "Pintado de Cabello", "Asesoría Capilar"]
    },
    {
      name: "Sofía Castro",
      role: "Skin & Beard Specialist",
      image: "https://placehold.co/300x300/555555/FFFFFF?text=Sofía",
      bio: "Especialista en cuidado facial masculino y barbas. Sofía ha estudiado las necesidades específicas de la piel masculina y ha desarrollado protocolos que combinan eficacia con lujo. Cree que el cuidado facial es esencial para una apariencia impecable.",
      specialties: ["Tratamiento Facial", "Afeitado Premium", "Barba Estilizada"]
    }
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
    
    const handleScroll = () => {
      setScrollY(window.scrollY);
    };

    window.addEventListener("mousemove", handleMouseMove);
    window.addEventListener("scroll", handleScroll);
    
    return () => {
      window.removeEventListener("mousemove", handleMouseMove);
      window.removeEventListener("scroll", handleScroll);
    };
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

  const mapPosition = [12.0432, -77.0282];

  // 3D Title Component
  const AnimatedTitle = () => {
    const title = "LA MAGIA DEL BARBERO";
    return (
      <div className="relative">
        <div className="absolute inset-0 bg-gradient-to-r from-red-500 to-yellow-500 rounded-lg blur-lg opacity-50 animate-pulse"></div>
        <h1 className="relative text-5xl md:text-7xl font-bold bg-gradient-to-r from-amber-400 via-yellow-300 to-amber-400 bg-clip-text text-transparent mb-2 animate-bounce tracking-wide">
          {title.split('').map((char, index) => (
            <span
              key={index}
              className="inline-block"
              style={{
                transform: `rotateX(${Math.sin((index + scrollY * 0.01) * 0.5) * 10}deg)`,
                transition: 'transform 0.1s ease-out'
              }}
            >
              {char === ' ' ? '\u00A0' : char}
            </span>
          ))}
        </h1>
      </div>
    );
  };

  return (
    <div className="min-h-screen bg-black text-white overflow-x-hidden">
      {/* Animated Background Elements */}
      <div 
        className="fixed w-96 h-96 bg-gradient-to-r from-red-500 to-yellow-500 rounded-full filter blur-3xl opacity-20 -z-10 transition-all duration-1000 pointer-events-none"
        style={{
          left: mousePosition.x - 192,
          top: mousePosition.y - 192,
          transform: `translate(${Math.sin(scrollY * 0.001) * 20}px, ${Math.cos(scrollY * 0.001) * 20}px)`
        }}
      ></div>
      <div 
        className="fixed w-80 h-80 bg-gradient-to-r from-blue-500 to-purple-500 rounded-full filter blur-3xl opacity-20 -z-10 transition-all duration-1500 pointer-events-none"
        style={{
          left: mousePosition.x - 300,
          top: mousePosition.y + 100,
          transform: `translate(${Math.cos(scrollY * 0.001) * 20}px, ${Math.sin(scrollY * 0.001) * 20}px)`
        }}
      ></div>
      <div 
        className="fixed w-72 h-72 bg-gradient-to-r from-green-500 to-teal-500 rounded-full filter blur-3xl opacity-15 -z-10 transition-all duration-2000 pointer-events-none"
        style={{
          right: mousePosition.x - 100,
          bottom: mousePosition.y - 50,
          transform: `translate(${Math.sin(scrollY * 0.002) * 15}px, ${Math.cos(scrollY * 0.002) * 15}px)`
        }}
      ></div>

      {/* Header */}
      <header className="relative bg-gradient-to-r from-red-900 via-black to-red-900 border-b-4 border-amber-500 shadow-2xl">
        <div className="absolute inset-0 bg-black opacity-50"></div>
        <div className="relative container mx-auto px-6 py-8">
          <div className="flex flex-col md:flex-row justify-between items-center">
            <div className="text-center md:text-left mb-6 md:mb-0">
              <AnimatedTitle />
              <p className="text-xl md:text-2xl text-amber-300 font-semibold animate-pulse">Barber Shop Premium & Academy</p>
            </div>
            <div className="text-center md:text-right">
              <div className="bg-black bg-opacity-50 p-4 rounded-lg border border-amber-500 backdrop-blur-sm">
                <p className="text-lg flex items-center"><span className="text-amber-400 mr-2">📞</span> <strong>977 355 999</strong></p>
                <p className="text-lg flex items-center"><span className="text-amber-400 mr-2">📞</span> <strong>931 538 059</strong></p>
                <p className="text-lg mt-2 flex items-center"><span className="text-amber-400 mr-2">📍</span> <strong>Jirón Alfonso Ugarte 3er piso</strong></p>
              </div>
            </div>
          </div>
        </div>

        {/* Navigation */}
        <nav className="bg-black bg-opacity-70 sticky top-0 z-50 backdrop-blur-md">
          <div className="container mx-auto px-6">
            <div className="flex justify-center space-x-8 py-4">
              {['Inicio', 'Servicios', 'Galería', 'Equipo', 'Promociones', 'Ubicación', 'Contacto'].map((item) => (
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
      <section id="inicio" ref={heroRef} className="relative h-screen flex items-center justify-center overflow-hidden">
        <div className="absolute inset-0 bg-gradient-to-b from-transparent to-black"></div>
        <div 
          className="absolute inset-0 bg-cover bg-center filter blur-sm scale-110 transition-transform duration-10000"
          style={{
            backgroundImage: `url(https://placehold.co/1920x1080/1a1a1a/FFFFFF?text=Barber+Shop+Interior)`,
            transform: `scale(${1 + scrollY * 0.0002})`
          }}
        ></div>
        <div className="absolute inset-0 bg-black opacity-60"></div>
        <div className="relative z-10 text-center px-6 transform transition-transform duration-1000" style={{ transform: `translateY(${scrollY * 0.5}px)` }}>
          <h2 className="text-6xl md:text-8xl font-bold mb-6 text-transparent bg-clip-text bg-gradient-to-r from-amber-400 to-red-500 animate-bounce">
            BIENVENIDO
          </h2>
          <p className="text-2xl md:text-4xl mb-8 text-white leading-relaxed max-w-4xl transform transition-transform duration-1000" style={{ transform: `translateX(${scrollY * 0.3}px)` }}>
            Transformamos tu estilo con la <span className="text-amber-400 font-bold">magia</span> de un verdadero barbero profesional
          </p>
          <div className="flex flex-col sm:flex-row justify-center gap-6 mt-8">
            <button
              onClick={handleWhatsAppClick}
              className="bg-gradient-to-r from-amber-500 to-red-600 text-black font-bold text-2xl px-12 py-4 rounded-full hover:from-amber-400 hover:to-red-500 transform hover:scale-105 transition-all duration-300 shadow-2xl hover:shadow-amber-500/50"
            >
              RESERVAR AHORA
            </button>
            <a
              href="#servicios"
              className="bg-transparent border-2 border-amber-400 text-amber-400 font-bold text-2xl px-12 py-4 rounded-full hover:bg-amber-400 hover:text-black transform hover:scale-105 transition-all duration-300"
            >
              CONOCE MÁS
            </a>
          </div>
        </div>
        
        {/* Floating Elements */}
        <div className="absolute top-20 left-10 animate-bounce text-amber-400 text-4xl" style={{ animationDelay: '0s' }}>✂️</div>
        <div className="absolute top-40 right-20 animate-pulse text-red-400 text-5xl" style={{ animationDelay: '1s' }}>💈</div>
        <div className="absolute bottom-20 left-20 animate-bounce text-yellow-400 text-3xl" style={{ animationDelay: '2s' }}>🪒</div>
        <div className="absolute bottom-40 right-10 animate-pulse text-amber-300 text-4xl" style={{ animationDelay: '3s' }}>🧴</div>
        <div className="absolute top-1/2 left-10 animate-spin text-amber-500 text-2xl" style={{ animationDuration: '3s' }}>🌀</div>
        <div className="absolute top-1/3 right-1/4 animate-bounce text-red-500 text-3xl" style={{ animationDelay: '0.5s' }}>✨</div>
      </section>

      {/* Services Section */}
      <section id="servicios" className="py-20 bg-gradient-to-b from-black to-gray-900">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="servicios-title">
            NUESTROS SERVICIOS
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            {services.map((service, index) => (
              <div
                key={index}
                className={`bg-gradient-to-b from-gray-800 to-gray-900 p-6 rounded-xl border border-amber-500/30 hover:border-amber-400 transition-all duration-500 transform hover:scale-105 hover:shadow-2xl hover:shadow-amber-500/20 animate-on-scroll backdrop-blur-sm`}
                style={{ animationDelay: `${index * 0.1}s` }}
                id={`service-${index}`}
              >
                <img
                  src={service.image}
                  alt={service.name}
                  className="w-full h-48 object-cover rounded-lg mb-4 shadow-lg hover:scale-105 transition-transform duration-300"
                />
                <h3 className="text-2xl font-bold text-amber-400 mb-3">{service.name}</h3>
                <p className="text-gray-300 mb-4 leading-relaxed">{service.description}</p>
                <div className="space-y-2 mb-6">
                  {service.features.map((feature, i) => (
                    <div key={i} className="flex items-center text-sm text-gray-400">
                      <span className="text-amber-400 mr-2">✓</span>
                      {feature}
                    </div>
                  ))}
                </div>
                <button className="w-full bg-amber-500 text-black py-3 rounded-full font-bold hover:bg-amber-400 transition duration-300 transform hover:scale-105">
                  Reservar
                </button>
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
                className="relative group overflow-hidden rounded-lg hover:scale-105 transition-transform duration-300 animate-on-scroll cursor-pointer"
                style={{ animationDelay: `${index * 0.05}s` }}
                id={`gallery-${index}`}
                onClick={() => setCurrentImageIndex(index)}
              >
                <img
                  src={image}
                  alt={`Estilo ${index + 1}`}
                  className="w-full h-48 object-cover transition-transform duration-500 group-hover:scale-110"
                />
                <div className="absolute inset-0 bg-gradient-to-t from-black via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <div className="absolute bottom-4 left-4 text-white opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                  <p className="font-bold">Estilo {index + 1}</p>
                </div>
              </div>
            ))}
          </div>
          
          {/* Image Carousel */}
          <div className="mt-16 bg-gradient-to-r from-gray-900 to-black p-8 rounded-2xl border border-amber-500/30 backdrop-blur-sm">
            <h3 className="text-3xl font-bold text-center mb-8 text-amber-400">Estilo Destacado</h3>
            <div className="relative h-96 overflow-hidden rounded-xl">
              <img
                src={galleryImages[currentImageIndex]}
                alt="Estilo destacado"
                className="w-full h-full object-cover rounded-xl shadow-2xl transition-opacity duration-1000"
              />
              <div className="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"></div>
              <div className="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-2">
                {galleryImages.map((_, index) => (
                  <button
                    key={index}
                    className={`w-3 h-3 rounded-full transition-all duration-300 ${
                      index === currentImageIndex ? 'bg-amber-400' : 'bg-gray-600 hover:bg-gray-500'
                    }`}
                    onClick={() => setCurrentImageIndex(index)}
                  />
                ))}
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Team Section */}
      <section id="equipo" className="py-20 bg-gradient-to-b from-gray-900 to-black">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="team-title">
            NUESTRO EQUIPO
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
            {team.map((member, index) => (
              <div
                key={index}
                className="bg-gradient-to-b from-gray-800 to-gray-900 p-6 rounded-xl border border-amber-500/30 hover:border-amber-400 transition-all duration-500 transform hover:scale-105 hover:shadow-2xl hover:shadow-amber-500/20 animate-on-scroll backdrop-blur-sm"
                style={{ animationDelay: `${index * 0.1}s` }}
                id={`team-${index}`}
              >
                <img
                  src={member.image}
                  alt={member.name}
                  className="w-32 h-32 rounded-full mx-auto mb-4 border-4 border-amber-400 object-cover"
                />
                <h3 className="text-xl font-bold text-amber-400 text-center mb-1">{member.name}</h3>
                <p className="text-center text-gray-300 mb-4">{member.role}</p>
                <p className="text-sm text-gray-400 mb-4 leading-relaxed">{member.bio}</p>
                <div className="space-y-1">
                  <p className="text-amber-400 font-bold text-sm">Especialidades:</p>
                  {member.specialties.map((specialty, i) => (
                    <p key={i} className="text-xs text-gray-400 flex items-center">
                      <span className="text-amber-400 mr-1">•</span>
                      {specialty}
                    </p>
                  ))}
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Promotions Section */}
      <section id="promociones" className="py-20 bg-gradient-to-b from-black to-gray-900">
        <div className="container mx-auto px-6">
          <h2 className="text-5xl font-bold text-center mb-16 bg-gradient-to-r from-amber-400 to-red-500 bg-clip-text text-transparent animate-on-scroll" id="promociones-title">
            PROGRAMA DE LEALTAD
          </h2>
          <div className="max-w-4xl mx-auto">
            <div className="bg-gradient-to-r from-amber-900/50 to-red-900/50 p-12 rounded-2xl border-4 border-amber-500 text-center relative overflow-hidden animate-on-scroll backdrop-blur-sm" id="promotion-card">
              <div className="absolute inset-0 bg-gradient-to-r from-amber-400/10 to-red-500/10 animate-pulse"></div>
              <h3 className="text-4xl font-bold mb-6 text-white">ACUMULA Y GANA</h3>
              <div className="text-6xl font-bold text-amber-400 mb-6">4 + 1 GRATIS</div>
              <p className="text-xl mb-8 text-gray-200">
                Acumula tus visitas y el <strong className="text-amber-400">quinto servicio es completamente gratis</strong> después de 4 visitas
              </p>
              <div className="grid grid-cols-5 gap-4 mb-8">
                {[1, 2, 3, 4, 5].map((num) => (
                  <div
                    key={num}
                    className={`w-16 h-16 rounded-full border-4 flex items-center justify-center text-2xl font-bold transition-all duration-500 cursor-pointer ${
                      num <= 4 ? 'border-amber-400 bg-amber-400 text-black hover:bg-amber-300' : 'border-gray-600 bg-gray-800 text-gray-400 hover:bg-gray-700'
                    }`}
                  >
                    {num}
                  </div>
                ))}
              </div>
              <p className="text-lg text-amber-300 italic mb-4">¡Tu fidelidad tiene recompensa!</p>
              <p className="text-gray-300 text-sm">Aplica para todos nuestros servicios. Presenta tu tarjeta de fidelidad en cada visita.</p>
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
          <div className="relative max-w-4xl mx-auto">
            <div className="overflow-hidden">
              <div 
                className="flex transition-transform duration-500 ease-in-out"
                style={{ transform: `translateX(-${activeTestimonial * 100}%)` }}
              >
                {testimonials.map((testimonial, index) => (
                  <div key={index} className="w-full flex-shrink-0 px-4">
                    <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-8 rounded-xl border border-amber-500/30 animate-on-scroll backdrop-blur-sm">
                      <div className="flex mb-4">
                        {[...Array(testimonial.rating)].map((_, i) => (
                          <span key={i} className="text-amber-400 text-2xl">★</span>
                        ))}
                      </div>
                      <p className="text-lg mb-6 text-gray-200 italic">"{testimonial.text}"</p>
                      <div className="flex items-center">
                        <img src={testimonial.image} alt={testimonial.name} className="w-12 h-12 rounded-full mr-4" />
                        <p className="font-bold text-amber-400">- {testimonial.name}</p>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
            <div className="flex justify-center mt-8 space-x-2">
              {testimonials.map((_, index) => (
                <button
                  key={index}
                  className={`w-3 h-3 rounded-full transition-all duration-300 ${
                    index === activeTestimonial ? 'bg-amber-400' : 'bg-gray-600 hover:bg-gray-500'
                  }`}
                  onClick={() => setActiveTestimonial(index)}
                />
              ))}
            </div>
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
              <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-8 rounded-2xl border border-amber-500/30 backdrop-blur-sm">
                <h3 className="text-3xl font-bold mb-6 text-amber-400">Visítanos</h3>
                <div className="space-y-4 text-lg">
                  <p className="flex items-start"><span className="text-amber-400 font-bold mr-2 mt-1">📍</span> <span><strong>Dirección:</strong> Jirón Alfonso Ugarte 3er piso, Lima</span></p>
                  <p className="flex items-center"><span className="text-amber-400 font-bold mr-2">📞</span> <span><strong>Teléfonos:</strong> 977 355 999 / 931 538 059</span></p>
                  <p className="flex items-center"><span className="text-amber-400 font-bold mr-2">🕒</span> <span><strong>Horario:</strong> Lunes a Sábado: 9:00 AM - 8:00 PM</span></p>
                  <p className="flex items-center"><span className="text-amber-400 font-bold mr-2">🕒</span> <span><strong>Horario:</strong> Domingo: 10:00 AM - 6:00 PM</span></p>
                  <p className="flex items-start"><span className="text-amber-400 font-bold mr-2 mt-1">🅿️</span> <span><strong>Estacionamiento:</strong> Disponible en el edificio</span></p>
                  <p className="flex items-start"><span className="text-amber-400 font-bold mr-2 mt-1">♿</span> <span><strong>Accesibilidad:</strong> Acceso para personas con discapacidad</span></p>
                </div>
                <button
                  onClick={handleWhatsAppClick}
                  className="mt-6 w-full bg-gradient-to-r from-green-500 to-green-600 text-white font-bold text-xl py-4 rounded-full hover:from-green-400 hover:to-green-500 transition-all duration-300 transform hover:scale-105 flex items-center justify-center space-x-2"
                >
                  <span>📱</span>
                  <span>RESERVAR POR WHATSAPP</span>
                </button>
              </div>
            </div>
            <div className="animate-on-scroll" id="map-container">
              <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-6 rounded-2xl border border-amber-500/30 h-96 backdrop-blur-sm">
                <div className="w-full h-full bg-gradient-to-br from-gray-700 to-gray-900 rounded-xl flex items-center justify-center">
                  <div className="text-center">
                    <div className="text-6xl mb-4">📍</div>
                    <p className="text-white text-xl mb-4">Ubicación de la Barbería</p>
                    <a 
                      href="https://maps.app.goo.gl/rmAqpfnZKrg94J3y8" 
                      target="_blank" 
                      rel="noopener noreferrer"
                      className="bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-full font-bold inline-block transition duration-300 transform hover:scale-105"
                    >
                      VER EN GOOGLE MAPS
                    </a>
                  </div>
                </div>
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
            <div className="bg-gradient-to-b from-gray-800 to-gray-900 p-12 rounded-2xl border border-amber-500 animate-on-scroll backdrop-blur-sm" id="contact-form">
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
                  <div className="flex items-center space-x-4">
                    <div className="w-12 h-12 bg-amber-500 rounded-full flex items-center justify-center">
                      <span className="text-black text-2xl">📧</span>
                    </div>
                    <div>
                      <p className="font-bold text-amber-400">Email</p>
                      <p className="text-white">info@lamagiadelbarbero.com</p>
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
                  <div className="bg-amber-500 bg-opacity-20 p-4 rounded-lg">
                    <p className="text-center text-amber-300 text-sm">
                      <strong>Consejo:</strong> Para una mejor atención, reserva con anticipación, especialmente los fines de semana.
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
              <p className="text-gray-300 mb-4 leading-relaxed">
                Donde el arte del corte se convierte en magia. Profesionalismo, estilo y atención personalizada desde 2010. 
                Más que una barbería, somos una comunidad de hombres que valoran la excelencia en cada detalle.
              </p>
              <p className="text-amber-400 font-bold">Propietario: Kennedy, Jr. Juan F. Ramos</p>
            </div>
            <div>
              <h4 className="text-xl font-bold text-amber-400 mb-4">Contacto</h4>
              <div className="space-y-2 text-gray-300">
                <p className="flex items-center justify-center md:justify-start"><span className="text-amber-400 mr-2">📞</span> 977 355 999</p>
                <p className="flex items-center justify-center md:justify-start"><span className="text-amber-400 mr-2">📞</span> 931 538 059</p>
                <p className="flex items-center justify-center md:justify-start"><span className="text-amber-400 mr-2">📧</span> info@lamagiadelbarbero.com</p>
                <p className="flex items-center justify-center md:justify-start"><span className="text-amber-400 mr-2">📍</span> Jirón Alfonso Ugarte 3er piso</p>
                <p className="flex items-center justify-center md:justify-start"><span className="text-amber-400 mr-2">🕒</span> Lunes a Sábado: 9:00 AM - 8:00 PM</p>
                <p className="flex items-center justify-center md:justify-start"><span className="text-amber-400 mr-2">🕒</span> Domingo: 10:00 AM - 6:00 PM</p>
              </div>
            </div>
            <div>
              <h4 className="text-xl font-bold text-amber-400 mb-4">Redes Sociales</h4>
              <div className="space-y-4">
                <button
                  onClick={handleWhatsAppClick}
                  className="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-full transition-all duration-300 flex items-center justify-center space-x-2 transform hover:scale-105"
                >
                  <span>📱</span>
                  <span>WhatsApp</span>
                </button>
                <div className="bg-black bg-opacity-50 p-4 rounded-lg">
                  <p className="text-sm text-gray-400">
                    Síguenos en Instagram y Facebook para ver nuestros últimos estilos, promociones y consejos de cuidado masculino.
                  </p>
                </div>
                <div className="flex justify-center space-x-4 pt-2">
                  <div className="w-10 h-10 bg-blue-600 rounded-full flex items-center justify-center hover:bg-blue-700 transition duration-300 transform hover:scale-110 cursor-pointer">
                    <span>f</span>
                  </div>
                  <div className="w-10 h-10 bg-purple-600 rounded-full flex items-center justify-center hover:bg-purple-700 transition duration-300 transform hover:scale-110 cursor-pointer">
                    <span>i</span>
                  </div>
                  <div className="w-10 h-10 bg-red-600 rounded-full flex items-center justify-center hover:bg-red-700 transition duration-300 transform hover:scale-110 cursor-pointer">
                    <span>t</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div className="border-t border-amber-500/30 mt-8 pt-8 text-center">
            <p className="text-gray-400">
              © 2020 La Magia del Barbero Barber Shop . Todos los derechos reservados.
            </p>
            <p className="text-amber-400 font-bold mt-2">
              Diseñado  por AnthZz Berrocal | Experiencia de Desarrollo Web Avanzada
            </p>
          </div>
        </div>
      </footer>

      {/* Scroll to Top Button */}
      <button
        onClick={() => window.scrollTo({ top: 0, behavior: 'smooth' })}
        className="fixed bottom-8 right-8 bg-amber-500 text-black p-4 rounded-full shadow-2xl hover:bg-amber-400 transition-all duration-300 transform hover:scale-110 z-50 animate-pulse"
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
        
        .backdrop-blur-sm {
          backdrop-filter: blur(4px);
        }
        
        @media (max-width: 768px) {
          .text-5xl {
            font-size: 2.5rem;
          }
          .text-7xl {
            font-size: 3.5rem;
          }
          .text-6xl {
            font-size: 3rem;
          }
        }
      `}</style>
    </div>
  );
};

export default App;
```
