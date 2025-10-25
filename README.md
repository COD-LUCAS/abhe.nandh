# abhenandh
I’m creating a simple personal website using HTML and CSS that displays my name and basic details. It includes sections for my introduction, contact info, and profile, designed with a clean and minimal layout to practice and showcase my basic web development skills.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Modern Portfolio - Future Ready</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #00f3ff;
            --secondary: #7b2ff7;
            --dark: #0a0e27;
            --light: #ffffff;
            --gray: #8892b0;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--dark);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Navigation */
        nav {
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            background: rgba(10, 14, 39, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(0, 243, 255, 0.1);
        }

        nav .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            gap: 40px;
            list-style: none;
        }

        .nav-links a {
            color: var(--gray);
            text-decoration: none;
            transition: color 0.3s;
            position: relative;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding-top: 80px;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 50%, rgba(123, 47, 247, 0.1), transparent 50%),
                        radial-gradient(circle at 80% 80%, rgba(0, 243, 255, 0.1), transparent 50%);
            pointer-events: none;
        }

        .hero-content {
            position: relative;
            z-index: 1;
        }

        .hero h1 {
            font-size: 72px;
            margin-bottom: 20px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: fadeInUp 0.8s ease;
        }

        .hero p {
            font-size: 20px;
            color: var(--gray);
            margin-bottom: 40px;
            animation: fadeInUp 0.8s ease 0.2s both;
        }

        .btn {
            display: inline-block;
            padding: 15px 40px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: var(--light);
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: transform 0.3s, box-shadow 0.3s;
            animation: fadeInUp 0.8s ease 0.4s both;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 243, 255, 0.3);
        }

        /* About Section */
        .about {
            padding: 100px 0;
            background: linear-gradient(180deg, var(--dark), rgba(10, 14, 39, 0.95));
        }

        .section-title {
            font-size: 48px;
            margin-bottom: 60px;
            text-align: center;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -20px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
        }

        .about-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-top: 80px;
        }

        .feature-card {
            padding: 40px;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(0, 243, 255, 0.1);
            border-radius: 20px;
            transition: transform 0.3s, border-color 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
        }

        .feature-icon {
            font-size: 48px;
            margin-bottom: 20px;
        }

        .feature-card h3 {
            font-size: 24px;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .feature-card p {
            color: var(--gray);
        }

        /* Projects Section */
        .projects {
            padding: 100px 0;
        }

        .project-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 80px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(0, 243, 255, 0.1);
            border-radius: 20px;
            overflow: hidden;
            transition: transform 0.3s;
        }

        .project-card:hover {
            transform: scale(1.05);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
        }

        .project-info {
            padding: 30px;
        }

        .project-info h3 {
            font-size: 24px;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .project-info p {
            color: var(--gray);
            margin-bottom: 20px;
        }

        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .tag {
            padding: 5px 15px;
            background: rgba(0, 243, 255, 0.1);
            border: 1px solid var(--primary);
            border-radius: 20px;
            font-size: 12px;
            color: var(--primary);
        }

        /* Contact Section */
        .contact {
            padding: 100px 0;
            background: linear-gradient(180deg, var(--dark), rgba(10, 14, 39, 0.95));
        }

        .contact-content {
            max-width: 600px;
            margin: 80px auto 0;
            text-align: center;
        }

        .contact-content p {
            font-size: 18px;
            color: var(--gray);
            margin-bottom: 40px;
        }

        /* Footer */
        footer {
            padding: 40px 0;
            text-align: center;
            border-top: 1px solid rgba(0, 243, 255, 0.1);
            color: var(--gray);
        }

        /* Animations */
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

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                gap: 20px;
            }

            .hero h1 {
                font-size: 48px;
            }

            .section-title {
                font-size: 36px;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="container">
            <div class="logo">PORTFOLIO</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Future Ready<br>Web Development</h1>
                <p>Building modern, responsive, and high-performance web applications</p>
                <a href="#projects" class="btn">View Projects</a>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
        <div class="container">
            <h2 class="section-title">What We Do</h2>
            <div class="about-content">
                <div class="feature-card">
                    <div class="feature-icon">⚡</div>
                    <h3>Fast Performance</h3>
                    <p>Lightning-fast load times and optimized code for the best user experience.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">📱</div>
                    <h3>Responsive Design</h3>
                    <p>Perfect display on all devices from mobile phones to desktop monitors.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🎨</div>
                    <h3>Modern UI/UX</h3>
                    <p>Beautiful interfaces with smooth animations and intuitive navigation.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🔒</div>
                    <h3>Secure & Reliable</h3>
                    <p>Built with security best practices and reliable hosting solutions.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="project-grid">
                <div class="project-card">
                    <div class="project-image">🚀</div>
                    <div class="project-info">
                        <h3>Project Alpha</h3>
                        <p>A modern web application with cutting-edge features and sleek design.</p>
                        <div class="tech-tags">
                            <span class="tag">HTML5</span>
                            <span class="tag">CSS3</span>
                            <span class="tag">JavaScript</span>
                        </div>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-image">💎</div>
                    <div class="project-info">
                        <h3>Project Beta</h3>
                        <p>Responsive portfolio showcasing creative work with smooth animations.</p>
                        <div class="tech-tags">
                            <span class="tag">Responsive</span>
                            <span class="tag">Modern</span>
                            <span class="tag">Fast</span>
                        </div>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-image">🌟</div>
                    <div class="project-info">
                        <h3>Project Gamma</h3>
                        <p>E-commerce platform with advanced features and secure payments.</p>
                        <div class="tech-tags">
                            <span class="tag">E-commerce</span>
                            <span class="tag">Secure</span>
                            <span class="tag">Scalable</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <div class="contact-content">
                <p>Ready to start your next project? Let's build something amazing together.</p>
                <a href="mailto:contact@example.com" class="btn">Contact Us</a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2025 Portfolio. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling for navigation links
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

        // Add scroll effect to navigation
        window.addEventListener('scroll', () => {
            const nav = document.querySelector('nav');
            if (window.scrollY > 100) {
                nav.style.boxShadow = '0 10px 30px rgba(0, 0, 0, 0.3)';
            } else {
                nav.style.boxShadow = 'none';
            }
        });
    </script>
</body>
</html>
