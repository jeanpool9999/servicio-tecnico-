<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JDPROJECTECH - Servicios Tecnológicos Profesionales</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;500;600;700&family=Exo+2:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-dark: #0a0e1a;
            --secondary-dark: #1a1f35;
            --accent-blue: #00d4ff;
            --accent-cyan: #00fff0;
            --tech-gold: #ffd700;
            --text-primary: #ffffff;
            --text-secondary: #b0c4de;
            --border-glow: rgba(0, 212, 255, 0.3);
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background: var(--primary-dark);
            color: var(--text-primary);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Fondo animado de circuitos */
        .circuit-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.1;
        }

        .circuit-line {
            position: absolute;
            background: linear-gradient(90deg, transparent, var(--accent-blue), transparent);
            animation: dataFlow 4s infinite linear;
        }

        .circuit-line:nth-child(1) {
            top: 20%;
            left: -100px;
            width: 200px;
            height: 2px;
            animation-delay: 0s;
        }

        .circuit-line:nth-child(2) {
            top: 40%;
            right: -100px;
            width: 150px;
            height: 1px;
            animation-delay: 1s;
            animation-direction: reverse;
        }

        .circuit-line:nth-child(3) {
            top: 60%;
            left: -80px;
            width: 180px;
            height: 2px;
            animation-delay: 2s;
        }

        .circuit-line:nth-child(4) {
            top: 80%;
            right: -120px;
            width: 160px;
            height: 1px;
            animation-delay: 3s;
            animation-direction: reverse;
        }

        .circuit-node {
            position: absolute;
            width: 6px;
            height: 6px;
            background: var(--accent-cyan);
            border-radius: 50%;
            box-shadow: 0 0 10px var(--accent-cyan);
            animation: pulse 2s infinite;
        }

        .circuit-node:nth-child(5) { top: 25%; left: 15%; animation-delay: 0.5s; }
        .circuit-node:nth-child(6) { top: 45%; right: 20%; animation-delay: 1.5s; }
        .circuit-node:nth-child(7) { top: 65%; left: 25%; animation-delay: 2.5s; }
        .circuit-node:nth-child(8) { top: 85%; right: 15%; animation-delay: 3.5s; }

        @keyframes dataFlow {
            0% { transform: translateX(-100px); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateX(calc(100vw + 100px)); opacity: 0; }
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(10, 14, 26, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-glow);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 5%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .logo {
            font-family: 'Orbitron', monospace;
            font-size: 1.8rem;
            font-weight: 900;
            background: linear-gradient(45deg, var(--accent-blue), var(--accent-cyan));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: var(--text-secondary);
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
            padding: 0.5rem 1rem;
        }

        .nav-links a:hover {
            color: var(--accent-cyan);
            text-shadow: 0 0 10px var(--accent-cyan);
        }

        .nav-links a::before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background: var(--accent-cyan);
            transition: all 0.3s ease;
            transform: translateX(-50%);
        }

        .nav-links a:hover::before {
            width: 100%;
        }

        .mobile-menu {
            display: none;
            font-size: 1.5rem;
            color: var(--accent-cyan);
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .hero-carousel {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .hero-slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: all 1s ease-in-out;
            background-size: cover;
            background-position: center;
        }

        .hero-slide.active {
            opacity: 0.3;
        }

        .hero-slide:nth-child(1) {
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1581092795360-fd1ca04f0952?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
        }

        .hero-slide:nth-child(2) {
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2071&q=80');
        }

        .hero-slide:nth-child(3) {
            background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1518709268805-4e9042af2176?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2025&q=80');
        }

        .hero-content {
            text-align: center;
            z-index: 10;
            max-width: 900px;
            padding: 0 2rem;
        }

        .hero-title {
            font-family: 'Orbitron', monospace;
            font-size: 4rem;
            font-weight: 900;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, var(--accent-blue), var(--text-primary), var(--accent-cyan));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
            opacity: 0;
            animation: slideInUp 1s ease-out 0.5s forwards;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            color: var(--text-secondary);
            margin-bottom: 2rem;
            opacity: 0;
            animation: slideInUp 1s ease-out 1s forwards;
        }

        .typing-text {
            font-size: 1.8rem;
            color: var(--accent-cyan);
            font-weight: 600;
            margin-bottom: 3rem;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .cta-buttons {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            flex-wrap: wrap;
            opacity: 0;
            animation: slideInUp 1s ease-out 1.5s forwards;
        }

        .cta-btn {
            padding: 1rem 2rem;
            background: linear-gradient(45deg, var(--accent-blue), var(--accent-cyan));
            color: var(--primary-dark);
            text-decoration: none;
            font-weight: 600;
            border-radius: 8px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .cta-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.6s ease;
        }

        .cta-btn:hover::before {
            left: 100%;
        }

        .cta-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.4);
        }

        .cta-btn.secondary {
            background: transparent;
            color: var(--accent-cyan);
            border: 2px solid var(--accent-cyan);
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Servicios Section */
        .services {
            padding: 8rem 5% 4rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            font-family: 'Orbitron', monospace;
            font-size: 3rem;
            text-align: center;
            margin-bottom: 3rem;
            background: linear-gradient(45deg, var(--accent-blue), var(--accent-cyan));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }

        .section-title.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-bottom: 4rem;
        }

        .service-card {
            background: linear-gradient(145deg, var(--secondary-dark), rgba(26, 31, 53, 0.8));
            border: 1px solid var(--border-glow);
            border-radius: 15px;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            opacity: 0;
            transform: translateY(50px);
        }

        .service-image {
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .service-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(0, 212, 255, 0.1), rgba(0, 255, 240, 0.1));
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .service-card:hover .service-image::after {
            opacity: 1;
        }

        .service-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(from 0deg, transparent, var(--accent-blue), transparent);
            animation: rotate 4s linear infinite;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .service-card:hover::before {
            opacity: 0.1;
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.2);
            border-color: var(--accent-cyan);
        }

        .service-icon {
            font-size: 3rem;
            color: var(--accent-cyan);
            margin-bottom: 1rem;
            transition: all 0.3s ease;
        }

        .service-card:hover .service-icon {
            transform: scale(1.1);
            text-shadow: 0 0 20px var(--accent-cyan);
        }

        .service-title {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            color: var(--text-primary);
        }

        .service-description {
            color: var(--text-secondary);
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }

        .service-price {
            font-size: 2rem;
            font-weight: 700;
            color: var(--tech-gold);
            font-family: 'Orbitron', monospace;
        }

        @keyframes rotate {
            100% { transform: rotate(360deg); }
        }

        /* Why Choose Us Section */
        .why-choose {
            padding: 4rem 5%;
            background: linear-gradient(135deg, var(--secondary-dark), var(--primary-dark));
            margin: 4rem 0;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .feature-item {
            text-align: center;
            padding: 2rem;
            transition: all 0.3s ease;
            opacity: 0;
            transform: translateY(30px);
        }

        .feature-item.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .feature-icon {
            font-size: 3rem;
            color: var(--accent-blue);
            margin-bottom: 1rem;
            transition: all 0.3s ease;
        }

        .feature-item:hover .feature-icon {
            transform: scale(1.2) rotate(5deg);
            color: var(--accent-cyan);
        }

        .feature-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }

        .feature-description {
            color: var(--text-secondary);
            font-size: 0.95rem;
        }

        /* Gallery Section */
        .gallery {
            padding: 4rem 5%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .gallery-item {
            position: relative;
            height: 250px;
            border-radius: 10px;
            overflow: hidden;
            background: var(--secondary-dark);
            border: 1px solid var(--border-glow);
            transition: all 0.3s ease;
            opacity: 0;
            transform: scale(0.9);
            background-size: cover;
            background-position: center;
        }

        .gallery-item:nth-child(1) {
            background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1596496050827-8299e0220306?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2053&q=80');
        }

        .gallery-item:nth-child(2) {
            background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2071&q=80');
        }

        .gallery-item:nth-child(3) {
            background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1544197150-b99a580bb7a8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
        }

        .gallery-item:nth-child(4) {
            background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1518709268805-4e9042af2176?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2025&q=80');
        }

        .gallery-item:nth-child(5) {
            background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1581092795360-fd1ca04f0952?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
        }

        .gallery-item:nth-child(6) {
            background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1591799264318-7e6ef8ddb7ea?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2574&q=80');
        }

        .gallery-item.visible {
            opacity: 1;
            transform: scale(1);
        }

        .gallery-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, var(--accent-blue), var(--accent-cyan));
            opacity: 0.1;
            transition: opacity 0.3s ease;
        }

        .gallery-item:hover {
            transform: scale(1.05);
            box-shadow: 0 15px 30px rgba(0, 212, 255, 0.3);
        }

        .gallery-item:hover::before {
            opacity: 0.2;
        }

        .gallery-content {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            padding: 1.5rem;
            background: linear-gradient(transparent, rgba(10, 14, 26, 0.9));
        }

        .gallery-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .gallery-description {
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        /* Contact Section */
        .contact {
            padding: 4rem 5%;
            background: var(--secondary-dark);
        }

        .contact-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .contact-info h3 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--accent-cyan);
        }

        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 1.5rem;
            padding: 1rem;
            background: rgba(0, 212, 255, 0.05);
            border-radius: 8px;
            border-left: 3px solid var(--accent-cyan);
        }

        .contact-item i {
            font-size: 1.5rem;
            color: var(--accent-cyan);
            margin-right: 1rem;
            width: 30px;
        }

        .map-container {
            height: 300px;
            background: var(--primary-dark);
            border-radius: 10px;
            border: 1px solid var(--border-glow);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-secondary);
        }

        /* Footer */
        footer {
            background: var(--primary-dark);
            padding: 2rem 5%;
            border-top: 1px solid var(--border-glow);
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-logo {
            font-family: 'Orbitron', monospace;
            font-size: 1.5rem;
            font-weight: 900;
            background: linear-gradient(45deg, var(--accent-blue), var(--accent-cyan));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1rem;
        }

        .footer-text {
            color: var(--text-secondary);
            margin-bottom: 1rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .social-links a {
            color: var(--accent-cyan);
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            color: var(--accent-blue);
            transform: translateY(-3px);
        }

        .copyright {
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-top: 1rem;
            padding-top: 1rem;
            border-top: 1px solid rgba(176, 196, 222, 0.1);
        }

        /* WhatsApp Float Button */
        .whatsapp-float {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #25d366, #128c7e);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.8rem;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4);
            transition: all 0.3s ease;
            animation: pulse 2s infinite;
        }

        .whatsapp-float:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 30px rgba(37, 211, 102, 0.6);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .mobile-menu {
                display: block;
            }

            .nav-links {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                background: rgba(10, 14, 26, 0.98);
                flex-direction: column;
                padding: 2rem;
                border-top: 1px solid var(--border-glow);
            }

            .nav-links.active {
                display: flex;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .hero-subtitle {
                font-size: 1.2rem;
            }

            .typing-text {
                font-size: 1.3rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .services-grid {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .service-card {
                padding: 1.5rem;
            }

            .features-grid {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .contact-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .gallery-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 480px) {
            .hero-title {
                font-size: 2rem;
            }

            .services-grid {
                grid-template-columns: 1fr;
            }

            .service-card {
                margin: 0 1rem;
            }

            nav {
                padding: 1rem 3%;
            }

            .services, .gallery, .contact {
                padding: 4rem 3%;
            }
        }
    </style>
</head>
<body>
    <!-- Fondo animado de circuitos -->
    <div class="circuit-bg">
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
        <div class="circuit-node"></div>
        <div class="circuit-node"></div>
        <div class="circuit-node"></div>
        <div class="circuit-node"></div>
    </div>

    <!-- Header -->
    <header>
        <nav>
            <div class="logo">JDPROJECTECH</div>
            <ul class="nav-links">
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#servicios">Servicios</a></li>
                <li><a href="#nosotros">Nosotros</a></li>
                <li><a href="#galeria">Galería</a></li>
                <li><a href="#contacto">Contacto</a></li>
            </ul>
            <div class="mobile-menu">
                <i class="fas fa-bars"></i>
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="inicio" class="hero">
        <div class="hero-carousel">
            <div class="hero-slide active"></div>
            <div class="hero-slide"></div>
            <div class="hero-slide"></div>
        </div>
        <div class="hero-content">
            <h1 class="hero-title">JDPROJECTECH</h1>
            <p class="hero-subtitle">Expertos en Tecnología y Soluciones Digitales</p>
            <div class="typing-text" id="typingText"></div>
            <div class="cta-buttons">
                <a href="#servicios" class="cta-btn">Ver Servicios</a>
                <a href="#contacto" class="cta-btn secondary">Contactar</a>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="servicios" class="services">
        <h2 class="section-title">Nuestros Servicios</h2>
        <div class="services-grid">
            <div class="service-card">
                <div class="service-image" style="background-image: url('https://images.unsplash.com/photo-1588508065123-287b28e013da?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2012&q=80'); height: 200px; background-size: cover; background-position: center; border-radius: 10px; margin-bottom: 1rem;"></div>
                <i class="fas fa-desktop service-icon"></i>
                <h3 class="service-title">Mantenimiento de PCs</h3>
                <p class="service-description">Limpieza profunda, optimización del sistema y mantenimiento preventivo para un rendimiento óptimo.</p>
                <div class="service-price">$10</div>
            </div>
            <div class="service-card">
                <div class="service-image" style="background-image: url('https://images.unsplash.com/photo-1597872200969-2b65d56bd16b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2000&q=80'); height: 200px; background-size: cover; background-position: center; border-radius: 10px; margin-bottom: 1rem;"></div>
                <i class="fas fa-hard-drive service-icon"></i>
                <h3 class="service-title">Formateo con Respaldo</h3>
                <p class="service-description">Formateo completo del sistema con respaldo seguro de todos tus datos importantes.</p>
                <div class="service-price">$15</div>
            </div>
            <div class="service-card">
                <div class="service-image" style="background-image: url('https://images.unsplash.com/photo-1558618666-fcd25c85cd64?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2071&q=80'); height: 200px; background-size: cover; background-position: center; border-radius: 10px; margin-bottom: 1rem;"></div>
                <i class="fas fa-video service-icon"></i>
                <h3 class="service-title">Instalación de Cámaras</h3>
                <p class="service-description">Sistemas de seguridad profesionales con cámaras HD y monitoreo remoto.</p>
                <div class="service-price">Desde $25</div>
            </div>
            <div class="service-card">
                <div class="service-image" style="background-image: url('https://images.unsplash.com/photo-1544197150-b99a580bb7a8?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80'); height: 200px; background-size: cover; background-position: center; border-radius: 10px; margin-bottom: 1rem;"></div>
                <i class="fas fa-network-wired service-icon"></i>
                <h3 class="service-title">Configuración de Redes</h3>
                <p class="service-description">Configuración profesional de redes empresariales y domésticas para máxima conectividad.</p>
                <div class="service-price">$20</div>
            </div>
            <div class="service-card">
                <div class="service-image" style="background-image: url('https://images.unsplash.com/photo-1612198188060-c7c2a3b66eae?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2012&q=80'); height: 200px; background-size: cover; background-position: center; border-radius: 10px; margin-bottom: 1rem;"></div>
                <i class="fas fa-print service-icon"></i>
                <h3 class="service-title">Reparación de Impresoras</h3>
                <p class="service-description">Diagnóstico y reparación de impresoras de todas las marcas y modelos.</p>
                <div class="service-price">Desde $12</div>
            </div>
            <div class="service-card">
                <div class="service-image" style="background-image: url('https://images.unsplash.com/photo-1518709268805-4e9042af2176?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2025&q=80'); height: 200px; background-size: cover; background-position: center; border-radius: 10px; margin-bottom: 1rem;"></div>
                <i class="fas fa-server service-icon"></i>
                <h3 class="service-title">Servidores</h3>
                <p class="service-description">Instalación, configuración y mantenimiento de servidores empresariales.</p>
                <div class="service-price">Desde $40</div>
            </div>
        </div>
    </section>

    <!-- Why Choose Us Section -->
    <section id="nosotros" class="why-choose">
        <h2 class="section-title">¿Por Qué Elegirnos?</h2>
        <!-- Team Image -->
        <div style="text-align: center; margin-bottom: 3rem;">
            <img src="https://images.unsplash.com/photo-1581092795360-fd1ca04f0952?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" 
                 alt="Nuestro equipo de trabajo" 
                 style="width: 100%; max-width: 800px; height: 300px; object-fit: cover; border-radius: 15px; border: 1px solid var(--border-glow); box-shadow: 0 10px 30px rgba(0, 212, 255, 0.2);">
        </div>
        <div class="features-grid">
            <div class="feature-item">
                <i class="fas fa-bolt feature-icon"></i>
                <h3 class="feature-title">Rapidez</h3>
                <p class="feature-description">Servicio técnico rápido y eficiente. Resolvemos tus problemas tecnológicos en el menor tiempo posible.</p>
            </div>
            <div class="feature-item">
                <i class="fas fa-shield-alt feature-icon"></i>
                <h3 class="feature-title">Garantía</h3>
                <p class="feature-description">Todos nuestros servicios incluyen garantía completa. Tu tranquilidad es nuestra prioridad.</p>
            </div>
            <div class="feature-item">
                <i class="fas fa-tools feature-icon"></i>
                <h3 class="feature-title">Equipos Modernos</h3>
                <p class="feature-description">Utilizamos herramientas y equipos de última generación para brindarte el mejor servicio.</p>
            </div>
            <div class="feature-item">
                <i class="fas fa-user-graduate feature-icon"></i>
                <h3 class="feature-title">Personal Capacitado</h3>
                <p class="feature-description">Técnicos certificados con amplia experiencia en el sector tecnológico.</p>
            </div>
            <div class="feature-item">
                <i class="fas fa-lock feature-icon"></i>
                <h3 class="feature-title">Seguridad</h3>
                <p class="feature-description">Máxima seguridad en el manejo de tus datos y equipos. Confidencialidad garantizada.</p>
            </div>
        </div>
    </section>

    <!-- Gallery Section -->
    <section id="galeria" class="gallery">
        <h2 class="section-title">Nuestro Trabajo</h2>
        <div class="gallery-grid">
            <div class="gallery-item">
                <div class="gallery-content">
                    <h3 class="gallery-title">Reparación de Equipos</h3>
                    <p class="gallery-description">Diagnóstico y reparación profesional de computadoras y laptops</p>
                </div>
            </div>
            <div class="gallery-item">
                <div class="gallery-content">
                    <h3 class="gallery-title">Sistemas de Seguridad</h3>
                    <p class="gallery-description">Instalación de cámaras de seguridad con monitoreo 24/7</p>
                </div>
            </div>
            <div class="gallery-item">
                <div class="gallery-content">
                    <h3 class="gallery-title">Redes Estructuradas</h3>
                    <p class="gallery-description">Configuración profesional de redes empresariales</p>
                </div>
            </div>
            <div class="gallery-item">
                <div class="gallery-content">
                    <h3 class="gallery-title">Sala de Servidores</h3>
                    <p class="gallery-description">Instalación y mantenimiento de centros de datos</p>
                </div>
            </div>
            <div class="gallery-item">
                <div class="gallery-content">
                    <h3 class="gallery-title">Taller Técnico</h3>
                    <p class="gallery-description">Espacio equipado con tecnología de vanguardia</p>
                </div>
            </div>
            <div class="gallery-item">
                <div class="gallery-content">
                    <h3 class="gallery-title">Componentes</h3>
                    <p class="gallery-description">Repuestos y componentes tecnológicos originales</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contacto" class="contact">
        <h2 class="section-title">Contáctanos</h2>
        <div class="contact-content">
            <div class="contact-info">
                <h3>Información de Contacto</h3>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <div>
                        <strong>Teléfono:</strong><br>
                        +593 99 123 4567
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <div>
                        <strong>Email:</strong><br>
                        info@tecnologysolucion.com
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <div>
                        <strong>Dirección:</strong><br>
                        Manta, Montecristi, Ecuador
                    </div>
                </div>
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <div>
                        <strong>Horarios:</strong><br>
                        Lun - Vie: 8:00 AM - 6:00 PM<br>
                        Sáb: 9:00 AM - 2:00 PM
                    </div>
                </div>
            </div>
            <div class="map-container">
                <div>
                    <i class="fas fa-map" style="font-size: 3rem; color: var(--accent-cyan); margin-bottom: 1rem;"></i>
                    <p>Mapa de Ubicación</p>
                    <p style="font-size: 0.9rem;">Manta, Montecristi, Ecuador</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-logo">JDPROJECTECH</div>
            <p class="footer-text">Expertos en tecnología y soluciones digitales</p>
            <div class="social-links">
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
            </div>
            <div class="copyright">
                <p>&copy; 2025 Tecnology Solución. Todos los derechos reservados.</p>
            </div>
        </div>
    </footer>

    <!-- WhatsApp Float Button -->
    <a href="https://wa.me/593962952717" class="whatsapp-float" target="_blank">
        <i class="fab fa-whatsapp"></i>
    </a>

    <script>
        // Typing animation
        const phrases = [
            "Tecnología que resuelve",
            "Tu sistema, en buenas manos",
            "Seguridad, conectividad y precisión",
            "Soluciones tecnológicas profesionales"
        ];
        
        let currentPhrase = 0;
        let currentChar = 0;
        let isDeleting = false;
        const typingElement = document.getElementById('typingText');
        
        function typeEffect() {
            const currentText = phrases[currentPhrase];
            
            if (isDeleting) {
                typingElement.textContent = currentText.substring(0, currentChar - 1);
                currentChar--;
            } else {
                typingElement.textContent = currentText.substring(0, currentChar + 1);
                currentChar++;
            }
            
            let typeSpeed = isDeleting ? 50 : 100;
            
            if (!isDeleting && currentChar === currentText.length) {
                typeSpeed = 2000;
                isDeleting = true;
            } else if (isDeleting && currentChar === 0) {
                isDeleting = false;
                currentPhrase = (currentPhrase + 1) % phrases.length;
                typeSpeed = 500;
            }
            
            setTimeout(typeEffect, typeSpeed);
        }
        
        // Start typing effect
        setTimeout(typeEffect, 2000);
        
        // Hero carousel
        const slides = document.querySelectorAll('.hero-slide');
        let currentSlide = 0;
        
        function nextSlide() {
            slides[currentSlide].classList.remove('active');
            currentSlide = (currentSlide + 1) % slides.length;
            slides[currentSlide].classList.add('active');
        }
        
        setInterval(nextSlide, 5000);
        
        // Smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
        
        // Mobile menu toggle
        const mobileMenu = document.querySelector('.mobile-menu');
        const navLinks = document.querySelector('.nav-links');
        
        mobileMenu.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            const icon = mobileMenu.querySelector('i');
            icon.classList.toggle('fa-bars');
            icon.classList.toggle('fa-times');
        });
        
        // Scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };
        
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);
        
        // Observe elements for animation
        document.querySelectorAll('.section-title, .service-card, .feature-item, .gallery-item').forEach(el => {
            observer.observe(el);
        });
        
        // Header scroll effect
        const header = document.querySelector('header');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 100) {
                header.style.background = 'rgba(10, 14, 26, 0.98)';
                header.style.backdropFilter = 'blur(20px)';
            } else {
                header.style.background = 'rgba(10, 14, 26, 0.95)';
                header.style.backdropFilter = 'blur(10px)';
            }
        });
        
        // Add more circuit lines dynamically
        function createCircuitLine() {
            const circuitBg = document.querySelector('.circuit-bg');
            const line = document.createElement('div');
            line.className = 'circuit-line';
            
            // Random positioning
            const isVertical = Math.random() > 0.5;
            if (isVertical) {
                line.style.height = Math.random() * 200 + 100 + 'px';
                line.style.width = '2px';
                line.style.left = Math.random() * 100 + '%';
                line.style.top = '-100px';
                line.style.background = 'linear-gradient(180deg, transparent, var(--accent-cyan), transparent)';
            } else {
                line.style.width = Math.random() * 200 + 100 + 'px';
                line.style.height = '1px';
                line.style.top = Math.random() * 100 + '%';
                line.style.left = '-100px';
            }
            
            line.style.animationDelay = Math.random() * 4 + 's';
            circuitBg.appendChild(line);
            
            // Remove line after animation
            setTimeout(() => {
                if (line.parentNode) {
                    line.parentNode.removeChild(line);
                }
            }, 8000);
        }
        
        // Create new circuit lines periodically
        setInterval(createCircuitLine, 3000);
        
        // Add floating particles
        function createParticle() {
            const particle = document.createElement('div');
            particle.style.position = 'fixed';
            particle.style.width = '2px';
            particle.style.height = '2px';
            particle.style.background = 'var(--accent-cyan)';
            particle.style.borderRadius = '50%';
            particle.style.left = Math.random() * 100 + '%';
            particle.style.top = '100%';
            particle.style.zIndex = '-1';
            particle.style.opacity = '0.6';
            particle.style.animation = 'floatUp 6s linear infinite';
            
            document.body.appendChild(particle);
            
            setTimeout(() => {
                if (particle.parentNode) {
                    particle.parentNode.removeChild(particle);
                }
            }, 6000);
        }
        
        // Add CSS for floating particles
        const style = document.createElement('style');
        style.textContent = `
            @keyframes floatUp {
                0% {
                    transform: translateY(0) rotate(0deg);
                    opacity: 0.6;
                }
                50% {
                    opacity: 1;
                }
                100% {
                    transform: translateY(-100vh) rotate(360deg);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);
        
        // Create particles periodically
        setInterval(createParticle, 2000);
        
        // Add click effect to service cards
        document.querySelectorAll('.service-card').forEach(card => {
            card.addEventListener('click', function(e) {
                // Create ripple effect
                const ripple = document.createElement('div');
                const rect = this.getBoundingClientRect();
                const size = Math.max(rect.width, rect.height);
                const x = e.clientX - rect.left - size / 2;
                const y = e.clientY - rect.top - size / 2;
                
                ripple.style.width = ripple.style.height = size + 'px';
                ripple.style.left = x + 'px';
                ripple.style.top = y + 'px';
                ripple.style.position = 'absolute';
                ripple.style.borderRadius = '50%';
                ripple.style.background = 'rgba(0, 212, 255, 0.3)';
                ripple.style.transform = 'scale(0)';
                ripple.style.animation = 'ripple 0.6s linear';
                ripple.style.pointerEvents = 'none';
                
                this.style.position = 'relative';
                this.style.overflow = 'hidden';
                this.appendChild(ripple);
                
                setTimeout(() => {
                    ripple.remove();
                }, 600);
            });
        });
        
        // Add ripple animation CSS
        const rippleStyle = document.createElement('style');
        rippleStyle.textContent = `
            @keyframes ripple {
                to {
                    transform: scale(2);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(rippleStyle);
        
        // Performance optimization: reduce animations on mobile
        if (window.innerWidth <= 768) {
            document.querySelectorAll('.circuit-line').forEach(line => {
                line.style.animationDuration = '6s';
            });
        }
        
        // Loading screen effect
        window.addEventListener('load', () => {
            document.body.style.opacity = '0';
            setTimeout(() => {
                document.body.style.transition = 'opacity 1s ease';
                document.body.style.opacity = '1';
            }, 100);
        });
    </script>
</body>
</html>
