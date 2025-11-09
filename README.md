<!DOCTYPE html>
<html lang="es">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Cursos de Excel, AutoCAD, Revit, Photoshop, SketchUp e IA | SAIE</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Cursos prácticos y certificados para estudiantes y profesionales de arquitectura. Aprende Excel, AutoCAD, Revit, Photoshop, SketchUp e Inteligencia Artificial en solo 3 semanas. ¡Transforma tu carrera hoy!">
    <meta name="keywords" content="cursos arquitectura, Excel, AutoCAD, Revit, Photoshop, SketchUp, IA, cursos online, SAIE, soluciones arquitectónicas">

    <!-- Open Graph / Facebook -->
    <meta property="og:type" content="website">
    <meta property="og:title" content="Cursos de Excel, AutoCAD, Revit, Photoshop, SketchUp e IA | SAIE">
    <meta property="og:description" content="Cursos prácticos y certificados para estudiantes y profesionales de arquitectura. Aprende Excel, AutoCAD, Revit, Photoshop, SketchUp e Inteligencia Artificial en solo 3 semanas. ¡Transforma tu carrera hoy!">
    <meta property="og:image" content="https://via.placeholder.com/800x450?text=SAIE+Cursos+Arquitectura">
    <meta property="og:url" content="https://tu-dominio.com/cursos">

    <!-- Twitter -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="Cursos de Excel, AutoCAD, Revit, Photoshop, SketchUp e IA | SAIE">
    <meta name="twitter:description" content="Cursos prácticos y certificados para estudiantes y profesionales de arquitectura. Aprende Excel, AutoCAD, Revit, Photoshop, SketchUp e Inteligencia Artificial en solo 3 semanas. ¡Transforma tu carrera hoy!">
    <meta name="twitter:image" content="https://via.placeholder.com/800x450?text=SAIE+Cursos+Arquitectura">

    <!-- Favicon -->
    <link href="/favicon.ico" type="image/x-icon" rel="icon" />
    <link href="/favicon.ico" type="image/x-icon" rel="shortcut icon" />

    <!-- Google Tag Manager -->
    <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
        new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
        j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
        'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
        })(window,document,'script','dataLayer','GTM-5QPHJV6');</script>

    <!-- YouTube Player Script -->
    <script>
        var page = 5;
        const limit = 5;
        var execute = true;

        function onBlur() { console.log('blurred'); }
        function onFocus() { console.log('focused'); window.location.reload(); }

        document.addEventListener("DOMContentLoaded", function() {
            var div, n, v = document.getElementsByClassName("youtube");
            for (n = 0; n < v.length; n++) {
                div = document.createElement("div");
                div.setAttribute("data-id", v[n].dataset.id);
                div.innerHTML = labnolThumb(v[n].dataset.id);
                div.onclick = labnolIframe;
                v[n].appendChild(div);
            }
            window.onfocus = onFocus;
        });

        function labnolThumb(id) {
            var thumb = '<img class="player" src="https://via.placeholder.com/800x450?text=Video+Introductorio">';
            var play = '<img width="56px" height="56px" class="play_y" src="https://via.placeholder.com/56x56?text=▶" loading="lazy">';
            return thumb.replace("ID", id) + play;
        }

        function labnolIframe() {
            var iframe = document.createElement("iframe");
            var embed = "https://www.youtube.com/embed/ID?autoplay=1";
            iframe.setAttribute("src", embed.replace("ID", this.dataset.id));
            iframe.setAttribute("frameborder", "0");
            iframe.setAttribute("allow", "autoplay");
            iframe.setAttribute("allowfullscreen", "1");
            this.parentNode.replaceChild(iframe, this);
        }

        function more_ratings(event) {
            var curso_id = event.getAttribute('curso_id');
            page = document.getElementsByName('user_comment').length;
            xhr = new XMLHttpRequest();
            xhr.open('GET', 'https://edutin.com/ratings/get_more?id=' + curso_id + '&page=' + page, true);
            xhr.onload = function() {
                if (xhr.status === 200) {
                    try {
                        let comments = (xhr.responseText);
                        if (comments.length > 0) {
                            comments_list = document.getElementById("list_comment");
                            comments_list.insertAdjacentHTML("beforeend", comments);
                        } else {
                            execute = false;
                            boton_more = document.getElementById("ratings_get_more");
                            boton_more.style.display = "none";
                        }
                    } catch (e) { console.error(e.message); }
                } else { console.error(xhr.responseText); }
            };
            if (execute) { xhr.send(null); }
        }

        function change_src(event) {
            event.src = 'https://via.placeholder.com/56x56?text=👤';
        }

        function getCookie(nombre) {
            const cookies = document.cookie.split("; ");
            for (let cookie of cookies) {
                const [clave, valor] = cookie.split("=");
                if (clave === nombre) { return decodeURIComponent(valor); }
            }
            return null;
        }

        function send_post_certifications(event) {
            event.preventDefault();
            const newWindow = window.open('about:blank');
            newWindow.document.write('<p>Estamos procesando tu inscripción, por favor espera...</p>');
            newWindow.document.close();

            const idToken = getCookie(`accessToken`);
            const USERID = 0;

            if (idToken && USERID) {
                fetch("https://api.kc.edutin.com/b/p/certifications", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json",
                        "Authorization": `Bearer ${idToken}`
                    },
                    body: JSON.stringify({
                        data: {
                            curso_id: 12393,
                            user_id: USERID
                        }
                    })
                }).then(response => {
                    if (!response.ok) {
                        if (response.status == 401) {
                            setTimeout(() => { window.location.href = 'https://edutin.com/users/add?cursoId=12393'; }, 10);
                            newWindow.close();
                        }
                        throw new Error(`HTTP error! status: ${response.status}`);
                    }
                    return response.json();
                }).then(data => {
                    console.log("Respuesta de la API:", data);
                    setTimeout(() => { newWindow.location.href = `https://app.edutin.com/classroom?config=${encodeURIComponent(JSON.stringify(data.data.extra_data.config_redirect))}`; }, 10);
                    setTimeout(() => { window.location.reload(); }, 1000);
                }).catch(error => {
                    console.error("Error en la solicitud:", error);
                    window.location.href = 'https://edutin.com/users/add?cursoId=12393';
                    newWindow.close();
                });
            } else {
                console.error("No se encontró el token en las cookies");
                setTimeout(() => { window.location.href = 'https://edutin.com/users/add?cursoId=12393'; }, 100);
                newWindow.close();
            }
        }

        function redirectTo(url) {
            console.log(url);
            setTimeout(() => { window.open(url, '_blank'); }, 100);
            window.location.reload();
        }
    </script>

    <!-- Estilos personalizados -->
    <style>
        :root {
            --color-primary: #0047AB; /* Azul fuerte */
            --color-secondary: #F5F5DC; /* Crema */
            --color-text: #333;
            --color-bg: #FFFFFF;
            --color-accent: #FFD700;
        }

        body {
            font-family: 'Muli', sans-serif;
            background-color: var(--color-bg);
            color: var(--color-text);
            margin: 0;
            padding: 0;
        }

        .content-page {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .menu {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 20px;
            background-color: var(--color-secondary);
            border-bottom: 2px solid var(--color-primary);
        }

        .menu .left {
            display: flex;
            align-items: center;
        }

        .menu .item {
            display: flex;
            align-items: center;
            margin-right: 20px;
            text-decoration: none;
            color: var(--color-text);
        }

        .menu .logo-label {
            font-weight: bold;
            font-size: 18px;
            margin-left: 5px;
        }

        .menu .options {
            display: flex;
            align-items: center;
        }

        .dropdown {
            position: relative;
            cursor: pointer;
        }

        .dropdown:hover .dropdown-cont {
            display: block;
        }

        .dropdown-cont {
            display: none;
            position: absolute;
            top: 100%;
            left: 0;
            background-color: white;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            z-index: 1000;
        }

        .dropdown-cont li {
            padding: 10px 20px;
            border-bottom: 1px solid #eee;
        }

        .dropdown-cont li a {
            text-decoration: none;
            color: var(--color-text);
        }

        .cta {
            background-color: var(--color-primary);
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            text-decoration: none;
            font-weight: bold;
            transition: background-color 0.3s;
        }

        .cta:hover {
            background-color: #00338D;
        }

        .st-main1 {
            background-color: var(--color-secondary);
            padding: 30px;
            margin-top: 20px;
            border-radius: 10px;
        }

        .st-main1 .row {
            display: flex;
            gap: 30px;
            align-items: center;
        }

        .st-main1 .column {
            flex: 1;
        }

        .st-main1 h1 {
            font-size: 2.5em;
            color: var(--color-primary);
            margin-bottom: 10px;
        }

        .st-main1 p {
            font-size: 1em;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .youtube {
            position: relative;
            padding-bottom: 56.23%;
            height: 0;
            overflow: hidden;
            max-width: 100%;
            margin: 0;
            background: var(--color-primary);
        }

        .youtube iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            background: transparent;
        }

        .youtube .player {
            bottom: 0;
            display: block;
            left: 0px;
            margin: auto;
            max-width: 100%;
            width: 100%;
            position: absolute;
            right: 0;
            top: 16px;
            border: none;
            height: auto;
            cursor: pointer;
            -webkit-transition: .4s all;
            -moz-transition: .4s all;
            transition: .4s all;
        }

        .youtube .play_y {
            display: block;
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            top: 0;
            margin: auto;
            cursor: pointer;
            background-color: rgba(0, 0, 0, 0.3);
            border-radius: 50%;
            padding: 20px 16px 20px 24px;
        }

        .youtube img:hover {
            -webkit-filter: brightness(75%);
            filter: brightness(75%);
        }

        .statsc {
            display: flex;
            gap: 20px;
            align-items: center;
            margin-top: 20px;
        }

        .statsc .row {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .statsc .star {
            display: flex;
            gap: 5px;
        }

        .statsc .svg {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .prom-ct {
            display: flex;
            gap: 20px;
            margin-top: 30px;
        }

        .prom-ct .column {
            flex: 1;
            padding: 20px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .prom-ct h3 {
            color: var(--color-primary);
            margin-bottom: 10px;
        }

        .st-goals {
            margin-top: 40px;
            padding: 30px;
            background-color: var(--color-secondary);
            border-radius: 10px;
        }

        .st-goals h2 {
            color: var(--color-primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .st-goals .row {
            display: flex;
            gap: 30px;
            align-items: flex-start;
        }

        .st-goals .column {
            flex: 1;
        }

        .more {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .more li {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }

        .st-prog {
            margin-top: 40px;
            padding: 30px;
            background-color: white;
            border-radius: 10px;
        }

        .st-prog h2 {
            color: var(--color-primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .st-prog .row {
            display: flex;
            gap: 30px;
            align-items: flex-start;
        }

        .st-prog .column {
            flex: 1;
        }

        .tab {
            margin-bottom: 20px;
        }

        .tab input[type="checkbox"] {
            display: none;
        }

        .tab label {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 15px;
            background-color: var(--color-secondary);
            border: 1px solid var(--color-primary);
            border-radius: 5px;
            cursor: pointer;
        }

        .tab label:hover {
            background-color: #E0E0E0;
        }

        .tab-content {
            display: none;
            padding: 15px;
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-top: none;
            border-radius: 0 0 5px 5px;
        }

        .tab input[type="checkbox"]:checked ~ .tab-content {
            display: block;
        }

        .list-class a {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 8px 15px;
            text-decoration: none;
            color: var(--color-text);
            border-bottom: 1px solid #eee;
        }

        .list-class a:hover {
            background-color: #f0f0f0;
        }

        .st-certificate {
            margin-top: 40px;
            padding: 30px;
            background-color: var(--color-secondary);
            border-radius: 10px;
        }

        .st-certificate h2 {
            color: var(--color-primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .st-certificate .row {
            display: flex;
            gap: 30px;
            align-items: center;
        }

        .st-certificate .column {
            flex: 1;
        }

        .img-crt {
            max-width: 100%;
            height: auto;
            border-radius: 10px;
        }

        .title-c {
            padding: 15px;
            background-color: white;
            border-radius: 10px;
            margin-top: 20px;
            text-align: center;
        }

        .title-c h3 {
            color: var(--color-primary);
            margin-bottom: 5px;
        }

        .st-rating {
            margin-top: 40px;
            padding: 30px;
            background-color: white;
            border-radius: 10px;
        }

        .st-rating h2 {
            color: var(--color-primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .st-rating .row {
            display: flex;
            gap: 30px;
            align-items: flex-start;
        }

        .st-rating .column {
            flex: 1;
        }

        .rating {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 20px;
        }

        .r-number {
            font-size: 2.5em;
            font-weight: bold;
            color: var(--color-primary);
        }

        .t-value {
            display: flex;
            gap: 5px;
        }

        .bar {
            width: 100px;
            height: 10px;
            background-color: #eee;
            border-radius: 5px;
            overflow: hidden;
        }

        .progress {
            height: 100%;
            background-color: var(--color-primary);
        }

        .percent {
            margin-left: 10px;
            font-size: 0.9em;
        }

        .list-comments {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .list-comments li {
            display: flex;
            align-items: flex-start;
            gap: 15px;
            padding: 15px 0;
            border-bottom: 1px solid #eee;
        }

        .list-comments .user {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .list-comments .user img {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            object-fit: cover;
        }

        .list-comments .comment-info {
            margin-top: 10px;
            font-style: italic;
        }

        .load-rating {
            display: block;
            text-align: center;
            padding: 15px;
            color: var(--color-primary);
            text-decoration: none;
            font-weight: bold;
            margin-top: 20px;
        }

        .st-author {
            margin-top: 40px;
            padding: 30px;
            background-color: var(--color-secondary);
            border-radius: 10px;
        }

        .st-author h2 {
            color: var(--color-primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .st-author .row {
            display: flex;
            gap: 30px;
            align-items: flex-start;
        }

        .st-author .column {
            flex: 1;
        }

        .author {
            padding: 20px;
            background-color: white;
            border-radius: 10px;
        }

        .prof {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .prof img {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
        }

        .prof-profile {
            display: flex;
            flex-direction: column;
        }

        .prof-profile a {
            font-weight: bold;
            color: var(--color-primary);
            text-decoration: none;
        }

        .badge {
            background-color: var(--color-primary);
            color: white;
            padding: 2px 8px;
            border-radius: 10px;
            font-size: 0.8em;
            margin-top: 5px;
        }

        .st-questions {
            margin-top: 40px;
            padding: 30px;
            background-color: white;
            border-radius: 10px;
        }

        .st-questions h2 {
            color: var(--color-primary);
            margin-bottom: 20px;
            text-align: center;
        }

        .st-questions .row {
            display: flex;
            gap: 30px;
            align-items: flex-start;
        }

        .st-questions .column {
            flex: 1;
        }

        .questions {
            margin-bottom: 20px;
        }

        .questions input[type="checkbox"] {
            display: none;
        }

        .questions label {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 15px;
            background-color: var(--color-secondary);
            border: 1px solid var(--color-primary);
            border-radius: 5px;
            cursor: pointer;
        }

        .questions label:hover {
            background-color: #E0E0E0;
        }

        .questions .tab-content {
            display: none;
            padding: 15px;
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            border-top: none;
            border-radius: 0 0 5px 5px;
        }

        .questions input[type="checkbox"]:checked ~ .tab-content {
            display: block;
        }

        .footer {
            margin-top: 40px;
            padding: 30px;
            background-color: var(--color-primary);
            color: white;
        }

        .footer .main {
            display: flex;
            gap: 30px;
            flex-wrap: wrap;
        }

        .footer .column {
            flex: 1;
            min-width: 200px;
        }

        .footer ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .footer li {
            margin-bottom: 10px;
        }

        .footer a {
            color: white;
            text-decoration: none;
        }

        .footer a:hover {
            text-decoration: underline;
        }

        .social {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }

        .social a {
            display: flex;
            align-items: center;
            gap: 10px;
            color: white;
            text-decoration: none;
        }

        .legal {
            margin-top: 30px;
            text-align: center;
            font-size: 0.9em;
        }

        .legal div {
            margin-bottom: 10px;
        }

        .legal a {
            color: white;
            text-decoration: none;
        }

        .legal a:hover {
            text-decoration: underline;
        }

        @media (max-width: 768px) {
            .menu .row {
                flex-direction: column;
                align-items: flex-start;
            }

            .menu .left {
                margin-bottom: 10px;
            }

            .st-main1 .row {
                flex-direction: column;
            }

            .prom-ct {
                flex-direction: column;
            }

            .st-goals .row {
                flex-direction: column;
            }

            .st-prog .row {
                flex-direction: column;
            }

            .st-certificate .row {
                flex-direction: column;
            }

            .st-rating .row {
                flex-direction: column;
            }

            .st-author .row {
                flex-direction: column;
            }

            .st-questions .row {
                flex-direction: column;
            }

            .footer .main {
                flex-direction: column;
            }
        }
    </style>

    <link href="https://fonts.googleapis.com/css?family=Muli:400,600&display=swap" rel="stylesheet">
</head>
<body>
    <!-- Google Tag Manager (noscript) -->
    <noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-5QPHJV6" height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
    <!-- End Google Tag Manager (noscript) -->

    <div class="content-page">
        <!-- start-cta-mobile -->
        <div class="row menu mobiles">
            <div class="row s-menu">
                <div style="width: -webkit-fill-available;">
                    <p style="margin-bottom: 8px;">*Accede a este y a más de 6.000 cursos gratis</p>
                    <a class="cta menu-a" onclick="send_post_certifications(event)">Crear cuenta gratis</a>
                </div>
            </div>
        </div>
        <!-- start-cta-mobile -->

        <!-- start-menu-sticky -->
        <div class="menu-sticky">
            <div class="row menu">
                <div class="row s-menu">
                    <h2>Cursos de Excel, AutoCAD, Revit, Photoshop, SketchUp e IA</h2>
                    <div style="margin: auto 0 auto auto;">
                        <a class="cta menu-a" onclick="send_post_certifications(event)">Crear cuenta gratis</a>
                        <p style="margin: 8px 0 0;">*Accede a este y a más de 6.000 cursos gratis</p>
                    </div>
                </div>
            </div>
        </div>
        <!-- end-menu-sticky -->

        <div class="st-main1">
            <!-- start-menu -->
            <div class="menu">
                <div class="row menu-content">
                    <div class="left">
                        <a class="item" href="/">
                            <img width="18" height="32" src="https://via.placeholder.com/18x32?text=Logo" alt="SAIE">
                        </a>
                        <a class="item" href="/">
                            <div class="logo-label">SAIE</div>
                        </a>
                        <!-- start-options -->
                        <div class="options">
                            <!-- start-courses -->
                            <div class="dropdown" onclick="this.classList.toggle('active')">
                                <a class="row item-cours">
                                    <div>Cursos gratis</div>
                                    <img width="14" height="10" src="https://via.placeholder.com/14x10?text=▼" loading="lazy">
                                </a>
                                <!-- start-dropdown -->
                                <ul class="dropdown-cont courses">
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-programacion-c67">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Prog" alt="Programación">
                                                <span>Programación</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-informatica-y-computacion-c68">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Comp" alt="Informática">
                                                <span>Informática</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-herramientas-de-software-c69">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Soft" alt="Software">
                                                <span>Software</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-psicologia-y-educacion-c80">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Hum" alt="Humanidades">
                                                <span>Humanidades</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-idiomas-y-lenguas-c79">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Idi" alt="Idiomas y Lenguas">
                                                <span>Idiomas y Lenguas</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-salud-y-bienestar-c75">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Sal" alt="Salud y Bienestar">
                                                <span>Salud y Bienestar</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-deporte-y-fitness-c78">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Dep" alt="Deporte y Fitness">
                                                <span>Deporte y Fitness</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-moda-y-belleza-c72">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Mod" alt="Moda y Belleza">
                                                <span>Moda y Belleza</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-cocina-y-bebidas-c71">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Coc" alt="Cocina y Bebidas">
                                                <span>Cocina y Bebidas</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-arte-c74">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Art" alt="Arte">
                                                <span>Arte</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-diseno-grafico-c73">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Dis" alt="Diseño Gráfico">
                                                <span>Diseño Gráfico</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-marketing-y-ventas-c77">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Mar" alt="Marketing y Ventas">
                                                <span>Marketing y Ventas</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-administracion-y-negocios-c76">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Neg" alt="Negocios">
                                                <span>Negocios</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-ingenieria-c81">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Ing" alt="Ingeniería">
                                                <span>Ingeniería</span>
                                            </a>
                                        </div>
                                    </li>
                                    <li class="row">
                                        <div class="column">
                                            <a class="row" href="/cursos-de-ciencias-c82">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Cie" alt="Ciencias">
                                                <span>Ciencias</span>
                                            </a>
                                        </div>
                                        <div class="column">
                                            <a class="row" href="/cursos-de-matenimiento-y-reparacion-c70">
                                                <img width="22" height="auto" loading="lazy" src="https://via.placeholder.com/22x22?text=Rep" alt="Reparación">
                                                <span>Reparación</span>
                                            </a>
                                        </div>
                                    </li>
                                </ul>
                                <!-- end-dropdown -->
                            </div>
                            <!-- end-courses -->
                        </div>
                        <!-- end-options -->
                    </div>
                    <div class="right">
                        <div class="options">
                            <div class="row">
                                <!-- start-about-us -->
                                <div class="dropdown" onclick="this.classList.toggle('active')">
                                    <a class="row item-rigth">
                                        <div>Sobre nosotros</div>
                                        <img width="14" height="10" src="https://via.placeholder.com/14x10?text=▼">
                                    </a>
                                    <!-- start-dropdown-content-about-us -->
                                    <ul class="dropdown-cont about">
                                        <li>
                                            <a href="/about-us">Sobre SAIE</a>
                                            <div>Conoce nuestra misión y valores.</div>
                                        </li>
                                        <li>
                                            <a href="/history">Nuestra historia</a>
                                            <div>Conoce nuestra historia.</div>
                                        </li>
                                        <li>
                                            <a href="/virtual-campus">Campus virtual</a>
                                            <div>Conoce nuestra infraestructura tecnológica.</div>
                                        </li>
                                        <li>
                                            <a href="/academy-contents">Contenidos académicos</a>
                                            <div>Conoce el tipo de contenidos académicos utilizados en nuestra biblioteca de cursos.</div>
                                        </li>
                                        <li>
                                            <a href="https://edutin.us" target="_blank">Empleos</a>
                                            <div>Explore nuestros puestos vacantes, encuentre un trabajo que le encante y postule.</div>
                                        </li>
                                    </ul>
                                    <!-- end-dropdown-content-about-us -->
                                </div>
                                <!-- end-about-us -->
                                <!-- start-certificate -->
                                <a class="item-rigth" href="https://edutin.com/certificado-de-estudios">
                                    <div>Certificados</div>
                                </a>
                                <!-- end-certificate -->
                            </div>
                        </div>
                        <!-- start-login -->
                        <div class="row login">
                            <a href="https://edutin.com/users/login?cursoId=12393" target="_blank">Acceder</a>
                            <a href="https://edutin.com/users/add?cursoId=12393" target="_blank">Crear cuenta</a>
                        </div>
                        <!-- end-login -->
                        <!-- start-mobile-menu -->
                        <div class="dropdown menu-mobile" onclick="this.classList.toggle('active')">
                            <div class="row btn-menu">
                                <!-- start-icon-effect-mobile -->
                                <svg class="svg-menu" viewBox="0 0 100 100" width="60">
                                    <path class="line top" d="m 30,33 h 40 c 0,0 9.044436,-0.654587 9.044436,-8.508902 0,-7.854315 -8.024349,-11.958003 -14.89975,-10.85914 -6.875401,1.098863 -13.637059,4.171617 -13.637059,16.368042 v 40"></path>
                                    <path class="line middle" d="m 30,50 h 40"></path>
                                    <path class="line bottom" d="m 30,67 h 40 c 12.796276,0 15.357889,-11.717785 15.357889,-26.851538 0,-15.133752 -4.786586,-27.274118 -16.667516,-27.274118 -11.88093,0 -18.499247,6.994427 -18.435284,17.125656 l 0.252538,40"></path>
                                </svg>
                                <!-- end-icon-effect-mobile -->
                            </div>
                            <!-- start-dropdown-content-btn-menu -->
                            <ul class="dropdown-cont menu-btn">
                                <li class="login">
                                    <a class="btn-menu" href="/users/login?cursoId=12393" target="_blank">Acceder</a>
                                    <a class="btn-menu" href="/users/add?cursoId=12393" target="_blank">Crear cuenta</a>
                                </li>
                                <li>
                                    <a href="/about-us">Sobre SAIE</a>
                                </li>
                                <li>
                                    <a href="/history">Nuestra historia</a>
                                </li>
                                <li>
                                    <a href="/virtual-campus">Campus virtual</a>
                                </li>
                                <li>
                                    <a href="/academy-contents">Contenidos académicos</a>
                                </li>
                                <li>
                                    <a href="https://edutin.us" target="_blank">Empleos</a>
                                </li>
                                <li>
                                    <a href="/certificado-de-estudios">Certificados</a>
                                </li>
                            </ul>
                            <!-- end-dropdown-content-btn-menu -->
                        </div>
                        <!-- end-mobile-menu -->
                    </div>
                </div>
            </div>
            <!-- end-menu -->

            <div class="back">
                <div class="st-main">
                    <div class="row">
                        <div class="column">
                            <h1 class="web">Cursos de Excel, AutoCAD, Revit, Photoshop, SketchUp e IA</h1>
                            <p>¿Listo para transformar tu carrera en arquitectura? Nuestros cursos están diseñados para estudiantes y profesionales que buscan dominar las herramientas esenciales del sector: desde Excel para gestión de proyectos, hasta AutoCAD, Revit, Photoshop, SketchUp e Inteligencia Artificial para innovar en el diseño y la presentación. En solo 3 semanas y 36 horas, adquirirás habilidades prácticas que te abrirán puertas en el mercado laboral. ¡Empieza hoy y construye tu futuro!</p>
                            <!-- start-statistics -->
                            <div class="row statsc">
                                <div class="row">
                                    <ul class="row star">
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                    </ul>
                                    <div>4.9 <a href="#rating" class="view">opiniones</a></div>
                                </div>
                                <div class="row svg">
                                    <svg width="15px" height="14px" viewBox="0 0 15 14" version="1.1" xmlns="http://www.w3.org/2000/svg">
                                        <g transform="translate(-264.000000, -347.000000)" fill="#44D7B6">
                                            <g transform="translate(100.000000, 122.000000)">
                                                <g transform="translate(0.000000, 207.000000)">
                                                    <g transform="translate(164.000000, 0.000000)">
                                                        <path d="M7.5,18 C9.9813,18 12,20.0554036 12,22.5818182 C12,25.1082327 9.9813,27.1636364 7.5,27.1636364 C5.0187,27.1636364 3,25.1082327 3,22.5818182 C3,20.0554036 5.0187,18 7.5,18 Z M3.01969795,25.9798234 C3.94323401,27.2678978 5.60611864,28.129085 7.5,28.129085 C9.39388257,28.129085 11.0567681,27.2678967 11.9803038,25.9798209 C12.3800438,26.2377581 12.755077,26.5420642 13.0988667,26.8899916 C14.3248333,28.1307065 15,29.7684475 15,31.5016409 C15,31.776868 14.7761333,32 14.5,32 L0.5,32 C0.223866667,32 0,31.776868 0,31.5016409 C0,29.7684475 0.675166667,28.1307065 1.90113333,26.8899916 C2.24492188,26.5420653 2.61995642,26.23776 3.01969795,25.9798234 Z"></path>
                                                    </g>
                                                </g>
                                            </g>
                                        </g>
                                    </svg>
                                    <div>28.386 estudiantes</div>
                                </div>
                                <div class="row svg">
                                    <svg width="16px" height="14px" viewBox="0 0 16 14" version="1.1" xmlns="http://www.w3.org/2000/svg">
                                        <g transform="translate(-493.000000, -347.000000)" fill="#E04F5F">
                                            <g transform="translate(100.000000, 122.000000)">
                                                <g transform="translate(0.000000, 207.000000)">
                                                    <g transform="translate(393.000000, 0.000000)">
                                                        <path d="M14.708895,19.3943052 C12.8565595,17.5352316 9.85313471,17.5352316 8.00079922,19.3943052 L7.99925556,19.3943052 C6.14681357,17.5352316 3.14344204,17.5352316 1.29110655,19.3943052 C-0.561335435,21.2533789 -0.294229471,24.0335488 1.29110655,26.1266093 C2.97002011,28.3431273 6.03540411,32 7.99925556,32 L8.00079922,32 C9.96470386,32 13.0299814,28.3431273 14.708895,26.1266093 C16.2942843,24.0336022 16.5612837,21.2534324 14.708895,19.3943052 Z"></path>
                                                    </g>
                                                </g>
                                            </g>
                                        </g>
                                    </svg>
                                    <div>Curso gratis</div>
                                </div>
                            </div>
                            <!-- end-statistics -->
                        </div>
                        <div class="column">
                            <h1 class="mobile">Cursos de Excel, AutoCAD, Revit, Photoshop, SketchUp e IA</h1>
                            <div class="img-c">
                                <div class="youtube" data-id="ZUfQCww4DIk"></div>
                            </div>
                            <a class="cta" onclick="send_post_certifications(event)">Crear cuenta gratis</a>
                            <p style="margin-top: 8px;">*Accede a este y a más de 6.000 cursos gratis</p>
                        </div>
                    </div>
                    <!-- start-prom-ct -->
                    <div class="row prom-ct">
                        <div class="column shadow">
                            <div class="row">
                                <img width="30" heigth="46" style="margin-top: auto" src="https://via.placeholder.com/30x46?text=Mod" loading="lazy">
                                <h3>Modalidad 100% virtual</h3>
                            </div>
                            <h4>El contenido está disponible las 24 horas del día para que puedas estudiar en tu propio horario.</h4>
                        </div>
                        <div class="column shadow">
                            <div class="row">
                                <img width="30" heigth="46" src="https://via.placeholder.com/30x46?text=Cert" loading="lazy">
                                <h3>Certificado internacional</h3>
                            </div>
                            <h4>Al finalizar los cursos puedes obtener un certificado de estudios, con validez internacional. <a class="blue" href="#certificate">Ver más</a></h4>
                        </div>
                    </div>
                    <!-- end-prom-ct -->
                </div>
            </div>
        </div>

        <div class="st-goals">
            <h2>Qué aprenderás</h2>
            <div class="row">
                <!-- start-goals -->
                <div class="column">
                    <p>En este conjunto de cursos aprenderás a utilizar de manera eficiente las herramientas más demandadas en el campo de la arquitectura y el diseño. Desde la gestión de datos con Excel hasta la creación de modelos 3D con Revit y SketchUp, pasando por la edición de imágenes con Photoshop y la aplicación de Inteligencia Artificial para optimizar tus diseños. Al finalizar, estarás preparado para enfrentar cualquier proyecto profesional con confianza y precisión.</p>
                    <p><strong>Al finalizar estos cursos podrás:</strong></p>
                    <ul>
                        <li><strong>Objetivo 1.</strong> Dominar las funciones básicas y avanzadas de Excel para gestionar proyectos, presupuestos y datos de construcción.</li>
                        <li><strong>Objetivo 2.</strong> Utilizar AutoCAD para crear planos técnicos precisos y detallados.</li>
                        <li><strong>Objetivo 3.</strong> Diseñar modelos BIM con Revit, integrando arquitectura, estructura y MEP.</li>
                        <li><strong>Objetivo 4.</strong> Crear renderizados y presentaciones visuales impactantes con Photoshop y SketchUp.</li>
                        <li><strong>Objetivo 5.</strong> Aplicar técnicas de Inteligencia Artificial para optimizar diseños, automatizar tareas y generar ideas innovadoras.</li>
                    </ul>
                </div>
                <!-- end-goals -->
                <!-- start-more-info -->
                <div class="column">
                    <ul class="more">
                        <li class="row">
                            <img width="23" heigth="23" src="https://via.placeholder.com/23x23?text=Dur" loading="lazy">
                            <h4>
                                <strong>3 semanas estimadas</strong>
                                <br>
                                36 horas totales
                            </h4>
                        </li>
                        <li class="row">
                            <img width="23" heigth="23" src="https://via.placeholder.com/23x23?text=Vid" loading="lazy">
                            <h4>
                                <strong>Video clases</strong>
                                <br>
                                Aprende a través de videos explicativos y lecturas concretas
                            </h4>
                        </li>
                        <li class="row">
                            <img width="22" heigth="34" src="https://via.placeholder.com/22x34?text=Cert" loading="lazy">
                            <h4>
                                <strong>Título a certificar</strong>
                                <br>
                                Especialista en Herramientas Digitales para Arquitectura. <a class="blue" href="#certificate">By SAIE</a>
                            </h4>
                        </li>
                    </ul>
                </div>
                <!-- end-more-info -->
            </div>
        </div>

        <div class="st-prog">
            <h2>Programa del curso</h2>
            <div class="row">
                <!-- start-program -->
                <div class="column">
                    <div class="tab">
                        <input id="tab-1" type="checkbox">
                        <label for="tab-1">
                            <h4>Unidad 1. Introducción y entorno de trabajo en Excel</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 1</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Entorno de trabajo en Excel</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Personalización de la interfaz</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Atajos de teclado y eficiencia</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-2" type="checkbox">
                        <label for="tab-2">
                            <h4>Unidad 2. Operaciones básicas y manejo de datos</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 2</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Entrada y edición de datos</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Operaciones matemáticas básicas</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Formato de celdas y rangos</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Validación de datos</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-3" type="checkbox">
                        <label for="tab-3">
                            <h4>Unidad 3. Formatos y presentación de información</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 3</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Estilos y temas</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Condicionales y formatos</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Tablas dinámicas y filtros</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-4" type="checkbox">
                        <label for="tab-4">
                            <h4>Unidad 4. Fórmulas y funciones básicas</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 4</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Funciones matemáticas y estadísticas</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Funciones lógicas y de texto</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Referencias absolutas y relativas</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-5" type="checkbox">
                        <label for="tab-5">
                            <h4>Unidad 5. Gestión de listas y base de datos</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 5</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Creación y gestión de listas</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Búsqueda y filtrado de datos</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Importación y exportación de datos</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-6" type="checkbox">
                        <label for="tab-6">
                            <h4>Unidad 6. Gráficos y visualizaciones</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 6</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Tipos de gráficos y su uso</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Personalización de gráficos</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Dashboards y paneles de control</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-7" type="checkbox">
                        <label for="tab-7">
                            <h4>Unidad 7. Automatización básica con macros grabadas</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 7</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Grabación de macros</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Asignación de macros a botones</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Aplicaciones prácticas de macros</div>
                            </a>
                        </ul>
                    </div>
                    <div class="tab">
                        <input id="tab-8" type="checkbox">
                        <label for="tab-8">
                            <h4>Unidad 8. Impresión y presentación final</h4>
                            <img width="15" height="8" src="https://via.placeholder.com/15x8?text=▼"/>
                        </label>
                        <ul class="tab-content list-class">
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Introducción a la unidad 8</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Configuración de impresión</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Exportación a PDF y otros formatos</div>
                            </a>
                            <a class="row" onclick="send_post_certifications(event)">
                                <img width="10" heigth="12" src="https://via.placeholder.com/10x12?text=Play" loading="lazy">
                                <div class="name-class">Presentación final del proyecto</div>
                            </a>
                        </ul>
                    </div>
                </div>
                <!-- end-program -->
                <!-- start-related-courses -->
                <div class="column">
                    <div class="row t-related">
                        <img width="24" height="auto" loading="lazy" src="https://via.placeholder.com/24x24?text=Prod" alt="Productividad Digital">
                        <h4>Productividad Digital</h4>
                    </div>
                    <a class="row related-c" href="/curso-de-spss" title="Curso de SPSS">
                        <div class="related"><img src="https://via.placeholder.com/100x100?text=SPSS" alt="Curso de SPSS" loading="lazy"></div>
                        <div>
                            <h4>Curso de SPSS</h4>
                            <div class="free">GRATIS</div>
                        </div>
                    </a>
                    <a class="row related-c" href="/curso-de-arcgis" title="Curso de ArcGIS">
                        <div class="related"><img src="https://via.placeholder.com/100x100?text=ArcGIS" alt="Curso de ArcGIS" loading="lazy"></div>
                        <div>
                            <h4>Curso de ArcGIS</h4>
                            <div class="free">GRATIS</div>
                        </div>
                    </a>
                    <a class="row related-c" href="/curso-de-revit" title="Curso de Revit">
                        <div class="related"><img src="https://via.placeholder.com/100x100?text=Revit" alt="Curso de Revit" loading="lazy"></div>
                        <div>
                            <h4>Curso de Revit</h4>
                            <div class="free">GRATIS</div>
                        </div>
                    </a>
                    <a href="academia-de-productividad-digital-c69" class="blue">Ver más cursos gratis</a>
                </div>
                <!-- end-related-courses -->
            </div>
        </div>

        <div id="certificate" class="st-certificate">
            <div class="row">
                <div class="column">
                    <img class="img-crt" src="https://via.placeholder.com/400x300?text=Certificado" loading="lazy">
                    <h5>Puedes compartir tu Certificado en LinkedIn, en tu currículum impreso o en otros documentos.</h5>
                </div>
                <div class="column">
                    <h2>Obtenga un certificado de estudios</h2>
                    <ul>
                        <li class="row">
                            <img width="19" heigth="16" src="https://via.placeholder.com/19x16?text=Check" loading="lazy">
                            <h4>
                                <strong>Validez internacional</strong>
                                <br>
                                Evidencie su aprendizaje ante cualquier empleador o institución.
                            </h4>
                        </li>
                        <li class="row">
                            <img width="19" heigth="16" src="https://via.placeholder.com/19x16?text=Check" loading="lazy">
                            <h4>
                                <strong>Tareas calificadas</strong>
                                <br>
                                Reciba calificaciones y observaciones de todas sus actividades resueltas.
                            </h4>
                        </li>
                        <li class="row">
                            <img width="19" heigth="16" src="https://via.placeholder.com/19x16?text=Check" loading="lazy">
                            <h4>
                                <strong>Asistencia académica</strong>
                                <br>
                                Solicite asesoría sobre su proceso de certificación.
                            </h4>
                        </li>
                    </ul>
                    <div class="title-c shadow">
                        <h3>Especialista en Herramientas Digitales para Arquitectura</h3>
                        <div>36 horas certificables</div>
                    </div>
                    <p>Al finalizar los cursos puede obtener un certificado de estudios para evidenciar sus nuevos conocimientos y habilidades.</p>
                    <a class="cta" onclick="send_post_certifications(event)">Crear cuenta gratis</a>
                </div>
            </div>
        </div>

        <div id="rating" class="st-rating">
            <h2>Valoración de los estudiantes</h2>
            <div class="row">
                <div class="column">
                    <!-- start-general-rating -->
                    <div class="row">
                        <div class="rating">
                            <div class="r-number">4.9</div>
                            <div class="t-value">
                                <ul class="row star">
                                    <li class="row">
                                        <svg><use href="#star" style="opacity:1;"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star" style="opacity:1;"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star" style="opacity:1;"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star" style="opacity:1;"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star" style="opacity:1;"/></svg>
                                    </li>
                                </ul>
                            </div>
                        </div>
                        <div class="column">
                            <div class="row">
                                <div class="column bar"> <div class="progress"> <div class="progress bar" style="width:90%"></div> </div> </div>
                                <ul class="row star">
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                </ul>
                                <div class="percent">90%</div>
                            </div>
                            <div class="row">
                                <div class="column bar"> <div class="progress"> <div class="progress bar" style="width:10%"></div> </div> </div>
                                <ul class="row star">
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                </ul>
                                <div class="percent">10%</div>
                            </div>
                            <div class="row">
                                <div class="column bar"> <div class="progress"> <div class="progress bar" style="width:0%"></div> </div> </div>
                                <ul class="row star">
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                </ul>
                                <div class="percent">0%</div>
                            </div>
                            <div class="row">
                                <div class="column bar"> <div class="progress"> <div class="progress bar" style="width:0%"></div> </div> </div>
                                <ul class="row star">
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                </ul>
                                <div class="percent">0%</div>
                            </div>
                            <div class="row">
                                <div class="column bar"> <div class="progress"> <div class="progress bar" style="width:0%"></div> </div> </div>
                                <ul class="row star">
                                    <li class="row">
                                        <svg><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                    <li class="row">
                                        <svg class="opacity"><use href="#star"/></svg>
                                    </li>
                                </ul>
                                <div class="percent">0%</div>
                            </div>
                        </div>
                    </div>
                    <!-- end-general-rating -->
                    <!-- start-list-comments -->
                    <ul id="list_comment" class="list-comments">
                        <li name="user_comment" class="row">
                            <a class="user" href="/certifications/index/10448848">
                                <img width="56" height="56" loading="lazy" src="https://via.placeholder.com/56x56?text=User" alt="imagen usuario" onerror="change_src(this)"/>
                            </a>
                            <div>
                                <a href="/certifications/index/10448848"> Javier Ugena </a>
                                <div class="row">
                                    <ul class="row star">
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                    </ul>
                                    <div class="comment-date">hace 1 dia</div>
                                </div>
                            </div>
                        </li>
                        <li name="user_comment" class="row">
                            <a class="user" href="/certifications/index/10392219">
                                <img width="56" height="56" loading="lazy" src="https://via.placeholder.com/56x56?text=User" alt="imagen usuario" onerror="change_src(this)"/>
                            </a>
                            <div>
                                <a href="/certifications/index/10392219"> Ernesto Calderón </a>
                                <div class="row">
                                    <ul class="row star">
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                    </ul>
                                    <div class="comment-date">hace 5 dias</div>
                                </div>
                            </div>
                        </li>
                        <li name="user_comment" class="row">
                            <a class="user" href="/certifications/index/9985784">
                                <img width="56" height="56" loading="lazy" src="https://via.placeholder.com/56x56?text=User" alt="imagen usuario" onerror="change_src(this)"/>
                            </a>
                            <div>
                                <a href="/certifications/index/9985784"> Alain Monteiro </a>
                                <div class="row">
                                    <ul class="row star">
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                    </ul>
                                    <div class="comment-date">hace 5 dias</div>
                                </div>
                                <p class="comment-info">La introducción está excelente&nbsp;</p>
                            </div>
                        </li>
                        <li name="user_comment" class="row">
                            <a class="user" href="/certifications/index/10294233">
                                <img width="56" height="56" loading="lazy" src="https://via.placeholder.com/56x56?text=User" alt="imagen usuario" onerror="change_src(this)"/>
                            </a>
                            <div>
                                <a href="/certifications/index/10294233"> Esteban Alvarez </a>
                                <div class="row">
                                    <ul class="row star">
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                    </ul>
                                    <div class="comment-date">hace 6 dias</div>
                                </div>
                            </div>
                        </li>
                        <li name="user_comment" class="row">
                            <a class="user" href="/certifications/index/9968890">
                                <img width="56" height="56" loading="lazy" src="https://via.placeholder.com/56x56?text=User" alt="imagen usuario" onerror="change_src(this)"/>
                            </a>
                            <div>
                                <a href="/certifications/index/9968890"> César Urbano </a>
                                <div class="row">
                                    <ul class="row star">
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                        <li class="row">
                                            <svg><use href="#star" style="opacity:1;"/></svg>
                                        </li>
                                    </ul>
                                    <div class="comment-date">hace 2 semanas</div>
                                </div>
                            </div>
                        </li>
                    </ul>
                    <a id="ratings_get_more" class="row load-rating" curso_id="12393" onclick="more_ratings(this)">Ver más valoraciones</a>
                    <!-- end-list-comments -->
                </div>
            </div>
        </div>

        <div class="st-author">
            <h2>Información del autor</h2>
            <div class="row">
                <!-- start-author -->
                <div class="column">
                    <div class="author">
                        <div class="row prof">
                            <a class="user" href="/certifications/index/7057845"><img loading="lazy" src="https://via.placeholder.com/80x80?text=Adrian" alt="imagen usuario"></a>
                            <div class="prof-profile">
                                <a>Adrian Elichel</a>
                                <br>
                                <span>Arquitecto egresado</span>
                                <div class="badge">Profesor</div>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- end-author -->
            </div>
        </div>

        <div class="st-questions">
            <h2>Preguntas frecuentes</h2>
            <div class="row">
                <!-- start-questions -->
                <div class="column">
                    <div class="tab questions">
                        <input id="tab-110" type="checkbox">
                        <label for="tab-110">
                            <div>¿Puedo tomar estos cursos de manera gratuita?</div>
                            <img width="18" height="17" src="https://via.placeholder.com/18x17?text=▼">
                        </label>
                        <div class="tab-content">
                            <p>Claro que si, todos los cursos disponibles en SAIE son de acceso gratis. Los cursos también incluyen la opción de obtener un certificado de estudios para evidenciar su aprendizaje, en ese caso necesitará realizar el pago de una tarifa ajustada a la economía de su país.</p>
                        </div>
                    </div>
                    <div class="tab questions">
                        <input id="tab-120" type="checkbox">
                        <label for="tab-120">
                            <div>¿Qué incluyen los cursos de SAIE?</div>
                            <img width="18" height="17" src="https://via.placeholder.com/18x17?text=▼">
                        </label>
                        <div class="tab-content">
                            <p>Los cursos de SAIE incluyen videos, lecturas, evaluaciones, actividades y proyectos prácticos basados en situaciones de la vida real, que le ayudarán a colocar inmediatamente en práctica los conocimientos del curso.</p>
                        </div>
                    </div>
                    <div class="tab questions">
                        <input id="tab-130" type="checkbox">
                        <label for="tab-130">
                            <div>¿Cómo obtengo el certificado de estudios?</div>
                            <img width="18" height="17" src="https://via.placeholder.com/18x17?text=▼">
                        </label>
                        <div class="tab-content">
                            <p>Para obtener el certificado de estudios necesitará inscribirse al curso de su interés, seleccionar la opción "estudiar con certificado" y realizar el pago de una tarifa ajustada a la economía de su país. Finalmente, necesitará aprobar el curso con una calificación mínima para recibir su certificación.</p>
                        </div>
                    </div>
                </div>
                <!-- end-questions -->
                <div class="column"></div>
            </div>
        </div>

        <!-- start-footer -->
        <div class="footer">
            <div class="back-blue-dark">
                <div class="main">
                    <div class="row">
                        <div class="about column">
                            <ul>
                                <li>Sobre nosotros</li>
                                <li><a href="/about-us">Sobre SAIE</a></li>
                                <li><a href="/history">Nuestra historia</a></li>
                                <li><a href="/virtual-campus">Campus virtual</a></li>
                                <li><a href="/academy-contents">Contenidos académicos</a></li>
                                <li><a href="https://blog.edutin.com/academy-contents">Nuestro Blog</a></li>
                                <li><a href="https://edutin.us" target="_blank">Empleos</a></li>
                            </ul>
                        </div>
                        <div class="column">
                            <ul>
                                <li>Productos y servicios</li>
                                <li><a href="/cursos-gratis">Cursos gratis</a></li>
                                <li><a href="/cursos-para-empresas">Cursos para empresas</a></li>
                                <li><a href="/certificado-de-estudios">Certificación de cursos</a></li>
                                <li><a href="/programas-de-certificacion">Programas de certificación</a></li>
                                <li><a href="/capacitacion-para-equipos">Capacitación para equipos</a></li>
                                <li><a href="/capacitacion-para-empresas">Capacitación para empresas</a></li>
                                <li><a href="/programa-de-afiliados">Programa de afiliados</a></li>
                                <li><a href="/prices">Precios</a></li>
                            </ul>
                        </div>
                        <div class="column">
                            <ul>
                                <li>Ayuda</li>
                                <li><a target="_blank" href="/helps/home">Centro de ayuda</a></li>
                                <li><a target="_blank" href="/helps/account">Cuenta de estudiante</a></li>
                                <li><a target="_blank" href="/helps/courses">Cursos gratis</a></li>
                                <li><a target="_blank" href="/helps/certificates">Certificación de cursos</a></li>
                                <li><a target="_blank" href="/helps/classroom">Aula de clases</a></li>
                                <li><a target="_blank" href="/helps/payments">Pagos y reembolsos</a></li>
                            </ul>
                        </div>
                        <div class="column">
                            <ul class="talk-person-real">
                                <li>Contacto</li>
                                <li><a href="tel:5519192522">Llámanos: (5519192522)</a></li>
                                <li><a href="https://www.facebook.com/share/1TbwnWYYiC/" target="_blank">Visítanos en Facebook</a></li>
                            </ul>
                            <ul>
                                <li>Siguenos en redes</li>
                            </ul>
                            <div class="social">
                                <a target="_blank" href="https://www.facebook.com/share/1TbwnWYYiC/" aria-label="visitanos en Facebook">
                                    <img class="hover-out ls-is-cached lazyloaded" data-src="https://via.placeholder.com/50x50?text=FB" src="https://via.placeholder.com/50x50?text=FB" alt="facebook icon" height="100%" width="100%">
                                    <img class="hover-in lazyload" data-src="https://via.placeholder.com/50x50?text=FBH" src="https://via.placeholder.com/50x50?text=FBH" alt="facebook icon" height="100%" width="100%">
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="back-blue-light">
                <div class="legal">
                    <div>
                        <a target="_blank" href="/pages/terminos">Términos y condiciones</a>
                        <span class="dot">.</span>
                        <a target="_blank" href="/pages/politicas">Política de privacidad</a>
                    </div>
                    <h4>SAIE es una incorporación de educación virtual, constituida en México.</h4>
                    <h4>© 2025 SAIE. Todos los derechos reservados.</h4>
                </div>
            </div>
        </div>
        <!-- end-footer -->
    </div>

    <svg style="display:none" fill="none" xmlns="http://www.w3.org/2000/svg" version="2.0">
        <defs>
            <symbol id="star" viewBox="0 0 24 24">
                <path fill-rule="evenodd" clip-rule="evenodd" d="M17.5614 21.0007C17.4034 21.0007 17.2444 20.9637 17.0984 20.8877L11.9994 18.2237L6.90138 20.8877C6.56338 21.0627 6.15538 21.0327 5.84938 20.8087C5.54138 20.5847 5.38838 20.2057 5.45338 19.8307L6.42438 14.2027L2.30438 10.2177C2.03038 9.95272 1.93138 9.55472 2.04838 9.19072C2.16538 8.82872 2.47838 8.56372 2.85638 8.50972L8.55638 7.68172L11.1044 2.55572C11.4424 1.87572 12.5574 1.87572 12.8954 2.55572L15.4434 7.68172L21.1434 8.50972C21.5214 8.56372 21.8344 8.82872 21.9514 9.19072C22.0684 9.55472 21.9694 9.95272 21.6954 10.2177L17.5754 14.2027L18.5464 19.8307C18.6114 20.2057 18.4574 20.5847 18.1504 20.8087C17.9764 20.9367 17.7694 21.0007 17.5614 21.0007Z"/>
                <path/>
            </symbol>
        </defs>
        <use href="#star"/>
    </svg>

    <!-- Google Tag Manager (noscript) -->
    <noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-5QPHJV6" height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
    <!-- End Google Tag Manager (noscript) -->
</body>
</html>
