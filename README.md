# Zhaba.github.io
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Разработчик Telegram-ботов | Портфолио</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        /* Основные стили */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', sans-serif;
        }

        :root {
            --primary: #0a0a0a;
            --secondary: #1a1a1a;
            --accent: #00ff88;
            --light: #ffffff;
            --dark: #000000;
        }

        body {
            background-color: var(--dark);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Загрузочная анимация */
        .loader-wrapper {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--dark);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }

        .loader {
            width: 100px;
            height: 100px;
            border: 5px solid var(--secondary);
            border-top: 5px solid var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Боковое меню */
        .side-menu {
            position: fixed;
            right: -300px;
            top: 0;
            width: 300px;
            height: 100%;
            background: rgba(26, 26, 26, 0.95);
            backdrop-filter: blur(10px);
            padding: 40px;
            transition: 0.5s;
            z-index: 1000;
        }

        .menu-btn {
            position: fixed;
            right: 30px;
            top: 30px;
            z-index: 1001;
            background: none;
            border: none;
            color: var(--accent);
            font-size: 30px;
            cursor: pointer;
        }

        .side-menu.active {
            right: 0;
        }

        .side-menu ul {
            list-style: none;
            margin-top: 50px;
        }

        .side-menu ul li {
            margin: 20px 0;
        }

        .side-menu ul li a {
            color: var(--light);
            text-decoration: none;
            font-size: 1.2rem;
            transition: 0.3s;
            display: block;
            padding: 10px;
            border-left: 3px solid transparent;
        }

        .side-menu ul li a:hover {
            color: var(--accent);
            border-left: 3px solid var(--accent);
            padding-left: 20px;
        }

        /* Герой секция */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(45deg, var(--primary), var(--dark));
        }

        .hero-content {
            text-align: center;
            z-index: 1;
        }

        .hero h1 {
            font-size: 4.5rem;
            margin-bottom: 20px;
            background: linear-gradient(45deg, var(--accent), #00ffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero p {
            font-size: 1.5rem;
            max-width: 800px;
            margin: 0 auto 30px;
        }

        /* Кнопки */
        .btn {
            display: inline-block;
            padding: 15px 40px;
            background: transparent;
            color: var(--accent);
            border: 2px solid var(--accent);
            border-radius: 30px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            margin: 10px;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--accent);
            transition: 0.5s;
            z-index: -1;
        }

        .btn:hover {
            color: var(--dark);
        }

        .btn:hover::before {
            left: 0;
        }

        /* Анимированные частицы */
        .particles {
            position: absolute;
            width: 100%;
            height: 100%;
        }

        .particle {
            position: absolute;
            background: var(--accent);
            border-radius: 50%;
            opacity: 0.3;
            animation: float 15s infinite;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 0.3; }
            50% { transform: translateY(-100px) rotate(180deg); opacity: 0.6; }
            100% { transform: translateY(0) rotate(360deg); opacity: 0.3; }
        }

        /* Секции */
        section {
            padding: 100px 20px;
            position: relative;
        }

        .section-title {
            font-size: 3rem;
            text-align: center;
            margin-bottom: 50px;
            color: var(--accent);
        }

        /* Карточки навыков */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 40px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
            transition: 0.5s;
            cursor: pointer;
        }

        .skill-card:hover {
            transform: translateY(-20px);
            background: rgba(255, 255, 255, 0.1);
        }

        .skill-icon {
            font-size: 3rem;
            color: var(--accent);
            margin-bottom: 20px;
        }

        /* Портфолио */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 40px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .project-card {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            aspect-ratio: 16/9;
        }

        .project-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 0.5s;
        }

        .project-info {
            position: absolute;
            bottom: -100%;
            left: 0;
            width: 100%;
            padding: 30px;
            background: rgba(0, 0, 0, 0.9);
            transition: 0.5s;
        }

        .project-card:hover .project-info {
            bottom: 0;
        }

        .project-card:hover img {
            transform: scale(1.1);
            filter: blur(3px);
        }

        /* Контактная форма */
        .contact-form {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.05);
            padding: 50px;
            border-radius: 20px;
            backdrop-filter: blur(10px);
        }

        .form-group {
            margin-bottom: 30px;
        }

        input, textarea {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border: none;
            border-radius: 10px;
            color: var(--light);
            font-size: 1.1rem;
            transition: 0.3s;
        }

        input:focus, textarea:focus {
            background: rgba(255, 255, 255, 0.15);
            outline: none;
        }

        textarea {
            height: 200px;
            resize: vertical;
        }

        /* Футер */
        footer {
            background: var(--primary);
            padding: 50px 20px;
            text-align: center;
        }

        .social-links {
            margin-bottom: 30px;
        }

        .social-links a {
            color: var(--light);
            font-size: 2rem;
            margin: 0 15px;
            transition: 0.3s;
        }

        .social-links a:hover {
            color: var(--accent);
            transform: translateY(-5px);
        }

        /* Медиа запросы */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 3rem;
            }
            
            .section-title {
                font-size: 2.5rem;
            }
            
            .skill-card {
                padding: 30px;
            }
        }
    </style>
</head>
<body>
    <!-- Загрузочная анимация -->
    <div class="loader-wrapper">
        <div class="loader"></div>
    </div>

    <!-- Боковое меню -->
    <button class="menu-btn" onclick="toggleMenu()">
        <i class="fas fa-bars"></i>
    </button>
    
    <div class="side-menu">
        <ul>
            <li><a href="#home">Главная</a></li>
            <li><a href="#about">Обо мне</a></li>
            <li><a href="#skills">Навыки</a></li>
            <li><a href="#services">Услуги</a></li>
            <li><a href="#portfolio">Портфолио</a></li>
            <li><a href="#contact">Контакты</a></li>
        </ul>
    </div>

    <!-- Главная секция -->
    <section id="home" class="hero">
        <div class="particles" id="particles"></div>
        <div class="hero-content" data-aos="fade-up">
            <h1>Разработчик Telegram-ботов</h1>
            <p>Создаю умных ботов для вашего бизнеса</p>
            <div class="buttons">
                <a href="#portfolio" class="btn">Мои работы</a>
                <a href="#contact" class="btn">Связаться</a>
            </div>
        </div>
    </section>

    <!-- Секция "Обо мне" -->
    <section id="about" data-aos="fade-up">
        <h2 class="section-title">Обо мне</h2>
        <div class="about-content">
            <p>Я специализируюсь на разработке умных и эффективных Telegram-ботов, которые помогают автоматизировать бизнес-процессы и улучшать коммуникацию с клиентами.</p>
        </div>
    </section>

    <!-- Секция навыков -->
    <section id="skills" data-aos="fade-up">
        <h2 class="section-title">Мои навыки</h2>
        <div class="skills-grid">
            <div class="skill-card" data-aos="flip-left">
                <i class="fas fa-robot skill-icon"></i>
                <h3>Telegram Bot API</h3>
                <p>Профессиональная разработка ботов любой сложности</p>
            </div>
            <div class="skill-card" data-aos="flip-left" data-aos-delay="200">
                <i class="fab fa-js skill-icon"></i>
                <h3>JavaScript</h3>
                <p>Создание современных и быстрых решений</p>
            </div>
            <div class="skill-card" data-aos="flip-left" data-aos-delay="400">
                <i class="fab fa-python skill-icon"></i>
                <h3>Python</h3>
                <p>Разработка backend и интеграция с ИИ</p>
            </div>
        </div>
    </section>

    <!-- Секция услуг -->
    <section id="services" data-aos="fade-up">
        <h2 class="section-title">Мои услуги</h2>
        <div class="skills-grid">
            <div class="skill-card" data-aos="zoom-in">
                <i class="fas fa-cogs skill-icon"></i>
                <h3>Автоматизация</h3>
                <p>Автоматизация бизнес-процессов</p>
                <a href="#contact" class="btn">Заказать</a>
            </div>
            <div class="skill-card" data-aos="zoom-in" data-aos-delay="200">
                <i class="fas fa-shopping-cart skill-icon"></i>
                <h3>Магазины</h3>
                <p>Создание магазинов в Telegram</p>
                <a href="#contact" class="btn">Заказать</a>
            </div>
            <div class="skill-card" data-aos="zoom-in" data-aos-delay="400">
                <i class="fas fa-brain skill-icon"></i>
                <h3>ИИ боты</h3>
                <p>Разработка умных ассистентов</p>
                <a href="#contact" class="btn">Заказать</a>
            </div>
        </div>
    </section>

    <!-- Портфолио -->
    <section id="portfolio" data-aos="fade-up">
        <h2 class="section-title">Мои проекты</h2>
        <div class="portfolio-grid">
            <div class="project-card" data-aos="fade-up">
                <img src="https://source.unsplash.com/random/800x600?bot" alt="Проект 1">
                <div class="project-info">
                    <h3>Бот для автоматизации</h3>
                    <p>Автоматизация бизнес-процессов и поддержка клиентов 24/7</p>
                    <a href="#" class="btn">Подробнее</a>
                </div>
            </div>
            <div class="project-card" data-aos="fade-up" data-aos-delay="200">
                <img src="https://source.unsplash.com/random/800x600?ai" alt="Проект 2">
                <div class="project-info">
                    <h3>Умный ассистент</h3>
                    <p>ИИ-бот для персональной поддержки</p>
                    <a href="#" class="btn">Подробнее</a>
                </div>
            </div>
            <div class="project-card" data-aos="fade-up" data-aos-delay="400">
                <img src="https://source.unsplash.com/random/800x600?shop" alt="Проект 3">
                <div class="project-info">
                    <h3>Магазин в Telegram</h3>
                    <p>Автоматизированный магазин с оплатой и CRM</p>
                    <a href="#" class="btn">Подробнее</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Контактная форма -->
    <section id="contact" data-aos="fade-up">
        <h2 class="section-title">Связаться со мной</h2>
        <form class="contact-form" data-aos="zoom-in">
            <div class="form-group">
                <input type="text" placeholder="Ваше имя" required>
            </div>
            <div class="form-group">
                <input type="email" placeholder="Ваш email" required>
            </div>
            <div class="form-group">
                <textarea placeholder="Ваше сообщение" required></textarea>
            </div>
            <button type="submit" class="btn">Отправить</button>
        </form>
    </section>

    <!-- Футер -->
    <footer>
        <div class="social-links">
            <a href="#"><i class="fab fa-telegram"></i></a>
            <a href="#"><i class="fab fa-github"></i></a>
            <a href="#"><i class="fab fa-linkedin"></i></a>
        </div>
        <p>© 2025 Разработчик Telegram-ботов. Все права защищены.</p>
    </footer>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // Инициализация AOS
        AOS.init({
            duration: 1000,
            once: true
        });

        // Загрузочная анимация
        window.addEventListener('load', function() {
            const loader = document.querySelector('.loader-wrapper');
            loader.style.opacity = '0';
            setTimeout(() => {
                loader.style.display = 'none';
            }, 1000);
        });

        // Боковое меню
        function toggleMenu() {
            document.querySelector('.side-menu').classList.toggle('active');
        }

        // Создание частиц
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            for(let i = 0; i < 50; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.width = Math.random() * 5 + 'px';
                particle.style.height = particle.style.width;
                particle.style.animationDelay = Math.random() * 5 + 's';
                particlesContainer.appendChild(particle);
            }
        }
        createParticles();

        // Плавная прокрутка
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
                if(document.querySelector('.side-menu').classList.contains('active')) {
                    document.querySelector('.side-menu').classList.remove('active');
                }
            });
        });
    </script>
</body>
</html>