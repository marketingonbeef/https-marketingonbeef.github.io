<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
    <title>Onbeef - Tecnologia para Açougues | Delivery, Gestão e Crescimento</title>
    <meta name="description" content="A plataforma completa para açougues que querem vender mais com delivery, gestão inteligente e CRM automatizado.">
    <link rel="icon" href="https://i.ibb.co/YBC98Rns/Logo-Onbeef-1.png" type="image/png">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <style>
        *, *::before, *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --red: #C0392B;
            --red-light: #E74C3C;
            --red-dark: #96281B;
            --dark-bg: #0A0A0A;
            --dark-card: #111111;
            --dark-border: #222222;
            --text-primary: #FFFFFF;
            --text-secondary: #AAAAAA;
            --text-muted: #666666;
            --gradient-red: linear-gradient(135deg, #C0392B, #E74C3C);
        }

        html { scroll-behavior: smooth; }

        body {
            font-family: 'Poppins', sans-serif;
            background: var(--dark-bg);
            color: var(--text-primary);
            overflow-x: hidden;
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
        }

        a { text-decoration: none; color: inherit; }
        ul { list-style: none; }
        img { max-width: 100%; height: auto; display: block; }

        .container {
            width: 100%;
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 16px;
        }

        /* ===== BUTTONS ===== */
        .btn-primary {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            background: var(--gradient-red);
            color: #fff;
            padding: 14px 28px;
            border-radius: 50px;
            font-weight: 700;
            font-size: 0.9rem;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(192, 57, 43, 0.4);
        }

        .btn-secondary {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            background: transparent;
            color: var(--red-light);
            padding: 12px 26px;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.9rem;
            border: 2px solid var(--red);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .btn-secondary:hover {
            background: var(--red);
            color: #fff;
        }

        /* ===== NAVBAR ===== */
        .navbar {
            position: fixed;
            top: 0; left: 0;
            width: 100%;
            z-index: 1000;
            padding: 12px 0;
            background: rgba(10, 10, 10, 0.9);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border-bottom: 1px solid transparent;
            transition: all 0.3s ease;
        }

        .navbar.scrolled { border-bottom-color: var(--dark-border); }

        .navbar .container {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .navbar-logo img { height: 36px; }

        .navbar-links {
            display: flex;
            align-items: center;
            gap: 28px;
        }

        .navbar-links a {
            color: var(--text-secondary);
            font-weight: 500;
            font-size: 0.85rem;
            transition: color 0.3s;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .navbar-links a:hover { color: var(--red-light); }

        .navbar-cta {
            background: var(--gradient-red) !important;
            color: #fff !important;
            padding: 8px 20px !important;
            border-radius: 50px;
            font-weight: 700 !important;
        }

        .navbar-toggle {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            padding: 5px;
            z-index: 1001;
        }

        .navbar-toggle span {
            width: 26px;
            height: 2px;
            background: var(--red-light);
            transition: all 0.3s ease;
            border-radius: 2px;
        }

        .navbar-toggle.active span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
        .navbar-toggle.active span:nth-child(2) { opacity: 0; }
        .navbar-toggle.active span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

        .nav-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.6);
            z-index: 998;
        }

        .nav-overlay.active { display: block; }

        /* ===== HERO ===== */
        .hero {
            position: relative;
            min-height: 100vh;
            display: flex;
            align-items: center;
        }

        .hero-bg {
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
        }

        .hero-bg img {
            width: 100%; height: 100%;
            object-fit: cover;
        }

        .hero-bg::after {
            content: '';
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: linear-gradient(to right, rgba(10,10,10,0.95) 0%, rgba(10,10,10,0.8) 50%, rgba(10,10,10,0.4) 100%);
        }

        .hero .container {
            position: relative;
            z-index: 1;
            padding-top: 80px;
            padding-bottom: 40px;
        }

        .hero-content { max-width: 600px; }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: rgba(192, 57, 43, 0.12);
            border: 1px solid rgba(192, 57, 43, 0.3);
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 0.75rem;
            color: var(--red-light);
            margin-bottom: 20px;
            font-weight: 500;
        }

        .hero-content h1 {
            font-size: 2.8rem;
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 16px;
        }

        .hero-content h1 span {
            background: var(--gradient-red);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero-content > p {
            font-size: 1.05rem;
            color: var(--text-secondary);
            margin-bottom: 28px;
            line-height: 1.6;
        }

        .hero-buttons {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
        }

        .hero-stats {
            display: flex;
            gap: 32px;
            margin-top: 36px;
            padding-top: 28px;
            border-top: 1px solid var(--dark-border);
        }

        .hero-stat h3 {
            font-size: 1.6rem;
            font-weight: 800;
            background: var(--gradient-red);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
        }

        .hero-stat p {
            font-size: 0.75rem;
            color: var(--text-muted);
        }

        /* ===== SECTION TITLES ===== */
        .section-title {
            text-align: center;
            margin-bottom: 40px;
        }

        .section-title h2 {
            font-size: 2rem;
            font-weight: 800;
            margin-bottom: 10px;
            line-height: 1.2;
        }

        .section-title h2 span {
            background: var(--gradient-red);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .section-title p {
            color: var(--text-secondary);
            font-size: 0.95rem;
            max-width: 500px;
            margin: 0 auto;
        }

        /* ===== BENEFITS ===== */
        .benefits {
            padding: 60px 0;
            background: var(--dark-bg);
        }

        .benefits-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .benefit-card {
            background: var(--dark-card);
            border: 1px solid var(--dark-border);
            border-radius: 16px;
            padding: 28px 22px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .benefit-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 3px;
            background: var(--gradient-red);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .benefit-card:hover::before { transform: scaleX(1); }

        .benefit-card:hover {
            transform: translateY(-4px);
            border-color: rgba(192, 57, 43, 0.3);
        }

        .benefit-icon {
            width: 48px; height: 48px;
            border-radius: 12px;
            background: rgba(192, 57, 43, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 14px;
            font-size: 1.2rem;
            color: var(--red-light);
        }

        .benefit-card h3 {
            font-size: 1rem;
            font-weight: 700;
            margin-bottom: 8px;
        }

        .benefit-card p {
            color: var(--text-secondary);
            font-size: 0.85rem;
            line-height: 1.5;
        }

        /* ===== APP SHOWCASE ===== */
        .app-showcase {
            padding: 60px 0;
            background: var(--dark-card);
            overflow: hidden;
        }

        .app-showcase-inner {
            display: flex;
            align-items: center;
            gap: 60px;
        }

        .app-showcase-text { flex: 1; }

        .app-showcase-text h2 {
            font-size: 2rem;
            font-weight: 800;
            margin-bottom: 16px;
            line-height: 1.2;
        }

        .app-showcase-text h2 span {
            background: var(--gradient-red);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .app-showcase-text > p {
            color: var(--text-secondary);
            font-size: 0.95rem;
            line-height: 1.6;
            margin-bottom: 24px;
        }

        .app-features {
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .app-feature {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .app-feature-icon {
            width: 36px; height: 36px;
            min-width: 36px;
            border-radius: 10px;
            background: rgba(192, 57, 43, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--red-light);
            font-size: 0.85rem;
        }

        .app-feature span {
            color: var(--text-secondary);
            font-size: 0.88rem;
            font-weight: 500;
        }

        .phone-mockup-wrapper {
            flex-shrink: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .phone-image {
            width: 280px;
            border-radius: 32px;
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.5);
            position: relative;
            z-index: 1;
        }

        .phone-glow {
            position: absolute;
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 400px; height: 400px;
            background: radial-gradient(circle, rgba(192, 57, 43, 0.12) 0%, transparent 70%);
            pointer-events: none;
            z-index: 0;
        }

        /* ===== PLANS ===== */
        .plans {
            padding: 60px 0;
            background: var(--dark-bg);
        }

        .plans-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            align-items: start;
        }

        .plan-card {
            background: var(--dark-card);
            border: 1px solid var(--dark-border);
            border-radius: 20px;
            padding: 32px 24px;
            position: relative;
            transition: all 0.3s ease;
        }

        .plan-card:hover {
            transform: translateY(-6px);
            border-color: rgba(192, 57, 43, 0.3);
            box-shadow: 0 0 25px rgba(192, 57, 43, 0.15);
        }

        .plan-card.featured { border-color: var(--red); }

        .plan-badge {
            position: absolute;
            top: -12px; left: 50%;
            transform: translateX(-50%);
            background: var(--gradient-red);
            color: #fff;
            padding: 5px 20px;
            border-radius: 50px;
            font-size: 0.7rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            white-space: nowrap;
        }

        .plan-header {
            text-align: center;
            margin-bottom: 20px;
            padding-bottom: 20px;
            border-bottom: 1px solid var(--dark-border);
        }

        .plan-header h3 {
            font-size: 1.3rem;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 4px;
        }

        .plan-header .plan-subtitle {
            color: var(--red-light);
            font-size: 0.8rem;
            font-weight: 600;
            font-style: italic;
        }

        .plan-price { text-align: center; margin: 18px 0; }

        .plan-price .currency {
            font-size: 1rem;
            font-weight: 600;
            color: var(--red-light);
            vertical-align: top;
            line-height: 2;
        }

        .plan-price .amount {
            font-size: 2.4rem;
            font-weight: 900;
            background: var(--gradient-red);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1;
        }

        .plan-price .period {
            font-size: 0.8rem;
            color: var(--text-muted);
            display: block;
            margin-top: 4px;
        }

        .plan-features { margin: 20px 0; }

        .plan-features li {
            display: flex;
            align-items: flex-start;
            gap: 10px;
            padding: 6px 0;
            color: var(--text-secondary);
            font-size: 0.82rem;
            line-height: 1.4;
        }

        .plan-features li i {
            color: var(--red-light);
            margin-top: 3px;
            font-size: 0.65rem;
            flex-shrink: 0;
        }

        .plan-features .sub-item {
            padding-left: 24px;
            font-size: 0.78rem;
            color: var(--text-muted);
        }

        .plan-cta { text-align: center; margin-top: 24px; }

        .plan-cta .btn-primary,
        .plan-cta .btn-secondary {
            width: 100%;
            justify-content: center;
            padding: 12px 20px;
            font-size: 0.85rem;
        }

        .plan-signature {
            text-align: center;
            font-style: italic;
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-top: 12px;
        }

        /* ===== FAQ ===== */
        .faq {
            padding: 60px 0;
            background: var(--dark-card);
        }

        .faq-list { max-width: 700px; margin: 0 auto; }

        .faq-item { border-bottom: 1px solid var(--dark-border); }

        .faq-question {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 0;
            cursor: pointer;
            transition: color 0.3s;
        }

        .faq-question:hover { color: var(--red-light); }

        .faq-question h3 {
            font-size: 0.95rem;
            font-weight: 600;
            padding-right: 16px;
        }

        .faq-question i {
            color: var(--red-light);
            transition: transform 0.3s;
            flex-shrink: 0;
            font-size: 0.85rem;
        }

        .faq-item.active .faq-question i { transform: rotate(45deg); }

        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease;
        }

        .faq-item.active .faq-answer {
            max-height: 200px;
            padding-bottom: 18px;
        }

        .faq-answer p {
            color: var(--text-secondary);
            font-size: 0.88rem;
            line-height: 1.6;
        }

        /* ===== CTA FINAL ===== */
        .cta-final {
            padding: 60px 0;
            background: var(--dark-bg);
            text-align: center;
        }

        .cta-final h2 {
            font-size: 2.2rem;
            font-weight: 900;
            margin-bottom: 14px;
            line-height: 1.2;
        }

        .cta-final h2 span {
            background: var(--gradient-red);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .cta-final p {
            color: var(--text-secondary);
            font-size: 1rem;
            max-width: 480px;
            margin: 0 auto 28px;
        }

        /* ===== FOOTER ===== */
        .footer {
            padding: 36px 0 24px;
            background: var(--dark-card);
            border-top: 1px solid var(--dark-border);
        }

        .footer .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 18px;
        }

        .footer-logo img { height: 32px; }

        .footer-social { display: flex; gap: 12px; }

        .footer-social a {
            width: 40px; height: 40px;
            border-radius: 50%;
            border: 1px solid var(--dark-border);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-secondary);
            transition: all 0.3s;
            font-size: 1rem;
        }

        .footer-social a:hover {
            border-color: var(--red-light);
            color: var(--red-light);
        }

        .footer-copy { color: var(--text-muted); font-size: 0.75rem; }

        /* ===== WHATSAPP FLOAT ===== */
        .whatsapp-float {
            position: fixed;
            bottom: 20px; right: 20px;
            z-index: 999;
            width: 54px; height: 54px;
            border-radius: 50%;
            background: #25D366;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-size: 1.6rem;
            box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4);
            transition: all 0.3s;
            animation: pulse-wa 2s infinite;
        }

        .whatsapp-float:hover { transform: scale(1.1); }

        @keyframes pulse-wa {
            0%, 100% { box-shadow: 0 4px 20px rgba(37, 211, 102, 0.4); }
            50% { box-shadow: 0 4px 20px rgba(37, 211, 102, 0.7); }
        }

        /* ===== FADE IN ===== */
        .fade-in {
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* ============================================
           TABLET (max-width: 992px)
           ============================================ */
        @media (max-width: 992px) {
            .navbar-links {
                position: fixed;
                top: 0; right: -100%;
                width: 75%;
                max-width: 300px;
                height: 100vh;
                height: 100dvh;
                background: var(--dark-card);
                flex-direction: column;
                align-items: flex-start;
                padding: 80px 30px 30px;
                gap: 20px;
                transition: right 0.35s ease;
                border-left: 1px solid var(--dark-border);
                z-index: 999;
            }

            .navbar-links.active { right: 0; }
            .navbar-toggle { display: flex; }

            .hero-content h1 { font-size: 2.2rem; }

            .benefits-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 16px;
            }

            .app-showcase-inner {
                flex-direction: column;
                gap: 36px;
                text-align: center;
            }

            .app-showcase-text h2 { font-size: 1.6rem; }
            .app-features { align-items: center; }
            .phone-image { width: 240px; }

            .plans-grid {
                grid-template-columns: 1fr;
                max-width: 420px;
                margin: 0 auto;
                gap: 24px;
            }
        }

        /* ============================================
           MOBILE (max-width: 640px)
           ============================================ */
        @media (max-width: 640px) {
            .container { padding: 0 14px; }

            .navbar { padding: 10px 0; }
            .navbar-logo img { height: 30px; }

            .navbar-links {
                width: 80%;
                padding: 70px 24px 24px;
                gap: 16px;
            }

            .navbar-links a { font-size: 0.9rem; }

            .navbar-cta {
                padding: 10px 20px !important;
                font-size: 0.85rem !important;
                width: 100%;
                text-align: center;
                justify-content: center;
            }

            .hero { min-height: auto; }

            .hero-bg::after {
                background: linear-gradient(to bottom, rgba(10,10,10,0.9) 0%, rgba(10,10,10,0.85) 60%, rgba(10,10,10,0.7) 100%);
            }

            .hero .container {
                padding-top: 70px;
                padding-bottom: 32px;
            }

            .hero-badge {
                font-size: 0.68rem;
                padding: 5px 12px;
                margin-bottom: 14px;
            }

            .hero-content h1 {
                font-size: 1.7rem;
                margin-bottom: 12px;
            }

            .hero-content > p {
                font-size: 0.88rem;
                margin-bottom: 20px;
                line-height: 1.5;
            }

            .hero-buttons {
                flex-direction: column;
                gap: 10px;
            }

            .hero-buttons .btn-primary,
            .hero-buttons .btn-secondary {
                width: 100%;
                padding: 13px 20px;
                font-size: 0.85rem;
            }

            .hero-stats {
                gap: 0;
                justify-content: space-between;
                margin-top: 24px;
                padding-top: 20px;
            }

            .hero-stat { text-align: center; flex: 1; }
            .hero-stat h3 { font-size: 1.3rem; }
            .hero-stat p { font-size: 0.68rem; }

            .benefits, .app-showcase, .plans, .faq, .cta-final {
                padding: 40px 0;
            }

            .section-title { margin-bottom: 28px; }
            .section-title h2 { font-size: 1.4rem; }
            .section-title p { font-size: 0.85rem; }

            .benefits-grid {
                grid-template-columns: 1fr;
                gap: 12px;
            }

            .benefit-card {
                padding: 20px 18px;
                border-radius: 14px;
                display: flex;
                gap: 14px;
                align-items: flex-start;
            }

            .benefit-icon {
                width: 42px; height: 42px;
                min-width: 42px;
                border-radius: 10px;
                margin-bottom: 0;
                font-size: 1rem;
            }

            .benefit-card h3 { font-size: 0.9rem; margin-bottom: 4px; }
            .benefit-card p { font-size: 0.8rem; }

            .app-showcase-inner {
                flex-direction: column;
                gap: 28px;
                text-align: center;
            }

            .app-showcase-text h2 { font-size: 1.4rem; }
            .app-showcase-text > p { font-size: 0.85rem; margin-bottom: 18px; }

            .app-features { align-items: flex-start; gap: 10px; }
            .app-feature-icon { width: 32px; height: 32px; min-width: 32px; font-size: 0.75rem; border-radius: 8px; }
            .app-feature span { font-size: 0.8rem; }

            .phone-image { width: 220px; border-radius: 24px; }
            .phone-glow { width: 280px; height: 280px; }

            .plans-grid {
                grid-template-columns: 1fr;
                max-width: 100%;
                gap: 20px;
            }

            .plan-card {
                padding: 24px 18px;
                border-radius: 16px;
            }

            .plan-card.featured { transform: none; }
            .plan-card.featured:hover { transform: translateY(-4px); }

            .plan-header { margin-bottom: 14px; padding-bottom: 14px; }
            .plan-header h3 { font-size: 1.1rem; letter-spacing: 1px; }
            .plan-header .plan-subtitle { font-size: 0.75rem; }

            .plan-price { margin: 14px 0; }
            .plan-price .currency { font-size: 0.9rem; }
            .plan-price .amount { font-size: 2rem; }
            .plan-price .period { font-size: 0.75rem; }

            .plan-features { margin: 16px 0; }
            .plan-features li { padding: 4px 0; font-size: 0.8rem; gap: 8px; }
            .plan-features li i { font-size: 0.6rem; }
            .plan-features .sub-item { padding-left: 20px; font-size: 0.75rem; }

            .plan-cta { margin-top: 18px; }
            .plan-cta .btn-primary,
            .plan-cta .btn-secondary { padding: 11px 18px; font-size: 0.82rem; }

            .faq-question { padding: 14px 0; }
            .faq-question h3 { font-size: 0.88rem; }
            .faq-question i { font-size: 0.8rem; }
            .faq-answer p { font-size: 0.82rem; }
            .faq-item.active .faq-answer { padding-bottom: 14px; }

            .cta-final h2 { font-size: 1.5rem; }
            .cta-final p { font-size: 0.88rem; margin-bottom: 20px; }
            .cta-final .btn-primary {
                width: 100%;
                padding: 14px 20px;
                font-size: 0.88rem;
            }

            .footer { padding: 28px 0 20px; }
            .footer-logo img { height: 28px; }
            .footer-social a { width: 36px; height: 36px; font-size: 0.9rem; }
            .footer-copy { font-size: 0.7rem; }

            .whatsapp-float {
                width: 48px; height: 48px;
                bottom: 16px; right: 16px;
                font-size: 1.4rem;
            }
        }

        /* ============================================
           SMALL MOBILE (max-width: 380px)
           ============================================ */
        @media (max-width: 380px) {
            .hero-content h1 { font-size: 1.45rem; }
            .hero-stat h3 { font-size: 1.1rem; }
            .hero-stat p { font-size: 0.62rem; }
            .section-title h2 { font-size: 1.25rem; }
            .plan-price .amount { font-size: 1.8rem; }
            .phone-image { width: 190px; border-radius: 20px; }
        }
    </style>
</head>
<body>

    <!-- NAVBAR -->
    <nav class="navbar" id="navbar">
        <div class="container">
            <a href="#" class="navbar-logo">
                <img src="https://i.ibb.co/YBC98Rns/Logo-Onbeef-1.png" alt="Onbeef">
            </a>
            <div class="navbar-links" id="navLinks">
                <a href="#beneficios">Benefícios</a>
                <a href="#sistema">Sistema</a>
                <a href="#planos">Planos</a>
                <a href="#faq">FAQ</a>
                <a href="https://wa.me/5562994512211?text=Quero%20conhecer%20a%20Onbeef" target="_blank" class="navbar-cta">
                    <i class="fab fa-whatsapp"></i> Fale Conosco
                </a>
            </div>
            <div class="navbar-toggle" id="navToggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>
    <div class="nav-overlay" id="navOverlay"></div>

    <!-- HERO -->
    <section class="hero" id="inicio">
        <div class="hero-bg">
            <img src="https://i.ibb.co/s9C34hZp/grilled-fillet-steak-rustic-meal-wood-generated-by-ai.jpg" alt="Carne grelhada premium">
        </div>
        <div class="container">
            <div class="hero-content">
                <div class="hero-badge">
                    <i class="fas fa-bolt"></i> Seu açougue. Seu delivery. Nossa tecnologia.
                </div>
                <h1>Seu açougue no <span>próximo nível</span> com a Onbeef</h1>
                <p>Delivery, gestão de pedidos, CRM, fidelização e muito mais. Tudo em uma plataforma feita exclusivamente para o seu açougue vender mais.</p>
                <div class="hero-buttons">
                    <a href="https://wa.me/5562994512211?text=Quero%20conhecer%20a%20Onbeef" target="_blank" class="btn-primary">
                        <i class="fab fa-whatsapp"></i> Quero conhecer a Onbeef
                    </a>
                    <a href="#planos" class="btn-secondary">
                        <i class="fas fa-tag"></i> Ver Planos
                    </a>
                </div>
                <div class="hero-stats">
                    <div class="hero-stat">
                        <h3>500+</h3>
                        <p>Açougues atendidos</p>
                    </div>
                    <div class="hero-stat">
                        <h3>98%</h3>
                        <p>Satisfação dos clientes</p>
                    </div>
                    <div class="hero-stat">
                        <h3>3x</h3>
                        <p>Mais vendas no delivery</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- BENEFITS -->
    <section class="benefits" id="beneficios">
        <div class="container">
            <div class="section-title fade-in">
                <h2>Por que escolher a <span>Onbeef</span>?</h2>
                <p>Tudo o que seu açougue precisa para dominar o mercado.</p>
            </div>
            <div class="benefits-grid">
                <div class="benefit-card fade-in">
                    <div class="benefit-icon"><i class="fas fa-store"></i></div>
                    <div>
                        <h3>Catálogo Digital Completo</h3>
                        <p>Vitrine online com todos os produtos, fotos e preços atualizados em tempo real.</p>
                    </div>
                </div>
                <div class="benefit-card fade-in">
                    <div class="benefit-icon"><i class="fas fa-motorcycle"></i></div>
                    <div>
                        <h3>Delivery Integrado</h3>
                        <p>Receba pedidos online e gerencie entregas direto pelo painel.</p>
                    </div>
                </div>
                <div class="benefit-card fade-in">
                    <div class="benefit-icon"><i class="fas fa-bullhorn"></i></div>
                    <div>
                        <h3>Ferramentas de Marketing</h3>
                        <p>Banners, cupons e anúncios para atrair novos clientes.</p>
                    </div>
                </div>
                <div class="benefit-card fade-in">
                    <div class="benefit-icon"><i class="fas fa-users"></i></div>
                    <div>
                        <h3>CRM Inteligente</h3>
                        <p>Conheça seus clientes e envie ofertas personalizadas automaticamente.</p>
                    </div>
                </div>
                <div class="benefit-card fade-in">
                    <div class="benefit-icon"><i class="fas fa-star"></i></div>
                    <div>
                        <h3>Programa de Fidelização</h3>
                        <p>Sistema de pontos que faz o cliente voltar sempre.</p>
                    </div>
                </div>
                <div class="benefit-card fade-in">
                    <div class="benefit-icon"><i class="fab fa-whatsapp"></i></div>
                    <div>
                        <h3>Loja no WhatsApp</h3>
                        <p>Receba pedidos direto onde seus clientes já estão.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- APP SHOWCASE -->
    <section class="app-showcase" id="sistema">
        <div class="container">
            <div class="app-showcase-inner fade-in">
                <div class="app-showcase-text">
                    <h2>A experiência que seu cliente <span>merece</span></h2>
                    <p>Seus clientes escolhem os cortes, personalizam o pedido e compram direto pelo celular. Simples, rápido e bonito.</p>
                    <div class="app-features">
                        <div class="app-feature">
                            <div class="app-feature-icon"><i class="fas fa-image"></i></div>
                            <span>Fotos reais dos produtos em alta qualidade</span>
                        </div>
                        <div class="app-feature">
                            <div class="app-feature-icon"><i class="fas fa-weight-hanging"></i></div>
                            <span>Pedido por kg com peso variável</span>
                        </div>
                        <div class="app-feature">
                            <div class="app-feature-icon"><i class="fas fa-utensils"></i></div>
                            <span>Sugestão de acompanhamentos no carrinho</span>
                        </div>
                        <div class="app-feature">
                            <div class="app-feature-icon"><i class="fas fa-credit-card"></i></div>
                            <span>Pagamento online integrado (Pix, cartão)</span>
                        </div>
                        <div class="app-feature">
                            <div class="app-feature-icon"><i class="fas fa-truck"></i></div>
                            <span>Rastreio de entrega em tempo real</span>
                        </div>
                    </div>
                </div>
                <div class="phone-mockup-wrapper">
                    <div class="phone-glow"></div>
                    <img src="https://i.ibb.co/HJww9Qj/corte-nobre-print.png" alt="App Onbeef - Catálogo de Cortes" class="phone-image">
                </div>
            </div>
        </div>
    </section>

    <!-- PLANS -->
    <section class="plans" id="planos">
        <div class="container">
            <div class="section-title fade-in">
                <h2>Escolha o <span>plano ideal</span> pro seu açougue</h2>
            </div>
            <div class="plans-grid">
                <!-- PROFISSIONAL -->
                <div class="plan-card fade-in">
                    <div class="plan-header">
                        <h3>Profissional</h3>
                        <p class="plan-subtitle">Dominar a operação</p>
                    </div>
                    <div class="plan-price">
                        <span class="currency">R$</span>
                        <span class="amount">289,90</span>
                        <span class="period">/mês</span>
                    </div>
                    <ul class="plan-features">
                        <li><i class="fas fa-check"></i> Catálogo digital completo</li>
                        <li><i class="fas fa-check"></i> Gestor de pedidos</li>
                        <li><i class="fas fa-check"></i> Gestor de produtos</li>
                        <li><i class="fas fa-check"></i> Sugestão de produtos nos itens e no carrinho</li>
                        <li><i class="fas fa-check"></i> Ferramentas de marketing</li>
                        <li class="sub-item"><i class="fas fa-circle" style="font-size:0.35rem"></i> Banner / Cupom / Ads</li>
                        <li><i class="fas fa-check"></i> Pagamento online</li>
                        <li><i class="fas fa-check"></i> Impressão automática</li>
                        <li><i class="fas fa-check"></i> Loja integrada ao WhatsApp</li>
                        <li><i class="fas fa-check"></i> CRM</li>
                        <li><i class="fas fa-check"></i> Até 10 usuários</li>
                        <li><i class="fas fa-check"></i> Suporte via chat</li>
                        <li><i class="fas fa-check"></i> Ativação via vídeos</li>
                    </ul>
                    <div class="plan-cta">
                        <a href="https://wa.me/5562994512211?text=Quero%20o%20plano%20Profissional%20da%20Onbeef" target="_blank" class="btn-secondary">
                            <i class="fab fa-whatsapp"></i> Quero esse plano
                        </a>
                    </div>
                </div>

                <!-- EXPERT -->
                <div class="plan-card featured fade-in">
                    <div class="plan-badge">⭐ Mais Popular</div>
                    <div class="plan-header">
                        <h3>Expert</h3>
                        <p class="plan-subtitle">Dominar a vizinhança</p>
                    </div>
                    <div class="plan-price">
                        <span class="currency">R$</span>
                        <span class="amount">487,90</span>
                        <span class="period">/mês</span>
                    </div>
                    <ul class="plan-features">
                        <li><i class="fas fa-check"></i> Tudo do Profissional +</li>
                        <li><i class="fas fa-check"></i> Clube de assinatura com descontos exclusivos</li>
                        <li><i class="fas fa-check"></i> Programa de fidelização por pontos</li>
                        <li><i class="fas fa-check"></i> CRM automatizado</li>
                        <li><i class="fas fa-check"></i> Automação de mensagens pós-vendas</li>
                        <li><i class="fas fa-check"></i> Integrações com sistemas de gestão e entrega</li>
                        <li><i class="fas fa-check"></i> Domínio próprio gratuito</li>
                        <li><i class="fas fa-check"></i> Usuários Ilimitados</li>
                        <li><i class="fas fa-check"></i> Suporte prioritário via chat</li>
                    </ul>
                    <div class="plan-cta">
                        <a href="https://wa.me/5562994512211?text=Quero%20o%20plano%20Expert%20da%20Onbeef" target="_blank" class="btn-primary">
                            <i class="fab fa-whatsapp"></i> Quero esse plano
                        </a>
                    </div>
                </div>

                <!-- MASTER -->
                <div class="plan-card fade-in">
                    <div class="plan-header">
                        <h3>Master</h3>
                        <p class="plan-subtitle">Dominar o mercado</p>
                    </div>
                    <div class="plan-price">
                        <span class="currency">R$</span>
                        <span class="amount">2.049,90</span>
                        <span class="period">/mês</span>
                    </div>
                    <ul class="plan-features">
                        <li><i class="fas fa-check"></i> Gestor de performance dedicado à sua loja</li>
                        <li><i class="fas fa-check"></i> Plano de crescimento personalizado com metas e ajustes mensais</li>
                        <li><i class="fas fa-check"></i> Ações de crescimento com baixo ou custo zero</li>
                        <li><i class="fas fa-check"></i> Relatórios semanais de desempenho</li>
                        <li><i class="fas fa-check"></i> Reuniões mensais de planejamento</li>
                        <li><i class="fas fa-check"></i> Grupo exclusivo com sua equipe no WhatsApp</li>
                    </ul>
                    <div class="plan-signature">By Gabriel Gilberti</div>
                    <div class="plan-cta">
                        <a href="https://wa.me/5562994512211?text=Quero%20o%20plano%20Master%20da%20Onbeef" target="_blank" class="btn-secondary">
                            <i class="fab fa-whatsapp"></i> Quero esse plano
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ -->
    <section class="faq" id="faq">
        <div class="container">
            <div class="section-title fade-in">
                <h2>Perguntas <span>frequentes</span></h2>
            </div>
            <div class="faq-list">
                <div class="faq-item fade-in">
                    <div class="faq-question" onclick="toggleFaq(this)">
                        <h3>Preciso ter conhecimento técnico para usar a Onbeef?</h3>
                        <i class="fas fa-plus"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Não! A plataforma foi feita para ser simples e intuitiva. Oferecemos suporte completo e vídeos de ativação para você começar sem dificuldade.</p>
                    </div>
                </div>
                <div class="faq-item fade-in">
                    <div class="faq-question" onclick="toggleFaq(this)">
                        <h3>Em quanto tempo minha loja fica pronta?</h3>
                        <i class="fas fa-plus"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Sua loja pode estar no ar em poucas horas! Basta cadastrar seus produtos, configurar pagamento e pronto — já pode receber pedidos.</p>
                    </div>
                </div>
                <div class="faq-item fade-in">
                    <div class="faq-question" onclick="toggleFaq(this)">
                        <h3>Posso trocar de plano depois?</h3>
                        <i class="fas fa-plus"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Sim! Você pode fazer upgrade a qualquer momento conforme seu açougue cresce. Basta entrar em contato com nosso suporte.</p>
                    </div>
                </div>
                <div class="faq-item fade-in">
                    <div class="faq-question" onclick="toggleFaq(this)">
                        <h3>A Onbeef funciona para qualquer tamanho de açougue?</h3>
                        <i class="fas fa-plus"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Sim! Desde pequenos açougues de bairro até grandes redes. Temos planos que se adaptam a cada realidade do seu negócio.</p>
                    </div>
                </div>
                <div class="faq-item fade-in">
                    <div class="faq-question" onclick="toggleFaq(this)">
                        <h3>Como funciona o pagamento online dos clientes?</h3>
                        <i class="fas fa-plus"></i>
                    </div>
                    <div class="faq-answer">
                        <p>A plataforma integra com meios de pagamento seguros — Pix, cartão de crédito ou débito diretamente na hora do pedido.</p>
                    </div>
                </div>
                <div class="faq-item fade-in">
                    <div class="faq-question" onclick="toggleFaq(this)">
                        <h3>Tem contrato de fidelidade?</h3>
                        <i class="fas fa-plus"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Entre em contato pelo WhatsApp para conhecer todas as condições. Estamos prontos para tirar suas dúvidas!</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA FINAL -->
    <section class="cta-final">
        <div class="container fade-in">
            <h2>Pronto para <span>transformar</span> seu açougue?</h2>
            <p>Junte-se a centenas de açougues que já estão vendendo mais com a Onbeef.</p>
            <a href="https://wa.me/5562994512211?text=Quero%20conhecer%20a%20Onbeef" target="_blank" class="btn-primary">
                <i class="fab fa-whatsapp"></i> Quero conhecer a Onbeef
            </a>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
        <div class="container">
            <a href="#" class="footer-logo">
                <img src="https://i.ibb.co/YBC98Rns/Logo-Onbeef-1.png" alt="Onbeef">
            </a>
            <div class="footer-social">
                <a href="https://www.instagram.com/onbeef_app/" target="_blank"><i class="fab fa-instagram"></i></a>
                <a href="https://wa.me/5562994512211?text=Quero%20conhecer%20a%20Onbeef" target="_blank"><i class="fab fa-whatsapp"></i></a>
            </div>
            <p class="footer-copy">&copy; 2026 Onbeef. Todos os direitos reservados.</p>
        </div>
    </footer>

    <!-- WHATSAPP FLOAT -->
    <a href="https://wa.me/5562994512211?text=Quero%20conhecer%20a%20Onbeef" target="_blank" class="whatsapp-float">
        <i class="fab fa-whatsapp"></i>
    </a>

    <script>
        // Navbar scroll
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            navbar.classList.toggle('scrolled', window.scrollY > 50);
        });

        // Mobile menu
        const navToggle = document.getElementById('navToggle');
        const navLinks = document.getElementById('navLinks');
        const navOverlay = document.getElementById('navOverlay');

        function closeMenu() {
            navToggle.classList.remove('active');
            navLinks.classList.remove('active');
            navOverlay.classList.remove('active');
            document.body.style.overflow = '';
        }

        function openMenu() {
            navToggle.classList.add('active');
            navLinks.classList.add('active');
            navOverlay.classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        navToggle.addEventListener('click', () => {
            navLinks.classList.contains('active') ? closeMenu() : openMenu();
        });

        navOverlay.addEventListener('click', closeMenu);
        navLinks.querySelectorAll('a').forEach(link => link.addEventListener('click', closeMenu));

        // FAQ
        function toggleFaq(el) {
            const item = el.parentElement;
            const isActive = item.classList.contains('active');
            document.querySelectorAll('.faq-item').forEach(f => f.classList.remove('active'));
            if (!isActive) item.classList.add('active');
        }

        // Scroll animations
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) entry.target.classList.add('visible');
            });
        }, { threshold: 0.1, rootMargin: '0px 0px -30px 0px' });

        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
    </script>

</body>
</html>
