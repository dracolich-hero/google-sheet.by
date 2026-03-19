<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Excel-таблицы и автоматизация учета для малого бизнеса</title>
  <meta
    name="description"
    content="Создание Excel-таблиц, учет заказов, расходов и прибыли, автоматизация отчетов для малого бизнеса."
  />
  <style>
    :root{
      --bg: #f5f9ff;
      --card: #ffffff;
      --text: #12233d;
      --muted: #5d718b;
      --line: #dce8f8;
      --primary: #1f6feb;
      --primary-dark: #1557b5;
      --accent: #eaf3ff;
      --success: #16a34a;
      --shadow: 0 12px 30px rgba(31, 111, 235, 0.08);
      --radius: 18px;
      --radius-sm: 12px;
      --maxw: 1160px;
    }

    *{
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html{
      scroll-behavior: smooth;
    }

    body{
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at top right, rgba(31,111,235,0.06), transparent 28%),
        radial-gradient(circle at left bottom, rgba(31,111,235,0.05), transparent 22%),
        var(--bg);
      line-height: 1.55;
    }

    a{
      color: inherit;
      text-decoration: none;
    }

    img{
      max-width: 100%;
      display: block;
    }

    .container{
      width: 100%;
      max-width: var(--maxw);
      margin: 0 auto;
      padding: 0 20px;
    }

    .section{
      padding: 72px 0;
    }

    .section-title{
      font-size: clamp(28px, 4vw, 42px);
      line-height: 1.15;
      margin-bottom: 14px;
      letter-spacing: -0.02em;
    }

    .section-subtitle{
      color: var(--muted);
      max-width: 720px;
      margin-bottom: 34px;
      font-size: 16px;
    }

    .badge{
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 14px;
      border-radius: 999px;
      background: var(--accent);
      color: var(--primary-dark);
      font-size: 14px;
      font-weight: 600;
      margin-bottom: 18px;
      border: 1px solid #d8e8ff;
    }

    .btn{
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 14px 22px;
      border-radius: 12px;
      border: none;
      cursor: pointer;
      font-weight: 700;
      font-size: 15px;
      transition: transform 0.15s ease, background 0.15s ease, box-shadow 0.15s ease;
    }

    .btn:hover{
      transform: translateY(-1px);
    }

    .btn-primary{
      background: var(--primary);
      color: #fff;
      box-shadow: 0 10px 22px rgba(31, 111, 235, 0.18);
    }

    .btn-primary:hover{
      background: var(--primary-dark);
    }

    .btn-secondary{
      background: #fff;
      color: var(--primary-dark);
      border: 1px solid #dbe8fb;
    }

    .btn-full{
      width: 100%;
    }

    .card{
      background: var(--card);
      border: 1px solid rgba(220, 232, 248, 0.9);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
    }

    /* Header */
    .header{
      position: sticky;
      top: 0;
      z-index: 50;
      backdrop-filter: blur(12px);
      background: rgba(245, 249, 255, 0.88);
      border-bottom: 1px solid rgba(220, 232, 248, 0.9);
    }

    .header-inner{
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      min-height: 72px;
    }

    .logo{
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 800;
      font-size: 16px;
      color: var(--text);
    }

    .logo-mark{
      width: 36px;
      height: 36px;
      border-radius: 12px;
      background: linear-gradient(135deg, var(--primary), #5ca0ff);
      display: grid;
      place-items: center;
      color: #fff;
      font-size: 18px;
      font-weight: 800;
    }

    .nav{
      display: flex;
      gap: 18px;
      align-items: center;
      flex-wrap: wrap;
    }

    .nav a{
      color: var(--muted);
      font-size: 14px;
      font-weight: 600;
    }

    .nav a:hover{
      color: var(--primary-dark);
    }

    /* Hero */
    .hero{
      padding: 42px 0 32px;
    }

    .hero-grid{
      display: grid;
      grid-template-columns: 1.15fr 0.85fr;
      gap: 26px;
      align-items: stretch;
    }

    .hero-left{
      padding: 34px;
    }

    .hero h1{
      font-size: clamp(34px, 5vw, 58px);
      line-height: 1.05;
      letter-spacing: -0.03em;
      margin-bottom: 16px;
    }

    .hero p{
      color: var(--muted);
      font-size: 18px;
      max-width: 650px;
      margin-bottom: 24px;
    }

    .hero-actions{
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      margin-bottom: 24px;
    }

    .hero-stats{
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 12px;
    }

    .stat{
      background: #fff;
      border: 1px solid var(--line);
      border-radius: 14px;
      padding: 16px;
    }

    .stat strong{
      display: block;
      font-size: 20px;
      margin-bottom: 4px;
    }

    .stat span{
      color: var(--muted);
      font-size: 13px;
    }

    .hero-right{
      padding: 24px;
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .mockup{
      border-radius: 18px;
      overflow: hidden;
      border: 1px solid var(--line);
      background: #fff;
    }

    .mockup-top{
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 12px 14px;
      border-bottom: 1px solid var(--line);
      background: #f8fbff;
    }

    .dot{
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background: #c7d9f7;
    }

    .sheet{
      padding: 16px;
      display: grid;
      gap: 10px;
    }

    .sheet-row{
      display: grid;
      grid-template-columns: 1.2fr 0.8fr 0.8fr 0.8fr;
      gap: 8px;
    }

    .cell{
      height: 38px;
      border-radius: 10px;
      background: #f5f9ff;
      border: 1px solid #e1ecfb;
    }

    .cell.primary{
      background: #eaf3ff;
      border-color: #cfe2ff;
    }

    .info-box{
      padding: 18px;
      border-radius: 16px;
      background: linear-gradient(180deg, #ffffff, #f8fbff);
      border: 1px solid var(--line);
    }

    .info-box h3{
      font-size: 18px;
      margin-bottom: 8px;
    }

    .info-box p{
      color: var(--muted);
      font-size: 14px;
    }

    /* Services */
    .grid-3{
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .service-card{
      padding: 24px;
      position: relative;
      overflow: hidden;
    }

    .service-card.featured{
      border: 1px solid #bfd8ff;
      box-shadow: 0 18px 36px rgba(31, 111, 235, 0.12);
    }

    .service-tag{
      display: inline-block;
      padding: 6px 10px;
      border-radius: 999px;
      background: #eef5ff;
      color: var(--primary-dark);
      font-size: 12px;
      font-weight: 700;
      margin-bottom: 14px;
    }

    .service-title{
      font-size: 24px;
      margin-bottom: 8px;
    }

    .price{
      font-size: 34px;
      font-weight: 800;
      margin-bottom: 12px;
      color: var(--primary-dark);
    }

    .service-desc{
      color: var(--muted);
      margin-bottom: 18px;
      min-height: 48px;
    }

    .service-list{
      list-style: none;
      display: grid;
      gap: 10px;
      margin-bottom: 22px;
    }

    .service-list li{
      display: flex;
      gap: 10px;
      align-items: flex-start;
      color: var(--text);
      font-size: 15px;
    }

    .check{
      width: 20px;
      height: 20px;
      min-width: 20px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      background: #eaf7ef;
      color: var(--success);
      font-size: 12px;
      font-weight: 800;
      margin-top: 2px;
    }

    /* Examples */
    .examples-grid{
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .example-card{
      padding: 18px;
    }

    .example-visual{
      border-radius: 14px;
      border: 1px solid var(--line);
      background: linear-gradient(180deg, #ffffff, #f7fbff);
      padding: 14px;
      margin-bottom: 16px;
    }

    .mini-head{
      height: 16px;
      width: 45%;
      border-radius: 999px;
      background: #d7e8ff;
      margin-bottom: 12px;
    }

    .mini-grid{
      display: grid;
      gap: 8px;
    }

    .mini-row{
      display: grid;
      grid-template-columns: 1.3fr 0.9fr 0.9fr;
      gap: 6px;
    }

    .mini-cell{
      height: 24px;
      border-radius: 8px;
      background: #eef5ff;
      border: 1px solid #deebff;
    }

    .example-card h3{
      font-size: 18px;
      margin-bottom: 8px;
    }

    .example-card p{
      color: var(--muted);
      font-size: 14px;
    }

    /* Benefits */
    .benefits-wrap{
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 18px;
    }

    .benefits-list{
      padding: 24px;
      display: grid;
      gap: 14px;
    }

    .benefit-item{
      display: flex;
      gap: 14px;
      align-items: flex-start;
      padding: 14px;
      border-radius: 14px;
      background: #f8fbff;
      border: 1px solid #e4eefc;
    }

    .benefit-icon{
      width: 42px;
      height: 42px;
      border-radius: 12px;
      display: grid;
      place-items: center;
      background: #eaf3ff;
      color: var(--primary-dark);
      font-size: 20px;
      flex-shrink: 0;
    }

    .benefit-item h4{
      font-size: 16px;
      margin-bottom: 4px;
    }

    .benefit-item p{
      color: var(--muted);
      font-size: 14px;
    }

    .benefits-side{
      padding: 24px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 18px;
    }

    .roi-box{
      padding: 20px;
      border-radius: 16px;
      background: linear-gradient(180deg, #f7fbff, #ffffff);
      border: 1px solid var(--line);
    }

    .roi-box h3{
      font-size: 18px;
      margin-bottom: 8px;
    }

    .roi-box p{
      color: var(--muted);
      font-size: 14px;
      margin-bottom: 12px;
    }

    .roi-grid{
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
    }

    .roi-item{
      padding: 14px;
      border-radius: 12px;
      background: #fff;
      border: 1px solid var(--line);
    }

    .roi-item strong{
      display: block;
      font-size: 18px;
      margin-bottom: 4px;
    }

    .roi-item span{
      font-size: 13px;
      color: var(--muted);
    }

    /* Form */
    .lead-grid{
      display: grid;
      grid-template-columns: 1fr 0.9fr;
      gap: 18px;
    }

    .lead-left{
      padding: 28px;
    }

    .lead-left h3{
      font-size: 28px;
      margin-bottom: 12px;
    }

    .lead-left p{
      color: var(--muted);
      margin-bottom: 20px;
    }

    .lead-points{
      display: grid;
      gap: 12px;
    }

    .lead-point{
      display: flex;
      gap: 12px;
      align-items: flex-start;
      padding: 14px;
      border-radius: 14px;
      background: #f8fbff;
      border: 1px solid #e5effd;
    }

    .lead-form{
      padding: 24px;
    }

    .form-title{
      font-size: 22px;
      margin-bottom: 8px;
    }

    .form-subtitle{
      color: var(--muted);
      font-size: 14px;
      margin-bottom: 18px;
    }

    .form-group{
      margin-bottom: 14px;
    }

    label{
      display: block;
      font-size: 14px;
      font-weight: 600;
      margin-bottom: 8px;
      color: var(--text);
    }

    input, textarea, select{
      width: 100%;
      border: 1px solid #dbe8fb;
      background: #fff;
      border-radius: 12px;
      padding: 14px 14px;
      font-size: 15px;
      color: var(--text);
      outline: none;
      transition: border-color 0.15s ease, box-shadow 0.15s ease;
    }

    input:focus, textarea:focus, select:focus{
      border-color: #9cc3ff;
      box-shadow: 0 0 0 4px rgba(31, 111, 235, 0.08);
    }

    textarea{
      min-height: 120px;
      resize: vertical;
    }

    .form-note{
      margin-top: 12px;
      font-size: 13px;
      color: var(--muted);
    }

    .success-message{
      display: none;
      margin-top: 14px;
      padding: 12px 14px;
      border-radius: 12px;
      background: #eefcf3;
      color: #166534;
      border: 1px solid #c8f0d4;
      font-size: 14px;
      font-weight: 600;
    }

    /* Contacts */
    .contacts-grid{
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .contact-card{
      padding: 22px;
    }

    .contact-card h3{
      font-size: 18px;
      margin-bottom: 8px;
    }

    .contact-card p{
      color: var(--muted);
      font-size: 14px;
      margin-bottom: 14px;
    }

    .contact-link{
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-weight: 700;
      color: var(--primary-dark);
    }

    /* Footer */
    .footer{
      padding: 28px 0 42px;
      color: var(--muted);
      font-size: 14px;
    }

    .footer-inner{
      display: flex;
      justify-content: space-between;
      gap: 12px;
      flex-wrap: wrap;
      padding-top: 18px;
      border-top: 1px solid var(--line);
    }

    /* Mobile */
    @media (max-width: 980px){
      .hero-grid,
      .benefits-wrap,
      .lead-grid{
        grid-template-columns: 1fr;
      }

      .grid-3,
      .examples-grid,
      .contacts-grid{
        grid-template-columns: 1fr;
      }

      .hero-right{
        order: -1;
      }
    }

    @media (max-width: 720px){
      .header-inner{
        min-height: auto;
        padding: 14px 0;
        flex-direction: column;
        align-items: flex-start;
      }

      .nav{
        gap: 12px;
      }

      .hero{
        padding-top: 24px;
      }

      .hero-left,
      .hero-right,
      .lead-left,
      .lead-form,
      .service-card,
      .example-card,
      .benefits-list,
      .benefits-side,
      .contact-card{
        padding: 20px;
      }

      .hero-stats{
        grid-template-columns: 1fr;
      }

      .hero-actions{
        flex-direction: column;
      }

      .hero-actions .btn{
        width: 100%;
      }

      .section{
        padding: 56px 0;
      }

      .section-subtitle{
        margin-bottom: 24px;
      }
    }
  </style>
</head>
<body>

  <!-- HEADER -->
  <header class="header">
    <div class="container header-inner">
      <a href="#top" class="logo">
        <span class="logo-mark">XL</span>
        <span>Excel-таблицы для бизнеса</span>
      </a>

      <nav class="nav">
        <a href="#services">Услуги</a>
        <a href="#examples">Примеры</a>
        <a href="#benefits">Преимущества</a>
        <a href="#lead">Заявка</a>
        <a href="#contacts">Контакты</a>
      </nav>
    </div>
  </header>

  <!-- HERO -->
  <main id="top">
    <section class="hero">
      <div class="container hero-grid">
        <div class="hero-left card">
          <div class="badge">⚡ Учет без хаоса и ручной рутины</div>
          <h1>Excel-таблицы и автоматизация учета для малого бизнеса</h1>
          <p>
            Настрою удобные таблицы для учета заказов, расходов, прибыли и отчетов.
            Меньше ручной работы, меньше ошибок, больше контроля над деньгами и процессами.
          </p>

          <div class="hero-actions">
            <a href="#lead" class="btn btn-primary">Оставить заявку</a>
            <a href="#services" class="btn btn-secondary">Смотреть пакеты</a>
          </div>

          <div class="hero-stats">
            <div class="stat">
              <strong>1–3 дня</strong>
              <span>на базовую настройку таблицы</span>
            </div>
            <div class="stat">
              <strong>До 80%</strong>
              <span>меньше ручного ввода и ошибок</span>
            </div>
            <div class="stat">
              <strong>1 файл</strong>
              <span>вместо хаоса из разных таблиц</span>
            </div>
          </div>
        </div>

        <div class="hero-right card">
          <div class="mockup">
            <div class="mockup-top">
              <span class="dot"></span>
              <span class="dot"></span>
              <span class="dot"></span>
            </div>
            <div class="sheet">
              <div class="sheet-row">
                <div class="cell primary"></div>
                <div class="cell primary"></div>
                <div class="cell primary"></div>
                <div class="cell primary"></div>
              </div>
              <div class="sheet-row">
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
              </div>
              <div class="sheet-row">
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
              </div>
              <div class="sheet-row">
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
              </div>
              <div class="sheet-row">
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
                <div class="cell"></div>
              </div>
            </div>
          </div>

          <div class="info-box">
            <h3>Что можно автоматизировать?</h3>
            <p>
              Учет заказов, расходы, закупки, прибыль, зарплаты, остатки, заявки клиентов,
              отчеты по дням / неделям / месяцам, контроль менеджеров и повторных заказов.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- SERVICES -->
    <section class="section" id="services">
      <div class="container">
        <div class="badge">Пакеты услуг</div>
        <h2 class="section-title">3 готовых решения под ваш бизнес</h2>
        <p class="section-subtitle">
          Подходит для малого бизнеса, услуг, производства, торговли, бригад, мастеров,
          небольших офисов и частных предпринимателей.
        </p>

        <div class="grid-3">
          <div class="service-card card">
            <div class="service-tag">Старт</div>
            <h3 class="service-title">Базовый</h3>
            <div class="price">от 50 BYN</div>
            <p class="service-desc">
              Простая и удобная таблица для ежедневного учета без лишней сложности.
            </p>
            <ul class="service-list">
              <li><span class="check">✓</span><span>1 таблица под ваш процесс</span></li>
              <li><span class="check">✓</span><span>Учет заказов / расходов / доходов</span></li>
              <li><span class="check">✓</span><span>Базовые формулы и итоги</span></li>
              <li><span class="check">✓</span><span>Короткая инструкция по использованию</span></li>
            </ul>
            <a href="#lead" class="btn btn-secondary btn-full">Выбрать пакет</a>
          </div>

          <div class="service-card card featured">
            <div class="service-tag">Популярный</div>
            <h3 class="service-title">Оптимальный</h3>
            <div class="price">от 120 BYN</div>
            <p class="service-desc">
              Полноценная система учета с несколькими листами и автоматическими отчетами.
            </p>
            <ul class="service-list">
              <li><span class="check">✓</span><span>2–5 связанных таблиц</span></li>
              <li><span class="check">✓</span><span>Авторасчеты прибыли и расходов</span></li>
              <li><span class="check">✓</span><span>Отчеты по периодам (день / неделя / месяц)</span></li>
              <li><span class="check">✓</span><span>Настройка под ваш реальный процесс</span></li>
            </ul>
            <a href="#lead" class="btn btn-primary btn-full">Выбрать пакет</a>
          </div>

          <div class="service-card card">
            <div class="service-tag">Под ключ</div>
            <h3 class="service-title">Премиум</h3>
            <div class="price">от 250 BYN</div>
            <p class="service-desc">
              Индивидуальная автоматизация учета с логикой, аналитикой и сопровождением.
            </p>
            <ul class="service-list">
              <li><span class="check">✓</span><span>Сложные формулы и сценарии</span></li>
              <li><span class="check">✓</span><span>Дашборды и управленческие отчеты</span></li>
              <li><span class="check">✓</span><span>Оптимизация текущих файлов</span></li>
              <li><span class="check">✓</span><span>Поддержка и доработки после сдачи</span></li>
            </ul>
            <a href="#lead" class="btn btn-secondary btn-full">Обсудить проект</a>
          </div>
        </div>
      </div>
    </section>

    <!-- EXAMPLES -->
    <section class="section" id="examples">
      <div class="container">
        <div class="badge">Примеры таблиц</div>
        <h2 class="section-title">Какие таблицы я могу сделать</h2>
        <p class="section-subtitle">
          Ниже — популярные варианты, которые чаще всего нужны небольшому бизнесу.
        </p>

        <div class="examples-grid">
          <div class="example-card card">
            <div class="example-visual">
              <div class="mini-head"></div>
              <div class="mini-grid">
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
              </div>
            </div>
            <h3>Учет заказов</h3>
            <p>
              Заявки, статусы, оплаты, ответственные, сроки, повторные клиенты,
              фильтры по менеджерам и периодам.
            </p>
          </div>

          <div class="example-card card">
            <div class="example-visual">
              <div class="mini-head"></div>
              <div class="mini-grid">
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
              </div>
            </div>
            <h3>Финансы и прибыль</h3>
            <p>
              Доходы, расходы, маржа, чистая прибыль, закупки, долги,
              платежный календарь и итоговые отчеты.
            </p>
          </div>

          <div class="example-card card">
            <div class="example-visual">
              <div class="mini-head"></div>
              <div class="mini-grid">
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
                <div class="mini-row">
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                  <div class="mini-cell"></div>
                </div>
              </div>
            </div>
            <h3>Отчеты и аналитика</h3>
            <p>
              MTD / YTD, показатели по сотрудникам, план-факт, загрузка,
              эффективность и сводные таблицы для руководителя.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- BENEFITS -->
    <section class="section" id="benefits">
      <div class="container">
        <div class="badge">Почему это выгодно</div>
        <h2 class="section-title">Бизнесу нужен не “еще один файл”, а понятная система учета</h2>
        <p class="section-subtitle">
          Хорошо настроенная таблица помогает принимать решения быстрее и видеть реальную картину по деньгам и процессам.
        </p>

        <div class="benefits-wrap">
          <div class="benefits-list card">
            <div class="benefit-item">
              <div class="benefit-icon">⏱</div>
              <div>
                <h4>Экономия времени</h4>
                <p>Меньше ручного ввода, копирования и проверки данных каждый день.</p>
              </div>
            </div>

            <div class="benefit-item">
              <div class="benefit-icon">📊</div>
              <div>
                <h4>Понятные цифры</h4>
                <p>Вы сразу видите прибыль, расходы, просадки и ключевые показатели.</p>
              </div>
            </div>

            <div class="benefit-item">
              <div class="benefit-icon">✅</div>
              <div>
                <h4>Меньше ошибок</h4>
                <p>Формулы и логика уменьшают риск потерь из-за человеческого фактора.</p>
              </div>
            </div>

            <div class="benefit-item">
              <div class="benefit-icon">📁</div>
              <div>
                <h4>Все в одном месте</h4>
                <p>Заказы, расходы, отчеты и аналитика собираются в единой системе.</p>
              </div>
            </div>
          </div>

          <div class="benefits-side card">
            <div class="roi-box">
              <h3>Что вы получаете после внедрения</h3>
              <p>
                Вместо хаотичных таблиц — рабочий инструмент, который помогает управлять бизнесом
                и экономить время владельца или менеджера.
              </p>

              <div class="roi-grid">
                <div class="roi-item">
                  <strong>Быстрее</strong>
                  <span>отчеты за минуты, а не вручную</span>
                </div>
                <div class="roi-item">
                  <strong>Прозрачнее</strong>
                  <span>понятно, где теряются деньги</span>
                </div>
                <div class="roi-item">
                  <strong>Проще</strong>
                  <span>сотрудникам легче работать</span>
                </div>
                <div class="roi-item">
                  <strong>Надежнее</strong>
                  <span>меньше ошибок и дублирования</span>
                </div>
              </div>
            </div>

            <div class="info-box">
              <h3>Для кого подходит</h3>
              <p>
                Услуги, производство, бригады, мастерские, небольшие магазины, торговля,
                ремонт, доставка, офисные процессы и любой бизнес, где сейчас “всё в разных Excel-файлах”.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- LEAD FORM -->
    <section class="section" id="lead">
      <div class="container">
        <div class="badge">Оставить заявку</div>
        <h2 class="section-title">Напишите, какая таблица нужна — и я предложу решение</h2>
        <p class="section-subtitle">
          После отправки формы откроется Telegram с готовым текстом сообщения. Вам останется только нажать “Отправить”.
        </p>

        <div class="lead-grid">
          <div class="lead-left card">
            <h3>Как проходит работа</h3>
            <p>
              Все максимально просто: вы описываете задачу, я предлагаю структуру,
              делаю таблицу, тестируем на ваших данных и дорабатываем при необходимости.
            </p>

            <div class="lead-points">
              <div class="lead-point">
                <span class="check">1</span>
                <div>
                  <strong>Коротко описываете задачу</strong>
                  <div style="color: var(--muted); font-size: 14px;">Что хотите учитывать и какие данные уже есть.</div>
                </div>
              </div>

              <div class="lead-point">
                <span class="check">2</span>
                <div>
                  <strong>Получаете предложение и стоимость</strong>
                  <div style="color: var(--muted); font-size: 14px;">Выбираем пакет или делаем индивидуально.</div>
                </div>
              </div>

              <div class="lead-point">
                <span class="check">3</span>
                <div>
                  <strong>Получаете готовую таблицу</strong>
                  <div style="color: var(--muted); font-size: 14px;">С инструкцией, логикой и нужными отчетами.</div>
                </div>
              </div>
            </div>
          </div>

          <div class="lead-form card">
            <h3 class="form-title">Форма заявки</h3>
            <p class="form-subtitle">
              Заполните поля — откроется Telegram с готовым сообщением.
            </p>

            <form id="telegramForm">
              <div class="form-group">
                <label for="name">Ваше имя</label>
                <input type="text" id="name" name="name" placeholder="Например: Алексей" required />
              </div>

              <div class="form-group">
                <label for="contact">Телефон / Telegram / WhatsApp</label>
                <input type="text" id="contact" name="contact" placeholder="@username или +375..." required />
              </div>

              <div class="form-group">
                <label for="package">Интересующий пакет</label>
                <select id="package" name="package">
                  <option value="Базовый">Базовый</option>
                  <option value="Оптимальный" selected>Оптимальный</option>
                  <option value="Премиум">Премиум</option>
                  <option value="Нужна консультация">Нужна консультация</option>
                </select>
              </div>

              <div class="form-group">
                <label for="task">Что нужно автоматизировать</label>
                <textarea
                  id="task"
                  name="task"
                  placeholder="Например: учет заказов, расходы по каждому заказу, прибыль по неделям, отчет за месяц..."
                  required
                ></textarea>
              </div>

              <button type="submit" class="btn btn-primary btn-full">Оставить заявку</button>



              <div class="success-message" id="successMessage">
                Telegram открыт. Если не открылся автоматически — проверьте, установлен ли Telegram, или используйте Telegram Web.
              </div>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- CONTACTS -->
    <section class="section" id="contacts">
      <div class="container">
        <div class="badge">Контакты</div>
        <h2 class="section-title">Связаться удобным способом</h2>
        <p class="section-subtitle">
          Можно написать напрямую в Telegram или оставить заявку через форму выше.
        </p>

        <div class="contacts-grid">
          <div class="contact-card card">
            <h3>Telegram</h3>
            <p>Основной способ связи для быстрых заявок и обсуждения задачи.</p>
            <a class="contact-link" href="https://t.me/google_sheet_user" target="_blank" rel="noopener">
              Открыть Telegram →
            </a>
          </div>

          <div class="contact-card card">
            <h3>Email</h3>
            <p>Подходит для отправки примеров файлов, ТЗ и скриншотов.</p>
            <a class="contact-link" href="mailto:maxvasilko@gmail.com">
              yourmail@example.com →
            </a>
          </div>

          <div class="contact-card card">
            <h3>Срок ответа</h3>
            <p>Обычно отвечаю в течение дня и быстро оцениваю задачу.</p>
            <span class="contact-link">Ответ в течение 1–24 часов</span>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- FOOTER -->
  <footer class="footer">
    <div class="container footer-inner">
      <span>© 2026 Excel-таблицы для бизнеса</span>
      <span>Учет • Автоматизация • Отчеты • Аналитика</span>
    </div>
  </footer>

  <script>
    // ===== ВАЖНО =====
    // 1) Замените YOUR_TELEGRAM_USERNAME на ваш username БЕЗ @
    //    Например: если ссылка https://t.me/max_excel, то сюда ставите "max_excel"
    //
    // 2) Этот вариант БЕСПЛАТНЫЙ и работает без сервера:
    //    форма не отправляет данные "в фоне", а открывает Telegram с готовым текстом.
    //
    // 3) Если хотите полностью автоматическую отправку в Telegram-бота без открытия Telegram,
    //    я могу сделать v4 через Bot API + бесплатный серверless / Google Apps Script.

    const TELEGRAM_USERNAME = "google_sheet_user";

    const form = document.getElementById("telegramForm");
    const successMessage = document.getElementById("successMessage");

    function buildTelegramMessage(data) {
      return [
        "Новая заявка с сайта",
        "",
        "Имя: " + data.name,
        "Контакт: " + data.contact,
        "Пакет: " + data.package,
        "Задача:",
        data.task
      ].join("\n");
    }

    function openTelegram(message) {
      const encoded = encodeURIComponent(message);

      // Telegram Web / app
      const tgUrl = `https://t.me/${TELEGRAM_USERNAME}?text=${encoded}`;

      // Альтернатива через share URL (может работать не везде одинаково):
      // const tgUrl = `https://t.me/share/url?url=&text=${encoded}`;

      window.open(tgUrl, "_blank", "noopener");
    }

    form.addEventListener("submit", function(e) {
      e.preventDefault();

      const name = document.getElementById("name").value.trim();
      const contact = document.getElementById("contact").value.trim();
      const packageValue = document.getElementById("package").value;
      const task = document.getElementById("task").value.trim();

      if (!name || !contact || !task) {
        alert("Пожалуйста, заполните все обязательные поля.");
        return;
      }

      if (TELEGRAM_USERNAME === "google_sheet_user") {
        alert("Сначала замените YOUR_TELEGRAM_USERNAME в коде на ваш Telegram username без @.");
        return;
      }

      const message = buildTelegramMessage({
        name,
        contact,
        package: packageValue,
        task
      });

      openTelegram(message);

      successMessage.style.display = "block";

      // Небольшая пауза, затем можно очистить форму
      setTimeout(() => {
        form.reset();
      }, 300);
    });
  </script>
</body>
</html>
