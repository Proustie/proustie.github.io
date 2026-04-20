<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iván y Minerva - 23 de Mayo 2026</title>
    
    <!-- Google Fonts - Tipografías elegantes -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500&family=Lora:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Lora', Georgia, serif;
            background: #fafaf8;
            color: #2c2c2c;
            line-height: 1.8;
            overflow-x: hidden;
        }

        /* ========================================
           CABECERA PRINCIPAL
           ======================================== */
        .header {
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), 
                        url('imagenes/portada.jpg');
            background-size: cover;
            background-position: center;
            background-color: #d4af37;
            background-attachment: fixed;
            color: white;
            text-align: center;
            padding: 150px 20px;
            position: relative;
        }

        .header h1 {
            font-size: 5.5em;
            font-weight: 300;
            margin-bottom: 30px;
            text-shadow: 3px 3px 10px rgba(0,0,0,0.7);
            font-family: 'Cormorant Garamond', Georgia, serif;
            letter-spacing: 12px;
            animation: fadeInDown 1.5s ease-out;
        }

        .header .date {
            font-size: 2em;
            font-weight: 300;
            letter-spacing: 6px;
            text-shadow: 2px 2px 6px rgba(0,0,0,0.7);
            animation: fadeInUp 1.5s ease-out 0.3s backwards;
        }

        .header .divider {
            width: 200px;
            height: 2px;
            background: white;
            margin: 30px auto;
            animation: expandWidth 1.5s ease-out 0.6s backwards;
        }

        /* ========================================
           LÍNEA DE TIEMPO CENTRAL
           ======================================== */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0;
            position: relative;
        }

        .container::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 1px;
            background: linear-gradient(to bottom, 
                transparent 0%, 
                #c9b896 5%, 
                #c9b896 95%, 
                transparent 100%);
            top: 0;
            bottom: 0;
            z-index: 0;
        }

        /* ========================================
           SECCIONES CON ANIMACIONES
           ======================================== */
        .section {
            margin: 100px 40px;
            background: #ffffff;
            border-radius: 0;
            overflow: hidden;
            box-shadow: 0 2px 30px rgba(0,0,0,0.06);
            position: relative;
            z-index: 2;
            opacity: 0;
            transform: translateY(40px);
            transition: all 1s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid #f0ede7;
        }

        .section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* ========================================
           ENCABEZADOS DE SECCIONES
           ======================================== */
        .section-header {
            position: relative;
            height: 350px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .section-header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(rgba(0,0,0,0.35), rgba(0,0,0,0.45));
            z-index: 1;
        }

        .section-header h2 {
            position: relative;
            z-index: 2;
            font-size: 3em;
            color: white;
            font-weight: 300;
            text-align: center;
            text-shadow: 2px 2px 20px rgba(0,0,0,0.4);
            font-family: 'Cormorant Garamond', Georgia, serif;
            padding: 0 30px;
            letter-spacing: 6px;
            text-transform: uppercase;
            font-size: 2.5em;
        }

        /* Efecto parallax en headers con vídeo */
        .video-background {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 0;
        }

        .video-background video {
            min-width: 100%;
            min-height: 100%;
            width: auto;
            height: auto;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            object-fit: cover;
        }

        /* Fondos para secciones - paleta elegante y neutra */
        .ceremonia-bg {
            position: relative;
            background-color: #e8e4dc;
        }

        .celebracion-bg {
            position: relative;
            background-color: #e8e4dc;
        }

        .confirmacion-bg {
            background: linear-gradient(135deg, #d4c5b0 0%, #a8977a 100%);
        }

        .alojamiento-bg {
            background: linear-gradient(135deg, #b8a790 0%, #8a7766 100%);
        }

        .regalos-bg {
            background: linear-gradient(135deg, #c9b896 0%, #9d8b6f 100%);
        }

        .programa-bg {
            background: linear-gradient(135deg, #a89885 0%, #7d6e5d 100%);
        }

        .parking-bg {
            background: linear-gradient(135deg, #d0c2ad 0%, #b09f89 100%);
        }

        /* ========================================
           CONTENIDO DE SECCIONES
           ======================================== */
        .section-content {
            padding: 60px 50px;
        }

        .section-intro {
            text-align: center;
            font-size: 1.15em;
            color: #6b6b6b;
            margin-bottom: 50px;
            line-height: 1.9;
            font-style: italic;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }

        .info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .info-item {
            display: flex;
            align-items: flex-start;
            gap: 20px;
            padding: 30px;
            background: #fafaf8;
            border-radius: 0;
            border-left: 3px solid #c9b896;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border-top: 1px solid #f0ede7;
            border-bottom: 1px solid #f0ede7;
        }

        .info-item:hover {
            transform: translateX(5px);
            background: #ffffff;
            box-shadow: 0 4px 20px rgba(0,0,0,0.04);
        }

        .info-item svg {
            width: 28px;
            height: 28px;
            flex-shrink: 0;
            margin-top: 5px;
            opacity: 0.7;
        }

        .info-item .text h3 {
            font-size: 1.1em;
            color: #8a7766;
            margin-bottom: 12px;
            font-weight: 500;
            letter-spacing: 1px;
            text-transform: uppercase;
            font-size: 0.9em;
        }

        .info-item .text p {
            color: #6b6b6b;
            font-size: 1.1em;
            line-height: 1.8;
        }

        /* ========================================
           BOTONES Y ENLACES - Diseño minimalista elegante
           ======================================== */
        .button-group {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin-top: 50px;
        }

        .map-link, .button {
            display: inline-block;
            padding: 16px 45px;
            background: transparent;
            color: #8a7766;
            text-decoration: none;
            border-radius: 0;
            transition: all 0.3s ease;
            font-size: 0.95em;
            font-weight: 400;
            border: 2px solid #c9b896;
            letter-spacing: 2px;
            text-transform: uppercase;
            cursor: pointer;
        }

        .map-link:hover, .button:hover {
            background: #c9b896;
            color: #ffffff;
            border-color: #c9b896;
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(201, 184, 150, 0.2);
        }

        .button-secondary {
            background: transparent;
            color: #8a7766;
            border: 2px solid #d4c5b0;
        }

        .button-secondary:hover {
            background: #d4c5b0;
            color: #ffffff;
            border-color: #d4c5b0;
        }

        /* ========================================
           SECCIÓN DE CONFIRMACIÓN
           ======================================== */
        .confirm-box {
            background: #fafaf8;
            padding: 50px;
            border-radius: 0;
            text-align: center;
            max-width: 650px;
            margin: 40px auto;
            border: 1px solid #f0ede7;
        }

        .confirm-box h3 {
            font-size: 2em;
            color: #2c2c2c;
            margin-bottom: 25px;
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-weight: 300;
            letter-spacing: 2px;
        }

        .confirm-box p {
            color: #6b6b6b;
            font-size: 1.05em;
            margin-bottom: 25px;
            line-height: 1.9;
        }

        /* ========================================
           LISTA DE HOTELES
           ======================================== */
        .hotel-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .hotel-card {
            background: #fafaf8;
            padding: 35px;
            border-radius: 0;
            border: 1px solid #f0ede7;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .hotel-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 8px 30px rgba(0,0,0,0.08);
            border-color: #e8e4dc;
        }

        .hotel-card h4 {
            font-size: 1.4em;
            color: #8a7766;
            margin-bottom: 20px;
            font-weight: 300;
            letter-spacing: 1px;
        }

        .hotel-card p {
            color: #6b6b6b;
            margin-bottom: 12px;
            line-height: 1.7;
        }

        /* ========================================
           SECCIÓN DE REGALOS
           ======================================== */
        .gift-box {
            background: #fafaf8;
            padding: 60px 50px;
            border-radius: 0;
            text-align: center;
            max-width: 700px;
            margin: 40px auto;
            border: 1px solid #f0ede7;
        }

        .gift-icon {
            font-size: 3em;
            margin-bottom: 30px;
            opacity: 0.6;
        }

        .gift-box h3 {
            font-size: 2em;
            color: #2c2c2c;
            margin-bottom: 25px;
            font-family: 'Cormorant Garamond', Georgia, serif;
            font-weight: 300;
            letter-spacing: 2px;
        }

        .gift-box p {
            color: #6b6b6b;
            font-size: 1.08em;
            line-height: 1.9;
            margin-bottom: 18px;
        }

        /* ========================================
           SECCIÓN DE PROGRAMA (con imagen)
           ======================================== */
        .programa-image {
            max-width: 800px;
            margin: 30px auto;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(0,0,0,0.15);
        }

        .programa-image img {
            width: 100%;
            height: auto;
            display: block;
        }

        .programa-placeholder {
            background: white;
            padding: 80px 40px;
            text-align: center;
            color: #999;
            font-style: italic;
            border: 2px dashed #ddd;
            border-radius: 15px;
        }

        /* ========================================
           FOOTER
           ======================================== */
        footer {
            text-align: center;
            padding: 100px 20px;
            background: linear-gradient(135deg, #a89885 0%, #7d6e5d 100%);
            color: #ffffff;
            font-size: 1.1em;
            margin-top: 120px;
        }

        footer p {
            margin: 18px 0;
            opacity: 0.95;
        }

        footer .names {
            font-size: 2.8em;
            font-family: 'Cormorant Garamond', Georgia, serif;
            margin-top: 40px;
            letter-spacing: 6px;
            font-weight: 300;
        }

        footer .heart {
            font-size: 2em;
            animation: heartbeat 1.5s infinite;
            opacity: 0.8;
        }

        /* ========================================
           ANIMACIONES
           ======================================== */
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes expandWidth {
            from {
                width: 0;
            }
            to {
                width: 200px;
            }
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.2); }
        }

        /* ========================================
           RESPONSIVE
           ======================================== */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 3em;
                letter-spacing: 6px;
            }

            .header .date {
                font-size: 1.5em;
            }
            
            .section-header {
                height: 250px;
            }

            .section-header h2 {
                font-size: 2.2em;
            }
            
            .section-content {
                padding: 40px 25px;
            }

            .info-grid, .hotel-list {
                grid-template-columns: 1fr;
            }

            .timeline {
                display: none;
            }

            .container::before {
                display: none;
            }

            .button-group {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <!-- ========================================
         CABECERA PRINCIPAL
         ======================================== -->
    <div class="header">
        <h1>Iván y Minerva</h1>
        <div class="divider"></div>
        <div class="date">23 DE MAYO 2026</div>
    </div>

    <div class="container">
        <!-- ========================================
             SECCIÓN 1: CEREMONIA
             ======================================== -->
        <div class="section">
            <div class="section-header ceremonia-bg">
                <div class="video-background">
                    <video autoplay muted loop playsinline>
                        <!-- CAMBIA AQUÍ la ruta de tu vídeo de la iglesia -->
                        <source src="videos/caridad.mp4" type="video/mp4">
                    </video>
                </div>
                <h2 style="position: relative; z-index: 2;">Santuario de Nuestra Señora de la Caridad</h2>
            </div>
            <div class="section-content">
                <p class="section-intro">
                    Nos encantaría que nos acompañarais en este día tan especial.
                </p>
                <div class="info-grid">
                    <div class="info-item">
                        <svg fill="#d4af37" viewBox="0 0 24 24">
                            <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                        </svg>
                        <div class="text">
                            <h3>Ubicación</h3>
                            <p>Illescas, Toledo</p>
                        </div>
                    </div>
                    <div class="info-item">
                        <svg fill="#d4af37" viewBox="0 0 24 24">
                            <path d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8zm.5-13H11v6l5.25 3.15.75-1.23-4.5-2.67z"/>
                        </svg>
                        <div class="text">
                            <h3>Horario</h3>
                            <p>12:00h.</p>
                        </div>
                    </div>
                </div>
                <div class="button-group">
                    <a href="https://www.google.com/maps/search/?api=1&query=Santuario+Nuestra+Señora+de+la+Caridad+Illescas" target="_blank" class="map-link">📍 Cómo llegar</a>
                </div>
            </div>
        </div>

        <!-- ========================================
             SECCIÓN 2: CELEBRACIÓN
             ======================================== -->
        <div class="section">
            <div class="section-header celebracion-bg">
                <div class="video-background">
                    <video autoplay muted loop playsinline>
                        <!-- CAMBIA AQUÍ la ruta de tu vídeo de la hacienda -->
                        <source src="videos/hacienda.mp4" type="video/mp4">
                    </video>
                </div>
                <h2 style="position: relative; z-index: 2;">La Hacienda del Marqués</h2>
            </div>
            <div class="section-content">
                <p class="section-intro">
                    Después de la ceremonia, continuaremos la celebración con un cóctel y banquete.
                </p>
                <div class="info-grid">
                    <div class="info-item">
                        <svg fill="#d4af37" viewBox="0 0 24 24">
                            <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                        </svg>
                        <div class="text">
                            <h3>Ubicación</h3>
                            <p>Bargas, Toledo</p>
                        </div>
                    </div>
                    <div class="info-item">
                        <svg fill="#d4af37" viewBox="0 0 24 24">
                            <path d="M18.06 23h1.66c.84 0 1.53-.65 1.63-1.47L23 5.05h-5V1h-1.97v4.05h-4.97l.3 2.34c1.71.47 3.31 1.32 4.27 2.26 1.44 1.42 2.43 2.89 2.43 5.29V23zM1 22v-1h15.03v1c0 .54-.45 1-1.03 1H2c-.55 0-1-.46-1-1zm15.03-7C16.03 7 1 7 1 15h15.03zM1 17h15v2H1z"/>
                        </svg>
                        <div class="text">
                            <h3>Horario</h3>
                            <p>14:00h</p>
                        </div>
                    </div>
                </div>
                <div class="button-group">
                    <a href="https://www.google.com/maps/search/?api=1&query=La+Hacienda+del+Marqués+Bargas" target="_blank" class="map-link">📍 Cómo llegar</a>
                </div>
            </div>
        </div>

        <!-- ========================================
             SECCIÓN 3: CONFIRMACIÓN DE ASISTENCIA
             ======================================== -->
        <div class="section">
            <div class="section-header confirmacion-bg">
                <h2>Confirmación de Asistencia</h2>
            </div>
            <div class="section-content">
                <div class="confirm-box">
                    <h3>¿Contamos contigo?</h3>
                    <p>Por favor, confirma tu asistencia antes del <strong>1 de mayo de 2026</strong>.</p>
                    <p>Te agradeceríamos que nos indicases si tienes alguna alergia o intolerancia alimentaria.</p>
                    <a href="https://forms.gle/TU_ENLACE_DE_GOOGLE_FORMS" target="_blank" class="button">
                        ✉️ Confirmar asistencia
                    </a>
                </div>
            </div>
        </div>

        <!-- ========================================
             SECCIÓN 4: ALOJAMIENTO
             ======================================== -->
        <div class="section">
            <div class="section-header alojamiento-bg">
                <h2>Alojamiento</h2>
            </div>
            <div class="section-content">
                <p class="section-intro">
                    Si necesitas alojamiento, aquí te dejamos algunas opciones cercanas.
                </p>
                <div class="hotel-list">
                    <!-- PERSONALIZA AQUÍ tus hoteles recomendados -->
                    <div class="hotel-card">
                        <h4>🏨 Hotel Real de Illescas</h4>
                        <p><strong>Dirección:</strong> Pl. Hermanos Fernández Criado, 45200 Illescas, Toledo</p>
                        <p><strong>Distancia:</strong> 100 m.</p>
                        <p><strong>Teléfono:</strong> 925 54 16 99</p>
                        <a href="http://www.hotelrealillescas.es/" target="_blank" class="button button-secondary" style="margin-top: 15px; display: inline-block; padding: 12px 25px; font-size: 0.95em;">Ver más info</a>
                    </div>
                    <div class="hotel-card">
                        <h4>🏨 Hotel Carlos I</h4>
                        <p><strong>Dirección:</strong> Pol. Ind. Villa de Yuncos, C. Carlos I, 51, 45210 Yuncos, Toledo</p>
                        <p><strong>Distancia:</strong> 8 km.</p>
                        <p><strong>Teléfono:</strong> 925 55 79 19</p>
                        <a href="https://www.hotelcarlos1.com/" target="_blank" class="button button-secondary" style="margin-top: 15px; display: inline-block; padding: 12px 25px; font-size: 0.95em;">Ver más info</a>
                    </div>
                    <div class="hotel-card">
                        <h4>🏨 HOSTAL 82</h4>
                        <p><strong>Dirección:</strong> A-42 SALIDA 59 SENTIDO MADRID Via de Servicio, 45280, Toledo</p>
                        <p><strong>Distancia:</strong> 10 km.</p>
                        <p><strong>Teléfono:</strong> 925 09 30 65</p>
                        <a href="http://www.hostal82.com/" target="_blank" class="button button-secondary" style="margin-top: 15px; display: inline-block; padding: 12px 25px; font-size: 0.95em;">Ver más info</a>
                    </div>
                </div>
            </div>
        </div>

        <!-- ========================================
             SECCIÓN 5: REGALOS
             ======================================== -->
        <div class="section">
            <div class="section-header regalos-bg">
                <h2>Regalos</h2>
            </div>
            <div class="section-content">
                <div class="gift-box">
                    <div class="gift-icon">🎁</div>
                    <h3>Vuestra compañía es nuestro mejor regalo</h3>
                    <p>Lo más importante para nosotros es compartir este día tan especial con vosotros.</p>
                    <p>Si aun así deseáis hacernos un regalo, agradeceríamos una aportación para nuestra luna de miel.</p>
                    <!-- OPCIONAL: Añade aquí el número de cuenta o enlace a lista de bodas -->
                    <p style="margin-top: 25px; font-size: 1em; color: #999;">
                        <em>Podéis hacerlo llegar el día de la boda o contactar con nosotros.</em>
                    </p>
                </div>
            </div>
        </div>

        <!-- ========================================
             SECCIÓN 6: PROGRAMA DEL DÍA
             ======================================== -->
        <div class="section">
            <div class="section-header programa-bg">
                <h2>Programa del Día</h2>
            </div>
            <div class="section-content">
                <p class="section-intro">
                    Así transcurrirá nuestro gran día. ¡No te lo pierdas!
                </p>
                <!-- Aquí puedes poner tu imagen del timeline -->
                <div class="programa-image">
                    <!-- OPCIÓN 1: Si tienes una imagen del programa, descomenta esto y cambia la ruta:
                    <img src="imagenes/programa.jpg" alt="Programa del día">
                    -->
                    
                    <!-- OPCIÓN 2: Placeholder temporal (elimínalo cuando tengas la imagen) -->
                    <div class="programa-placeholder">
                        <p style="font-size: 1.2em;">📸 Aquí irá vuestra imagen del timeline del día</p>
                        <p style="margin-top: 15px; font-size: 0.95em;">Guarda tu imagen como "imagenes/programa.jpg" y descomenta la línea correspondiente en el HTML</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- ========================================
             SECCIÓN 7: APARCAMIENTO
             ======================================== -->
        <div class="section">
            <div class="section-header parking-bg">
                <h2>Aparcamiento</h2>
            </div>
            <div class="section-content">
                <div class="confirm-box">
                    <h3>🅿️ Dónde aparcar</h3>
                    <p>Tanto el Santuario como La Hacienda del Marqués disponen de aparcamiento gratuito.</p>
                    <p style="margin-top: 20px; color: #999; font-size: 0.95em;">
                        <em>Más información disponible próximamente.</em>
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- ========================================
         FOOTER
         ======================================== -->
    <footer>
        <p>¡Nos hace muchísima ilusión celebrarlo con vosotros!</p>
        <p class="heart">❤️</p>
        <p class="names">Iván & Minerva</p>
        <p style="margin-top: 30px; font-size: 0.9em; opacity: 0.8;">23 de Mayo, 2026</p>
    </footer>

    <!-- ========================================
         JAVASCRIPT PARA ANIMACIONES AL SCROLL
         ======================================== -->
    <script>
        // Animación de aparición al hacer scroll
        const observerOptions = {
            threshold: 0.15,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        // Observar todas las secciones
        document.addEventListener('DOMContentLoaded', () => {
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => observer.observe(section));
        });
    </script>

    <!-- ========================================
         INSTRUCCIONES PARA PERSONALIZAR:
         
         ✅ VÍDEOS: 
         - Ceremonia: busca <source src="videos/caridad.mp4"
         - Celebración: busca <source src="videos/hacienda.mp4"
         
         ✅ CONFIRMACIÓN DE ASISTENCIA:
         - Busca "TU_ENLACE_DE_GOOGLE_FORMS" y cambia el enlace
         
         ✅ HOTELES:
         - Busca "Hotel 1", "Hotel 2", "Hotel 3" y personaliza
         
         ✅ REGALOS:
         - Personaliza el mensaje según vuestras preferencias
         
         ✅ PROGRAMA DEL DÍA:
         - Guarda tu imagen como "imagenes/programa.jpg"
         - Descomenta la línea: <img src="imagenes/programa.jpg"
         
         ✅ APARCAMIENTO:
         - Añade información específica de aparcamiento
         
         ======================================== -->
</body>
</html>
