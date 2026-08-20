<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vaca Muerta · Energía Argentina</title>
    <style>
        /* ===== RESET ===== */
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
            background: #f4f6f9;
            color: #1a1a2e;
            line-height: 1.6;
        }
        a { text-decoration: none; color: inherit; }

        /* ===== NAVBAR ===== */
        nav {
            background: #0b1a2e;
            padding: 18px 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }
        .logo {
            font-size: 1.7rem;
            font-weight: 700;
            color: #f5b041;
            letter-spacing: -0.5px;
        }
        .logo span { color: #ecf0f1; font-weight: 300; }
        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }
        .nav-links a {
            color: #d5dbdb;
            font-weight: 500;
            padding: 6px 0;
            border-bottom: 2px solid transparent;
            transition: 0.25s;
        }
        .nav-links a:hover {
            color: #f5b041;
            border-bottom-color: #f5b041;
        }

        /* ===== SECTIONS ===== */
        .page {
            display: none;
            max-width: 1100px;
            margin: 0 auto;
            padding: 50px 30px 70px;
            animation: fadeUp 0.4s ease;
        }
        .page.active { display: block; }

        @keyframes fadeUp {
            0% { opacity:0; transform:translateY(20px); }
            100% { opacity:1; transform:translateY(0); }
        }

        /* ===== HERO ===== */
        .hero {
            background: linear-gradient(135deg, #0b1a2e 0%, #1a3a4a 100%);
            color: white;
            padding: 70px 40px;
            border-radius: 24px;
            text-align: center;
            margin-bottom: 30px;
            box-shadow: 0 12px 40px rgba(0,0,0,0.2);
        }
        .hero h1 {
            font-size: 3.2rem;
            font-weight: 700;
            margin-bottom: 12px;
        }
        .hero h1 span { color: #f5b041; }
        .hero p {
            font-size: 1.25rem;
            opacity: 0.9;
            max-width: 700px;
            margin: 0 auto 20px;
        }
        .badge {
            display: inline-block;
            background: #f5b041;
            color: #0b1a2e;
            font-weight: 600;
            padding: 6px 20px;
            border-radius: 30px;
            font-size: 0.9rem;
        }

        /* ===== CARDS ===== */
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            margin: 30px 0;
        }
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
            margin: 30px 0;
        }
        .card {
            background: white;
            padding: 28px 24px;
            border-radius: 18px;
            box-shadow: 0 6px 24px rgba(0,0,0,0.06);
            transition: transform 0.2s, box-shadow 0.2s;
            border-left: 4px solid #f5b041;
        }
        .card:hover {
            transform: translateY(-6px);
            box-shadow: 0 14px 36px rgba(0,0,0,0.10);
        }
        .card h3 { font-size: 1.3rem; margin-bottom: 8px; color: #0b1a2e; }
        .card p { color: #3d4a5a; }
        .card .icon { font-size: 2.2rem; margin-bottom: 8px; }

        /* ===== TABLA ===== */
        .table-wrap {
            background: white;
            border-radius: 18px;
            overflow: hidden;
            box-shadow: 0 6px 24px rgba(0,0,0,0.06);
            margin: 30px 0;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
        }
        th {
            background: #0b1a2e;
            color: white;
            padding: 16px 20px;
            font-weight: 600;
        }
        td {
            padding: 14px 20px;
            border-bottom: 1px solid #eef2f6;
        }
        tr:last-child td { border-bottom: none; }
        tr:hover td { background: #f8fafc; }

        /* ===== CONTACTO ===== */
        .contact-form {
            background: white;
            padding: 40px;
            border-radius: 24px;
            box-shadow: 0 6px 24px rgba(0,0,0,0.06);
            max-width: 600px;
            margin: 20px auto;
        }
        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 14px 18px;
            border: 1px solid #dce1e8;
            border-radius: 12px;
            font-size: 1rem;
            margin-bottom: 16px;
            transition: border 0.2s;
            font-family: inherit;
        }
        .contact-form input:focus,
        .contact-form textarea:focus {
            outline: none;
            border-color: #f5b041;
            box-shadow: 0 0 0 3px rgba(245,176,65,0.15);
        }
        .btn {
            background: #f5b041;
            color: #0b1a2e;
            border: none;
            padding: 14px 38px;
            border-radius: 40px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.2s;
            display: inline-block;
        }
        .btn:hover {
            background: #e09e2f;
            transform: scale(1.02);
        }

        /* ===== FOOTER ===== */
        footer {
            text-align: center;
            padding: 30px 20px;
            color: #7a8a9a;
            border-top: 1px solid #e2e8f0;
            margin-top: 20px;
            font-size: 0.95rem;
        }
        footer span { color: #f5b041; }

        /* ===== RESPONSIVE ===== */
        @media (max-width: 700px) {
            nav { flex-direction: column; gap: 14px; padding: 16px 20px; }
            .nav-links { gap: 20px; flex-wrap: wrap; justify-content: center; }
            .hero h1 { font-size: 2.2rem; }
            .hero { padding: 40px 20px; }
            .page { padding: 30px 16px 50px; }
            .contact-form { padding: 24px; }
        }
        @media (max-width: 480px) {
            .hero h1 { font-size: 1.8rem; }
            .grid-2, .grid-3 { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

<!-- ===== NAVEGACIÓN ===== -->
<nav>
    <div class="logo">⛰️ Vaca<span>Muerta</span></div>
    <ul class="nav-links">
        <li><a href="#" onclick="showPage('inicio')">Inicio</a></li>
        <li><a href="#" onclick="showPage('datos')">Datos & Claves</a></li>
        <li><a href="#" onclick="showPage('contacto')">Contacto</a></li>
    </ul>
</nav>

<!-- ============================================================ -->
<!-- PÁGINA 1: INICIO -->
<!-- ============================================================ -->
<div id="inicio" class="page active">
    <div class="hero">
        <div class="badge">🇦🇷 Yacimiento no convencional</div>
        <h1>Vaca <span>Muerta</span></h1>
        <p>El gigante energético de la Patagonia argentina. Segunda reserva mundial de gas no convencional y cuarta de petróleo.</p>
        <a href="#" class="btn" onclick="showPage('datos')">Explorar datos →</a>
    </div>

    <div class="grid-2">
        <div class="card">
            <div class="icon">🛢️</div>
            <h3>Petróleo</h3>
            <p>Recursos estimados en <strong>16 mil millones de barriles</strong>. Producción en constante crecimiento desde 2018.</p>
        </div>
        <div class="card">
            <div class="icon">🔥</div>
            <h3>Gas Natural</h3>
            <p>Más de <strong>308 TCF</strong> (trillones de pies cúbicos) de gas recoverable. Clave para la matriz energética.</p>
        </div>
        <div class="card">
            <div class="icon">🏗️</div>
            <h3>Inversiones</h3>
            <p>Más de <strong>USD 30.000 millones</strong> invertidos desde 2013. Empresas como YPF, PAE, Shell y Chevron.</p>
        </div>
        <div class="card">
            <div class="icon">📈</div>
            <h3>Impacto Económico</h3>
            <p>Genera más de <strong>50.000 empleos</strong> directos e indirectos. Motor del crecimiento de Neuquén.</p>
        </div>
    </div>

    <p style="text-align:center; color:#5a6a7a; max-width:700px; margin:10px auto;">
        <strong>📍 Ubicación:</strong> Cuenca Neuquina, provincia de Neuquén, Patagonia argentina.
        Abarca unas 30.000 km² entre las ciudades de Añelo y Rincón de los Sauces.
    </p>
</div>

<!-- ============================================================ -->
<!-- PÁGINA 2: DATOS & CLAVES -->
<!-- ============================================================ -->
<div id="datos" class="page">
    <h2 style="font-size:2.4rem; margin-bottom:6px;">📊 Datos clave</h2>
    <p style="color:#4a5a6a; margin-bottom:20px;">Información actualizada sobre Vaca Muerta</p>

    <div class="grid-3">
        <div class="card"><h3>🌍 Ranking mundial</h3><p>2º en gas no convencional · 4º en petróleo no convencional</p></div>
        <div class="card"><h3>⛽ Producción diaria</h3><p>~340.000 barriles de petróleo · ~80 millones m³ de gas</p></div>
        <div class="card"><h3>📅 Proyección 2030</h3><p>Se espera duplicar la producción actual con nuevas inversiones</p></div>
    </div>

    <div class="table-wrap">
        <table>
            <thead>
                <tr><th>Indicador</th><th>Valor</th><th>Año</th></tr>
            </thead>
            <tbody>
                <tr><td>Recursos de petróleo (est.)</td><td>16.000 millones de barriles</td><td>2023</td></tr>
                <tr><td>Recursos de gas (est.)</td><td>308 TCF</td><td>2023</td></tr>
                <tr><td>Inversión acumulada</td><td>USD 30.000+ millones</td><td>2013-2024</td></tr>
                <tr><td>Empleos generados</td><td>~50.000</td><td>2024</td></tr>
                <tr><td>Pozos activos</td><td>~2.500</td><td>2024</td></tr>
            </tbody>
        </table>
    </div>

    <div style="background:#eaf2f8; padding:24px 30px; border-radius:18px; margin:20px 0;">
        <h3 style="color:#0b1a2e;">🌱 Desafíos ambientales</h3>
        <p style="color:#2c3e50;">El desarrollo de Vaca Muerta requiere un equilibrio entre la producción energética y la sustentabilidad. Se utilizan técnicas de <strong>fracking</strong> (fractura hidráulica), lo que exige una gestión cuidadosa del agua, emisiones y monitoreo sísmico. Argentina avanza en regulaciones para minimizar el impacto ambiental.</p>
    </div>
</div>

<!-- ============================================================ -->
<!-- PÁGINA 3: CONTACTO -->
<!-- ============================================================ -->
<div id="contacto" class="page">
    <h2 style="font-size:2.4rem; text-align:center;">📬 Contacto</h2>
    <p style="text-align:center; color:#4a5a6a; margin-bottom:10px;">¿Quieres más información sobre Vaca Muerta? Escríbenos.</p>

    <div class="contact-form">
        <form onsubmit="alert('✅ Mensaje enviado (simulación). Gracias por tu interés en Vaca Muerta.'); return false;">
            <input type="text" placeholder="Nombre completo" required>
            <input type="email" placeholder="Correo electrónico" required>
            <input type="text" placeholder="Empresa / Institución (opcional)">
            <textarea rows="4" placeholder="¿Qué te gustaría saber sobre Vaca Muerta?" required></textarea>
            <button type="submit" class="btn" style="width:100%;">Enviar mensaje</button>
        </form>
        <p style="font-size:0.85rem; color:#8a9aa8; text-align:center; margin-top:16px;">
            ⚡ Este es un sitio informativo · Datos de fuentes públicas (YPF, IAPG, gobierno de Neuquén)
        </p>
    </div>

    <div style="text-align:center; margin-top:20px;">
        <p style="color:#4a5a6a;">📍 <strong>Ubicación:</strong> Cuenca Neuquina · Neuquén · Patagonia Argentina</p>
    </div>
</div>

<!-- ===== FOOTER ===== -->
<footer>
    ⛰️ Vaca Muerta · Sitio informativo · <span>Energía para el futuro</span> · 2026
</footer>

<!-- ===== JAVASCRIPT ===== -->
<script>
    function showPage(id) {
        // Ocultar todas las páginas
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
        // Mostrar la seleccionada
        document.getElementById(id).classList.add('active');
        // Scroll al inicio
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }
</script>

</body>
</html>
