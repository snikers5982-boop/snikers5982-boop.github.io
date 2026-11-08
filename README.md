<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Музей Лицея №84 — lycey84muzey</title>
<meta name="description" content="Виртуальный музей Лицея №84: экспонаты">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  :root {
    --primary: #1e3a5f;
    --accent: #c9a227;
    --light: #f5f2ec;
    --dark: #1a1a1a;
    --text: #333;
  }
  body {
    font-family: 'Georgia', 'Times New Roman', serif;
    color: var(--text);
    line-height: 1.6;
    background: var(--light);
  }
  h1, h2, h3 { font-family: 'Georgia', serif; color: var(--primary); }
  a { color: var(--primary); text-decoration: none; transition: 0.3s; }
  a:hover { color: var(--accent); }

  /* HEADER */
  header {
    position: fixed; top: 0; left: 0; right: 0;
    background: rgba(245, 242, 236, 0.95);
    backdrop-filter: blur(10px);
    box-shadow: 0 2px 20px rgba(0,0,0,0.08);
    z-index: 1000;
    padding: 15px 0;
  }
  .nav-container {
    max-width: 1200px; margin: 0 auto;
    padding: 0 20px;
    display: flex; justify-content: space-between; align-items: center;
  }
  .logo {
    display: flex; align-items: center; gap: 12px;
    font-size: 22px; font-weight: bold; color: var(--primary);
  }
  .logo-icon {
    width: 45px; height: 45px;
    background: linear-gradient(135deg, var(--primary), var(--accent));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    color: white; font-size: 20px;
  }
  nav ul { display: flex; list-style: none; gap: 30px; }
  nav a {
    font-family: Arial, sans-serif;
    font-size: 15px; font-weight: 500;
    position: relative;
  }
  nav a::after {
    content: ''; position: absolute;
    bottom: -5px; left: 0; width: 0; height: 2px;
    background: var(--accent); transition: 0.3s;
  }
  nav a:hover::after { width: 100%; }

  /* HERO */
  .hero {
    height: 100vh; min-height: 600px;
    background: linear-gradient(135deg, rgba(30,58,95,0.85), rgba(201,162,39,0.4)),
                url('https://avatars.mds.yandex.net/i?id=5035234ec718eacacf2ce86cd423fa7e_l-8497218-images-thumbs&n=13') center/cover;
    display: flex; align-items: center; justify-content: center;
    text-align: center; color: white;
    padding: 0 20px;
  }
  .hero-content { max-width: 800px; animation: fadeUp 1.2s ease; }
  .hero h1 {
    font-size: clamp(36px, 6vw, 68px);
    color: white; margin-bottom: 20px;
    text-shadow: 2px 2px 20px rgba(0,0,0,0.4);
    letter-spacing: 2px;
  }
  .hero p {
    font-size: clamp(16px, 2vw, 22px);
    margin-bottom: 35px; opacity: 0.95;
    font-family: Arial, sans-serif;
  }
  .btn {
    display: inline-block;
    padding: 15px 40px;
    background: var(--accent);
    color: var(--dark);
    font-family: Arial, sans-serif;
    font-weight: bold;
    letter-spacing: 1px;
    text-transform: uppercase;
    font-size: 14px;
    border-radius: 3px;
    transition: 0.3s;
    border: 2px solid var(--accent);
  }
  .btn:hover {
    background: transparent; color: white;
    transform: translateY(-3px);
    box-shadow: 0 10px 25px rgba(201,162,39,0.4);
  }
  .btn-outline {
    background: transparent; color: white;
    margin-left: 15px;
  }
  .btn-outline:hover { background: var(--accent); color: var(--dark); }

  /* SECTIONS */
  section { padding: 100px 20px; }
  .container { max-width: 1200px; margin: 0 auto; }
  .section-title {
    text-align: center;
    font-size: clamp(28px, 4vw, 42px);
    margin-bottom: 15px;
    position: relative;
    padding-bottom: 20px;
  }
  .section-title::after {
    content: ''; position: absolute;
    bottom: 0; left: 50%; transform: translateX(-50%);
    width: 80px; height: 3px;
    background: var(--accent);
  }
  .section-subtitle {
    text-align: center;
    color: #666;
    font-family: Arial, sans-serif;
    margin-bottom: 60px;
    max-width: 700px;
    margin-left: auto;
    margin-right: auto;
  }

  /* ABOUT */
  .about { background: white; }
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: center;
  }
  .about-image {
    aspect-ratio: 4/3;
    background: url('https://images.unsplash.com/photo-1518998053901-5348d3961a04?w=800') center/cover;
    border-radius: 8px;
    box-shadow: 20px 20px 0 var(--accent);
    transition: 0.4s;
  }
  .about-image:hover { transform: translate(-5px, -5px); }
  .about-text h3 { font-size: 28px; margin-bottom: 20px; }
  .about-text p { margin-bottom: 15px; font-family: Arial, sans-serif; }
  .stats {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 20px; margin-top: 40px;
  }
  .stat {
    text-align: center;
    padding: 20px;
    background: var(--light);
    border-radius: 8px;
  }
  .stat-num {
    font-size: 36px; font-weight: bold;
    color: var(--accent);
    font-family: Georgia, serif;
  }
  .stat-label {
    font-size: 13px; color: #666;
    font-family: Arial, sans-serif;
  }

  /* EXHIBITS */
  .exhibits { background: var(--light); }
  .exhibit-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
  }
  .card {
    background: white;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 5px 20px rgba(0,0,0,0.08);
    transition: 0.4s;
    cursor: pointer;
  }
  .card:hover {
    transform: translateY(-10px);
    box-shadow: 0 20px 40px rgba(0,0,0,0.15);
  }
  .card-img {
    height: 220px;
    background-size: cover;
    background-position: center;
    transition: 0.5s;
  }
  .card:hover .card-img { transform: scale(1.05); }
  .card-img-wrapper { overflow: hidden; }
  .card-body { padding: 25px; }
  .card-body h3 { font-size: 20px; margin-bottom: 10px; }
  .card-body p { font-size: 14px; color: #666; font-family: Arial, sans-serif; }
  .card-tag {
    display: inline-block;
    padding: 4px 12px;
    background: var(--accent);
    color: var(--dark);
    font-size: 11px;
    font-family: Arial, sans-serif;
    text-transform: uppercase;
    letter-spacing: 1px;
    border-radius: 3px;
    margin-bottom: 12px;
    font-weight: bold;
  }

  /* EVENTS */
  .events { background: var(--primary); color: white; }
  .events .section-title, .events h3 { color: white; }
  .events .section-subtitle { color: rgba(255,255,255,0.8); }
  .event-list {
    display: flex; flex-direction: column; gap: 20px;
    max-width: 900px; margin: 0 auto;
  }
  .event {
    display: flex; gap: 25px; align-items: center;
    padding: 25px;
    background: rgba(255,255,255,0.08);
    border-left: 4px solid var(--accent);
    border-radius: 4px;
    transition: 0.3s;
  }
  .event:hover {
    background: rgba(255,255,255,0.15);
    transform: translateX(10px);
  }
  .event-date {
    min-width: 80px;
    text-align: center;
    padding: 15px;
    background: var(--accent);
    color: var(--dark);
    border-radius: 4px;
    font-family: Arial, sans-serif;
  }
  .event-date .day { font-size: 28px; font-weight: bold; }
  .event-date .month { font-size: 12px; text-transform: uppercase; letter-spacing: 1px; }
  .event-info h3 { font-size: 20px; margin-bottom: 5px; }
  .event-info p { color: rgba(255,255,255,0.7); font-size: 14px; font-family: Arial, sans-serif; }

  /* CONTACT */
  .contact { background: white; }
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
  }
  .contact-info h3 { font-size: 24px; margin-bottom: 25px; }
  .contact-item {
    display: flex; gap: 15px; align-items: flex-start;
    margin-bottom: 25px;
    font-family: Arial, sans-serif;
  }
  .contact-icon {
    width: 45px; height: 45px; min-width: 45px;
    background: var(--light);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 20px;
    color: var(--accent);
  }
  .contact-item strong { display: block; color: var(--primary); margin-bottom: 3px; }
  .contact-form input, .contact-form textarea {
    width: 100%; padding: 15px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-family: Arial, sans-serif;
    font-size: 14px;
    background: var(--light);
    transition: 0.3s;
  }
  .contact-form input:focus, .contact-form textarea:focus {
    outline: none;
    border-color: var(--accent);
    background: white;
  }
  .contact-form textarea { resize: vertical; min-height: 120px; }
  .contact-form button {
    background: var(--primary);
    color: white;
    border: none;
    padding: 15px 40px;
    font-family: Arial, sans-serif;
    font-weight: bold;
    text-transform: uppercase;
    letter-spacing: 1px;
    border-radius: 4px;
    cursor: pointer;
    transition: 0.3s;
    font-size: 14px;
  }
  .contact-form button:hover {
    background: var(--accent);
    color: var(--dark);
    transform: translateY(-2px);
  }

  /* FOOTER */
  footer {
    background: var(--dark);
    color: rgba(255,255,255,0.7);
    padding: 40px 20px;
    text-align: center;
    font-family: Arial, sans-serif;
    font-size: 14px;
  }
  footer .domain {
    color: var(--accent);
    font-weight: bold;
    letter-spacing: 2px;
    margin-top: 10px;
    display: inline-block;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .reveal {
    opacity: 0;
    transform: translateY(40px);
    transition: 0.8s ease;
  }
  .reveal.active {
    opacity: 1;
    transform: translateY(0);
  }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    nav ul { display: none; }
    .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 40px; }
    .about-image { box-shadow: 10px 10px 0 var(--accent); }
    section { padding: 70px 20px; }
  }
  @media (max-width: 600px) {
    .stats { grid-template-columns: 1fr; }
    .event { flex-direction: column; text-align: center; }
    .btn-outline { margin-left: 0; margin-top: 10px; display: block; width: fit-content; margin-inline: auto; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="nav-container">
    <div class="logo">
      <div class="logo-icon">🏛</div>
      <div>Музей Лицея №84</div>
    </div>
    <nav>
      <ul>
        <li><a href="#about">О музее</a></li>
        <li><a href="#exhibits">Экспонаты</a></li>
        <li><a href="#events">События</a></li>
        <li><a href="#contact">Контакты</a></li>
      </ul>
    </nav>
  </div>
</header>

<!-- HERO -->
<section class="hero">
  <div class="hero-content">
    <h1>Музей Лицея №84</h1>
    <p>Хранитель истории, традиций и достижений нашего учебного заведения</p>
    <a href="#about" class="btn">Узнать больше</a>
    <a href="#exhibits" class="btn btn-outline">Экспонаты</a>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="about">
  <div class="container">
    <h2 class="section-title reveal">О нашем музее</h2>
    <p class="section-subtitle reveal">Мы бережно храним память о прошлом и вдохновляем будущие поколения</p>
    <div class="about-grid">
      <div class="about-image reveal"></div>
      <div class="about-text reveal">
        <h3>История и наследие</h3>
        <p>Музей Лицея №84 был основан благодаря усилиям педагогов, учеников и выпускников, желающих сохранить богатую историю нашего учебного заведения.</p>
        <p>В экспозиции представлены архивные документы, фотографии разных лет, награды, личные вещи выдающихся выпускников и учителей, а также предметы, связанные с ключевыми событиями в жизни лицея.</p>
        <p>Музей — это живое пространство, где проходят экскурсии, встречи с выпускниками, тематические выставки и исследовательские проекты школьников.</p>
        <div class="stats">
          <div class="stat">
            <div class="stat-num">500+</div>
            <div class="stat-label">Экспонатов</div>
          </div>
          <div class="stat">
            <div class="stat-num">40</div>
            <div class="stat-label">Лет истории</div>
          </div>
          <div class="stat">
            <div class="stat-num">1000+</div>
            <div class="stat-label">Посетителей</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EXHIBITS -->
<section class="exhibits" id="exhibits">
  <div class="container">
    <h2 class="section-title reveal">Экспозиции</h2>
    <p class="section-subtitle reveal">Познакомьтесь с ключевыми разделами нашего музея</p>
    <div class="exhibit-grid">
      <div class="card reveal">
        <div class="card-img-wrapper">
          <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1568667256549-094345857637?w=600')"></div>
        </div>
        <div class="card-body">
          <span class="card-tag">История</span>
          <h3>Страницы прошлого</h3>
          <p>Архивные документы, фотографии и реликвии, рассказывающие об истории лицея с момента основания.</p>
        </div>
      </div>
      <div class="card reveal">
        <div class="card-img-wrapper">
          <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1544717305-2782549b5136?w=600')"></div>
        </div>
        <div class="card-body">
          <span class="card-tag">Достижения</span>
          <h3>Наши звёзды</h3>
          <p>Награды, кубки и грамоты учеников и педагогов — гордость лицея на разных уровнях.</p>
        </div>
      </div>
      <div class="card reveal">
        <div class="card-img-wrapper">
          <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1503676260728-1c00da094a0b?w=600')"></div>
        </div>
        <div class="card-body">
          <span class="card-tag">Творчество</span>
          <h3>Ученические работы</h3>
          <p>Рисунки, поделки, проекты и исследования, созданные руками наших талантливых учеников.</p>
        </div>
      </div>
      <div class="card reveal">
        <div class="card-img-wrapper">
          <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?w=600')"></div>
        </div>
        <div class="card-body">
          <span class="card-tag">Память</span>
          <h3>Ветераны и выпускники</h3>
          <p>Личные вещи, письма и воспоминания выпускников, внёсших значительный вклад в историю.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- EVENTS -->
<section class="events" id="events">
  <div class="container">
    <h2 class="section-title reveal">Ближайшие события</h2>
    <p class="section-subtitle reveal">Экскурсии, встречи и выставки, которые ждут вас</p>
    <div class="event-list">
      <div class="event reveal">
        <div class="event-date">
          <div class="day">15</div>
          <div class="month">Май</div>
        </div>
        <div class="event-info">
          <h3>День открытых дверей музея</h3>
          <p>Приглашаем всех желающих познакомиться с обновлённой экспозицией</p>
        </div>
      </div>
      <div class="event reveal">
        <div class="event-date">
          <div class="day">22</div>
          <div class="month">Май</div>
        </div>
        <div class="event-info">
          <h3>Встреча с выпускниками</h3>
          <p>Тёплый вечер воспоминаний и общения поколений лицеистов</p>
        </div>
      </div>
      <div class="event reveal">
        <div class="event-date">
          <div class="day">01</div>
          <div class="month">Июнь</div>
        </div>
        <div class="event-info">
          <h3>Выставка «Таланты лицея»</h3>
          <p>Работы учеников в области искусства, науки и техники</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="container">
    <h2 class="section-title reveal">Свяжитесь с нами</h2>
    <p class="section-subtitle reveal">Запишитесь на экскурсию или задайте вопрос</p>
    <div class="contact-grid">
      <div class="contact-info reveal">
        <h3>Контакты музея</h3>
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div>
            <strong>Адрес</strong>
            г. Лицей, ул. Школьная, д. 84
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📞</div>
          <div>
            <strong>Телефон</strong>
            +7 (000) 000-00-00
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">✉️</div>
          <div>
            <strong>Email</strong>
            info@lycey84muzey.ru
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🕐</div>
          <div>
            <strong>Часы работы</strong>
            Пн–Пт: 9:00–17:00
          </div>
        </div>
      </div>
      <form class="contact-form reveal" onsubmit="event.preventDefault(); alert('Спасибо! Ваше сообщение отправлено.'); this.reset();">
        <input type="text" placeholder="Ваше имя" required>
        <input type="email" placeholder="Email" required>
        <input type="text" placeholder="Тема">
        <textarea placeholder="Ваше сообщение" required></textarea>
        <button type="submit">Отправить</button>
      </form>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div>© 2025 Музей Лицея №84. Все права защищены.</div>
  <div class="domain">lycey84muzey.ru</div>
</footer>

<script>
  // Reveal-анимация при скролле
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('active'), i * 100);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Плавный скролл
  document.querySelectorAll('a[href^="#"]').forEach(link => {
    link.addEventListener('click', e => {
      const target = document.querySelector(link.getAttribute('href'));
      if (target) {
        e.preventDefault();
        window.scrollTo({ top: target.offsetTop - 80, behavior: 'smooth' });
      }
    });
  });
</script>
</body>
</html>
