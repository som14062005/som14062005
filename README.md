<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Praveen Somasundaram - 3D Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }

        /* Animated Background Particles */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .particle {
            position: absolute;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            33% { transform: translateY(-30px) rotate(120deg); }
            66% { transform: translateY(-60px) rotate(240deg); }
        }

        /* Hero Section */
        .hero {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            text-align: center;
            padding: 2rem;
            position: relative;
        }

        .hero-title {
            font-size: 4rem;
            font-weight: 900;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
            background-size: 400% 400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease-in-out infinite;
            transform: perspective(1000px) rotateX(15deg);
            text-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .hero-subtitle {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0.9;
            animation: slideUp 1s ease-out 0.5s both;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 0.9;
                transform: translateY(0);
            }
        }

        /* 3D Card Container */
        .card-container {
            perspective: 1000px;
            margin: 4rem auto;
            max-width: 1200px;
            padding: 0 2rem;
        }

        .profile-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border-radius: 30px;
            padding: 3rem;
            transform-style: preserve-3d;
            transition: transform 0.6s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 40px 80px rgba(0, 0, 0, 0.3);
            animation: cardFloat 4s ease-in-out infinite;
        }

        @keyframes cardFloat {
            0%, 100% { transform: translateY(0px) rotateY(0deg); }
            25% { transform: translateY(-10px) rotateY(2deg); }
            50% { transform: translateY(-15px) rotateY(0deg); }
            75% { transform: translateY(-10px) rotateY(-2deg); }
        }

        .profile-card:hover {
            transform: rotateX(5deg) rotateY(5deg) translateZ(20px);
        }

        /* Skills Section */
        .skills-section {
            margin: 3rem 0;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 2rem;
            background: linear-gradient(45deg, #ffd700, #ff8c00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .skill-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 1.5rem;
            border-radius: 20px;
            text-align: center;
            transform: translateZ(0);
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
        }

        .skill-item::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.5s ease;
            opacity: 0;
        }

        .skill-item:hover::before {
            opacity: 1;
            animation: shine 0.5s ease;
        }

        @keyframes shine {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .skill-item:hover {
            transform: translateY(-10px) rotateX(10deg);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            background: rgba(255, 255, 255, 0.15);
        }

        .skill-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            animation: bounce 2s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }

        /* Social Links */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin: 3rem 0;
            flex-wrap: wrap;
        }

        .social-link {
            display: inline-block;
            padding: 1rem 2rem;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s ease;
            transform: translateZ(0);
            position: relative;
            overflow: hidden;
        }

        .social-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: all 0.5s ease;
        }

        .social-link:hover::before {
            left: 100%;
        }

        .social-link:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
        }

        /* Contribution Graph Styling */
        .contribution-section {
            margin: 4rem 0;
            text-align: center;
        }

        .contribution-graph {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            padding: 2rem;
            margin: 2rem 0;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            animation: slideInUp 1s ease-out;
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

        .contribution-graph img {
            max-width: 100%;
            border-radius: 10px;
            filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.3));
        }

        /* Snake Animation Container */
        .snake-container {
            margin: 3rem 0;
            text-align: center;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 20px;
            padding: 2rem;
            backdrop-filter: blur(10px);
        }

        .snake-container img {
            max-width: 100%;
            border-radius: 15px;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero-title {
                font-size: 2.5rem;
            }
            
            .profile-card {
                margin: 2rem 1rem;
                padding: 2rem;
            }
            
            .skills-grid {
                grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
                gap: 1rem;
            }
            
            .social-links {
                gap: 1rem;
            }
        }

        /* Loading Animation */
        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            animation: fadeOut 2s ease-in-out 1s both;
        }

        @keyframes fadeOut {
            to {
                opacity: 0;
                visibility: hidden;
            }
        }

        .loading-spinner {
            width: 80px;
            height: 80px;
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top: 4px solid #fff;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Scroll indicator */
        .scroll-indicator {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            animation: scrollBounce 2s ease-in-out infinite;
        }

        @keyframes scrollBounce {
            0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
            40% { transform: translateX(-50%) translateY(-10px); }
            60% { transform: translateX(-50%) translateY(-5px); }
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading-overlay">
        <div class="loading-spinner"></div>
    </div>

    <!-- Animated Background Particles -->
    <div class="particles" id="particles"></div>

    <!-- Hero Section -->
    <section class="hero">
        <h1 class="hero-title">Hi there 👋 It's me<br>Praveen Somasundaram</h1>
        <p class="hero-subtitle">🚀 Emerging Tech Enthusiast & Engineering Student</p>
        <div class="scroll-indicator">
            <div style="font-size: 2rem; animation: bounce 2s ease-in-out infinite;">⬇️</div>
        </div>
    </section>

    <!-- Main Content -->
    <div class="card-container">
        <div class="profile-card">
            <!-- About Section -->
            <div style="text-align: center; margin-bottom: 3rem;">
                <h2 style="font-size: 2rem; margin-bottom: 1rem; color: #ffd700;">🛠️ About Me</h2>
                <p style="font-size: 1.2rem; line-height: 1.8; opacity: 0.9;">
                    🧠 Currently learning DSA in Java, Web Development and Exploring Other Domains<br>
                    🏢 Engineering Student At Rajalakshmi Engineering College, Thandalam
                </p>
            </div>

            <!-- Social Links -->
            <h2 class="section-title">📡 Connect With Me</h2>
            <div class="social-links">
                <a href="https://www.linkedin.com/in/praveen-somasundaram2005/" class="social-link" target="_blank">
                    LinkedIn 💼
                </a>
                <a href="https://instagram.com/yourusername" class="social-link" target="_blank">
                    Instagram 📸
                </a>
                <a href="https://www.naukri.com/mnjuser/profile?id=&altresid" class="social-link" target="_blank">
                    Naukri 🎯
                </a>
                <a href="#" class="social-link" target="_blank">
                    Portfolio 🌐
                </a>
            </div>

            <!-- Skills Section -->
            <div class="skills-section">
                <h2 class="section-title">💻 I Code In</h2>
                <div class="skills-grid">
                    <div class="skill-item">
                        <div class="skill-icon">🟨</div>
                        <h3>JavaScript</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">⚛️</div>
                        <h3>React</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🟢</div>
                        <h3>Node.js</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🌐</div>
                        <h3>HTML5</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🎨</div>
                        <h3>CSS3</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">☕</div>
                        <h3>Java</h3>
                    </div>
                </div>
            </div>

            <!-- Tools Section -->
            <div class="skills-section">
                <h2 class="section-title">🛠️ Tools & Technologies</h2>
                <div class="skills-grid">
                    <div class="skill-item">
                        <div class="skill-icon">🎯</div>
                        <h3>Figma</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">📮</div>
                        <h3>Postman</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">💻</div>
                        <h3>VS Code</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🔧</div>
                        <h3>Git</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🐘</div>
                        <h3>PostgreSQL</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🔥</div>
                        <h3>Firebase</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">🍃</div>
                        <h3>MongoDB</h3>
                    </div>
                    <div class="skill-item">
                        <div class="skill-icon">📊</div>
                        <h3>Jupyter</h3>
                    </div>
                </div>
            </div>

            <!-- GitHub Stats -->
            <div class="contribution-section">
                <h2 class="section-title">📊 GitHub Activity</h2>
                <div class="contribution-graph">
                    <img src="https://ghchart.rshah.org/5e60ce/som14062005" alt="GitHub Contribution Graph" style="max-width: 100%; border-radius: 10px;" />
                </div>
            </div>

            <!-- GitHub Snake -->
            <div class="snake-container">
                <h2 class="section-title">🐍 Contribution Snake</h2>
                <picture>
                    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/som14062005/som14062005/output/github-snake-dark.svg" />
                    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/som14062005/som14062005/output/github-snake.svg" />
                    <img alt="github-snake" src="https://raw.githubusercontent.com/som14062005/som14062005/output/github-snake.svg" style="max-width: 100%;" />
                </picture>
            </div>
        </div>
    </div>

    <script>
        // Create floating particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                
                const size = Math.random() * 4 + 1;
                particle.style.width = size + 'px';
                particle.style.height = size + 'px';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 3 + 4) + 's';
                
                particlesContainer.appendChild(particle);
            }
        }

        // Mouse movement parallax effect
        document.addEventListener('mousemove', (e) => {
            const mouseX = e.clientX / window.innerWidth;
            const mouseY = e.clientY / window.innerHeight;
            
            const cards = document.querySelectorAll('.profile-card, .skill-item');
            cards.forEach((card, index) => {
                const speed = (index + 1) * 0.5;
                const x = (mouseX - 0.5) * speed;
                const y = (mouseY - 0.5) * speed;
                card.style.transform += ` translate3d(${x}px, ${y}px, 0)`;
            });
        });

        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'slideInUp 0.8s ease-out both';
                }
            });
        }, observerOptions);

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            
            // Observe skill items for scroll animations
            document.querySelectorAll('.skill-item, .contribution-graph, .snake-container').forEach(el => {
                observer.observe(el);
            });
        });

        // Smooth scrolling
        document.addEventListener('click', (e) => {
            if (e.target.closest('.scroll-indicator')) {
                window.scrollTo({
                    top: window.innerHeight,
                    behavior: 'smooth'
                });
            }
        });
    </script>
</body>
</html>
