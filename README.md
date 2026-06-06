<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="color-scheme" content="light dark">
    <title>Ansiedad Digital Escolar</title>
    
    <!-- Fuentes limpias y ligeras -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Plus+Jakarta+Sans:wght@700;800&display=swap" rel="stylesheet">
    
    <script>
        function validarFormulario(event) {
            event.preventDefault();
            
            var campoNombre = document.getElementById('idNombre');
            var campoCorreo = document.getElementById('idCorreo');
            var campoMensaje = document.getElementById('idMensaje');

            if (!campoNombre || !campoCorreo || !campoMensaje) {
                alert("Error interno: No se encontraron los campos del formulario.");
                return false;
            }

            var nombreText = campoNombre.value.trim();
            var correoText = campoCorreo.value.trim().toLowerCase();
            var mensajeText = campoMensaje.value.trim();

            var filtroNombre = /^[a-zA-ZáéíóúÁÉÍÓÚñÑüÜ\s]{3,}$/;
            if (!filtroNombre.test(nombreText)) {
                alert("Por favor, ingresa un nombre válido (mínimo 3 caracteres, sin números ni caracteres especiales).");
                campoNombre.focus();
                return false;
            }

            var filtroCorreo = /^[a-z0-9._%+-]+@(gmail|hotmail|live|outlook|yahoo|icloud|pcpuma|comunidad|ipn|alumno\.ipn|sep|nube\.sep|[a-z0-9.-]+\.unam|[a-z0-9.-]+\.edu)\.(com|mx|net|org|gob\.mx|edu\.mx|unam\.mx)$/;
            
            var esInstitucionalValido = correoText.endsWith('.unam.mx') || 
                                         correoText.endsWith('.edu.mx') || 
                                         correoText.endsWith('.ipn.mx') || 
                                         correoText.endsWith('.sep.gob.mx');
            
            if (!filtroCorreo.test(correoText) && !esInstitucionalValido) {
                alert("Por favor, usa un correo correcto personal o institucional.");
                campoCorreo.focus();
                return false;
            }

            if (mensajeText === "") {
                alert("Por favor, rellena el cuadro de mensaje antes de enviar.");
                campoMensaje.focus();
                return false;
            }

            alert("¡Tu mensaje fue enviado con éxito! Recuerda tomar un descanso de las pantallas hoy."); 
            return true;
        }
    </script>

    <style>
        :root {
            --bg-principal: #f0f4f8;
            --bg-tarjeta: #ffffff;
            --texto-principal: #1e293b;
            --texto-secundario: #475569;
            --azul-fuerte: #1e40af;
            --azul-brillante: #2563eb;
            --borde: rgba(0, 0, 0, 0.06);
        }

        :root.dark-mode {
            --bg-principal: #0f172a !important;
            --bg-tarjeta: #1e293b !important;
            --texto-principal: #f8fafc !important;
            --texto-secundario: #94a3b8 !important;
            --azul-fuerte: #0f172a !important;
            --azul-brillante: #38bdf8 !important;
            --borde: rgba(255, 255, 255, 0.08) !important;
        }

        @media (prefers-color-scheme: dark) {
            :root:not(.light-mode) {
                --bg-principal: #0f172a;
                --bg-tarjeta: #1e293b;
                --texto-principal: #f8fafc;
                --texto-secundario: #94a3b8;
                --azul-fuerte: #0f172a;
                --azul-brillante: #38bdf8;
                --borde: rgba(255, 255, 255, 0.08);
            }
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            /* Quitamos la transición global de background para evitar retrasos molestos al renderizar */
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        html {
            scroll-behavior: auto;
        }

        body {
            font-family: 'Inter', system-ui, -apple-system, sans-serif;
            line-height: 1.6;
            background-color: var(--bg-principal);
            color: var(--texto-principal);
            -webkit-font-smoothing: antialiased;
        }

        header {
            background: linear-gradient(135deg, #2563eb, #1d4ed8);
            color: white;
            text-align: center;
            padding: 70px 20px;
        }

        header h1 {
            font-family: 'Plus Jakarta Sans', sans-serif;
            font-weight: 800;
            margin-bottom: 14px;
            font-size: 2.6rem;
            letter-spacing: -0.02em;
        }

        header p {
            font-size: 1.1rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
        }

        /* BARRA DE NAVEGACIÓN MEJORADA (Cero trabas) */
        nav {
            background-color: var(--azul-fuerte);
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            justify-content: flex-start;
            overflow-x: auto;
            white-space: nowrap; 
            -webkit-overflow-scrolling: touch; 
            border-bottom: 1px solid var(--borde);
            padding: 0 10px;
        }

        @media (min-width: 768px) {
            nav {
                justify-content: center;
                overflow-x: visible;
            }
        }

        /* Ocultar barras de scroll visuales */
        nav::-webkit-scrollbar { display: none; }
        nav { -ms-overflow-style: none; scrollbar-width: none; }

        nav a {
            color: white;
            text-decoration: none;
            padding: 18px 24px;
            font-weight: 600;
            font-size: 0.95rem;
            display: inline-block;
            cursor: pointer;
            flex-shrink: 0; /* Evita que el texto se aplaste */
        }

        nav a:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        section {
            padding: 45px 20px;
            max-width: 850px;
            margin: 0 auto;
        }

        /* TARJETAS CON ANIMACIÓN MÁS FLUIDA (CSS optimizado) */
        .card {
            background-color: var(--bg-tarjeta);
            padding: 40px;
            border-radius: 24px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.03);
            border: 1px solid var(--borde);
            
            opacity: 0;
            transform: translateY(30px);
            /* Transición limpia únicamente para la aparición inicial */
            transition: transform 0.5s ease-out, opacity 0.5s ease-out;
            will-change: transform, opacity;
        }

        .card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* Animación elástica reducida para no colgar el navegador */
        @keyframes reboteLigero {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .bounce-animacion {
            animation: reboteLigero 0.4s ease-in-out;
        }

        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.06);
        }

        h2, h3 {
            font-family: 'Plus Jakarta Sans', sans-serif;
            color: var(--azul-brillante);
            letter-spacing: -0.02em;
        }

        h2 { font-size: 2rem; font-weight: 700; margin-bottom: 22px; }
        h3 { font-size: 1.35rem; font-weight: 700; margin-top: 25px; margin-bottom: 10px; }

        p {
            margin-bottom: 18px;
            font-size: 1.05rem;
            color: var(--texto-secundario);
        }

        .grid-tips {
            display: grid;
            grid-template-columns: 1fr;
            gap: 16px;
            margin-top: 20px;
        }

        .tip-item {
            background: rgba(37, 99, 235, 0.06);
            padding: 18px 22px;
            border-radius: 16px;
            border-left: 4px solid var(--azul-brillante);
            color: var(--texto-secundario);
        }
        
        .tip-item strong { color: var(--texto-principal); }

        form {
            display: flex;
            flex-direction: column;
            gap: 18px;
        }

        label {
            font-weight: 600;
            font-size: 0.9rem;
            margin-bottom: -10px;
        }

        input, textarea {
            padding: 16px;
            border: 2px solid var(--borde);
            border-radius: 12px;
            background-color: var(--bg-principal);
            color: var(--texto-principal);
            font-family: 'Inter', sans-serif;
            font-size: 1rem;
        }

        input:focus, textarea:focus {
            outline: none;
            border-color: var(--azul-brillante);
            box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.15);
        }

        textarea { resize: vertical; min-height: 140px; }

        button[type="submit"] {
            background-color: var(--azul-brillante);
            color: white;
            border: none;
            padding: 16px;
            border-radius: 12px;
            cursor: pointer;
            font-family: 'Inter', sans-serif;
            font-weight: 600;
            font-size: 1rem;
            box-shadow: 0 4px 12px rgba(37, 99, 235, 0.2);
        }

        button[type="submit"]:hover { background-color: #1d4ed8; }

        .btn-modo {
            position: fixed;
            bottom: 24px;
            right: 24px;
            width: 52px;
            height: 52px;
            border-radius: 50%;
            background-color: var(--azul-brillante);
            color: white;
            border: none;
            box-shadow: 0 4px 20px rgba(0,0,0,0.2);
            cursor: pointer;
            font-size: 1.4rem;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 999;
        }

        footer {
            background-color: var(--azul-fuerte);
            color: white;
            text-align: center;
            padding: 35px 20px;
            margin-top: 60px;
            font-size: 0.95rem;
            opacity: 0.9;
        }

        @media (max-width: 600px) {
            header h1 { font-size: 2rem; }
            nav a { padding: 16px 14px; font-size: 0.85rem; }
            .card { padding: 25px; border-radius: 20px; }
            h2 { font-size: 1.6rem; }
        }
    </style>
</head>
<body>

    <button class="btn-modo" id="toggleModo" title="Cambiar Modo">🌓</button>

    <header>
        <h1>Ansiedad Digital Escolar</h1>
        <p>Promoviendo el bienestar, la salud mental y el equilibrio tecnológico en la vida de los estudiantes.</p>
    </header>

    <nav>
        <a onclick="irASeccionDinamica('inicio')">Inicio</a>
        <a onclick="irASeccionDinamica('nosotros')">Nosotros</a>
        <a onclick="irASeccionDinamica('informacion')">Síntomas</a>
        <a onclick="irASeccionDinamica('prevencion')">Estrategias</a>
        <a onclick="irASeccionDinamica('contacto')">Contacto</a>
    </nav>

    <section id="inicio">
        <div class="card" id="card-inicio">
            <h2>¿Qué es?</h2>
            <p>La ansiedad digital escolar es el estrés, la sobrecarga o la incomodidad que experimentan los estudiantes debido a la conexión permanente a pantallas, redes sociales y plataformas de tareas. Aunque la tecnología es una excelente herramienta para estudiar, usarla todo el día sin límites puede terminar afectando la mente y el rendimiento académico.</p>
        </div>
    </section>

    <section id="nosotros">
        <div class="card" id="card-nosotros">
            <h2>Nuestro Objetivo</h2>
            <h3>Misión</h3>
            <p>Concientizar a la comunidad estudiantil y académica sobre los riesgos de la sobrecarga digital, ofreciendo herramientas sencillas para mejorar la salud mental.</p>
            <h3>Visión</h3>
            <p>Lograr que los estudiantes utilicen la tecnología de forma consciente, asegurando que los dispositivos sean herramientas de apoyo y no generadores de estrés.</p>
        </div>
    </section>

    <section id="informacion">
        <div class="card" id="card-informacion">
            <h2>Señales de Alerta</h2>
            <p>Estar conectados de forma permanente impide que el cerebro descanse adecuadamente. Los principales síntomas asociados son:</p>
            
            <div class="grid-tips">
                <div class="tip-item"><strong>Falta de enfoque:</strong> Dificultad para concentrarse en las clases o tareas debido a la revisión constante de notificaciones.</div>
                <div class="tip-item"><strong>Insomnio digital:</strong> Prolongación del uso de dispositivos durante la noche, afectando la calidad del sueño y la energía del día siguiente.</div>
                <div class="tip-item"><strong>Presión social:</strong> Sentimientos de insuficiencia o desánimo al comparar la vida personal con el contenido publicado en redes sociales.</div>
                <div class="tip-item"><strong>Efecto FOMO:</strong> Ansiedad o temor persistentente a perderse de información o eventos importantes si no se revisa el teléfono con frecuencia.</div>
            </div>
        </div>
    </section>

    <section id="prevencion">
        <div class="card" id="card-prevencion">
            <h2>Estrategias de Control</h2>
            <p>Encontrar un equilibrio no implica abandonar la tecnología, sino aprender a gestionarla correctamente. Se sugiere aplicar las siguientes pautas:</p>
            
            <div class="grid-tips">
                <div class="tip-item"><strong>Zonas libres de pantallas:</strong> Restringir el uso de teléfonos durante las comidas y desconectarse al menos 30 minutos antes de ir a dormir.</div>
                <div class="tip-item"><strong>Silenciar notificaciones innecesarias:</strong> Desactivar las alertas de aplicaciones que no sean prioritarias para evitar interrupciones constantes.</div>
                <div class="tip-item"><strong>Regla de pausas activas:</strong> Por cada 45 minutos de estudio o trabajo frente a la pantalla, realizar un descanso de 5 minutos para estirarse o hidratarse.</div>
            </div>
        </div>
    </section>

    <section id="contacto">
        <div class="card" id="card-contacto">
            <h2>Contacto</h2>
            <p>Si sientes que el entorno escolar y digital te sobrepasan, puedes escribirnos un mensaje. Todos los campos son obligatorios.</p>
            
            <form id="formContacto" action="https://formspree.io/f/xbdeglpy" method="POST" onsubmit="return validarFormulario(event);">
                <label for="idNombre">Nombre Completo:</label>
                <input type="text" id="idNombre" name="nombre" placeholder="Mínimo 3 letras, sin números ni signos" required>

                <label for="idCorreo">Correo Electrónico:</label>
                <input type="email" id="idCorreo" name="correo" placeholder="correo@comunidad.unam.mx, @ipn.mx, etc." required>

                <label for="idMensaje">Mensaje o Consulta:</label>
                <textarea id="idMensaje" name="mensaje" placeholder="Escribe aquí detalladamente lo que necesites..." required></textarea>

                <button type="submit" id="btnEnviar">Enviar Mensaje</button>
            </form>
        </div>
    </section>

    <footer>
        <p>&copy; 2026 Bienestar Digital Escolar. Todos los derechos reservados.</p>
    </footer>

    <script>
        // 1. Control del Modo Oscuro (Sin retrasos)
        const btnModo = document.getElementById('toggleModo');
        const root = document.documentElement;

        if (localStorage.getItem('theme') === 'dark') {
            root.classList.add('dark-mode');
        }

        btnModo.addEventListener('click', () => {
            if (root.classList.contains('dark-mode')) {
                root.classList.remove('dark-mode');
                root.classList.add('light-mode');
                localStorage.setItem('theme', 'light');
            } else {
                root.classList.remove('light-mode');
                root.classList.add('dark-mode');
                localStorage.setItem('theme', 'dark');
            }
        });

        // 2. SCROLL DINÁMICO ULTRA OPTIMIZADO (Suave de extremo a extremo)
        function irASeccionDinamica(idSeccion) {
            const seccion = document.getElementById(idSeccion);
            const tarjeta = document.getElementById('card-' + idSeccion);
            if (!seccion || !tarjeta) return;

            const posicionDestino = seccion.getBoundingClientRect().top + window.pageYOffset - 70;
            const posicionInicial = window.pageYOffset;
            const distancia = posicionDestino - posicionInicial;
            const distanciaAbsoluta = Math.abs(distancia);

            // Ajustamos el escalado de tiempo: mínimo 700ms y máximo 1600ms para evitar congelamientos
            const duracion = Math.max(700, Math.min(1600, distanciaAbsoluta * 0.5)); 
            let tiempoInicio = null;

            function animacionScroll(tiempoActual) {
                if (tiempoInicio === null) tiempoInicio = tiempoActual;
                const tiempoTranscurrido = tiempoActual - tiempoInicio;
                const progreso = Math.min(tiempoTranscurrido / duracion, 1);
                
                // Ease Out Cubic (más sutil y ligero para el procesador)
                const progresoEase = 1 - Math.pow(1 - progreso, 3);
                
                window.scrollTo(0, posicionInicial + (distancia * progresoEase));

                if (tiempoTranscurrido < duracion) {
                    requestAnimationFrame(animacionScroll);
                } else {
                    tarjeta.classList.add('bounce-animacion');
                    tarjeta.addEventListener('animationend', () => {
                        tarjeta.classList.remove('bounce-animacion');
                    }, { once: true });
                }
            }

            requestAnimationFrame(animacionScroll);
        }

        // 3. OBSERVEDOR DE INTERSECCIÓN LIGERO
        document.addEventListener("DOMContentLoaded", function() {
            const tarjetas = document.querySelectorAll('.card');

            const opciones = {
                root: null,
                threshold: 0.05, // Se activa más rápido al asomarse
                rootMargin: "0px"
            };

            const observador = new IntersectionObserver(function(entradas) {
                entradas.forEach(entrada => {
                    if (entrada.isIntersecting) {
                        entrada.target.classList.add('visible');
                    } else {
                        entrada.target.classList.remove('visible');
                    }
                });
            }, opciones);

            tarjetas.forEach(tarjeta => {
                observador.observe(tarjeta);
            });
        });
    </script>
</body>
</html>
