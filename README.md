<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animated GitHub Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(-45deg, #1a1a2e, #16213e, #0f3460, #533483);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            color: white;
            overflow-x: hidden;
            min-height: 100vh;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .star {
            position: absolute;
            width: 2px;
            height: 2px;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0; }
            50% { opacity: 1; }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            padding: 60px 0;
            position: relative;
        }

        .profile-pic {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 4px solid #00d4ff;
            margin: 0 auto 30px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
            animation: rotate 8s linear infinite, pulse 2s ease-in-out infinite alternate;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @keyframes pulse {
            from { box-shadow: 0 0 20px #00d4ff; }
            to { box-shadow: 0 0 40px #00d4ff, 0 0 60px #00d4ff; }
        }

        .name {
            font-size: 3.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4, #feca57);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: textGradient 4s ease infinite;
            margin-bottom: 20px;
        }

        @keyframes textGradient {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .tagline {
            font-size: 1.5rem;
            opacity: 0.9;
            animation: fadeInUp 2s ease;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 0.9;
                transform: translateY(0);
            }
        }

        .section {
            margin: 60px 0;
            padding: 40px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            animation: slideInLeft 1s ease;
        }

        .section:nth-child(even) {
            animation: slideInRight 1s ease;
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .section h2 {
            font-size: 2.5rem;
            margin-bottom: 30px;
            text-align: center;
            color: #00d4ff;
            text-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .tech-item {
            background: linear-gradient(45deg, rgba(255, 107, 107, 0.3), rgba(78, 205, 196, 0.3));
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
            animation: bounce 2s ease infinite;
            animation-delay: calc(var(--i) * 0.1s);
        }

        .tech-item:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.3);
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }

        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
            padding: 30px;
            border-radius: 20px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
            animation: float 3s ease-in-out infinite;
            animation-delay: calc(var(--i) * 0.5s);
        }

        .stat-card:hover {
            transform: translateY(-15px) rotateY(10deg);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .stat-number {
            font-size: 3rem;
            font-weight: bold;
            color: #00d4ff;
            margin-bottom: 10px;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .project-card {
            background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(78, 205, 196, 0.2));
            padding: 30px;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            animation: shimmer 3s linear infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .project-card:hover {
            transform: translateY(-10px) rotateX(5deg);
            box-shadow: 0 30px 60px rgba(0, 212, 255, 0.2);
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .contact-link {
            display: inline-block;
            padding: 15px 30px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            transition: all 0.3s ease;
            animation: glow 2s ease-in-out infinite alternate;
        }

        .contact-link:hover {
            transform: translateY(-5px) scale(1.1);
            box-shadow: 0 10px 30px rgba(255, 107, 107, 0.5);
        }

        @keyframes glow {
            from { box-shadow: 0 0 20px rgba(255, 107, 107, 0.5); }
            to { box-shadow: 0 0 30px rgba(78, 205, 196, 0.5); }
        }

        .typing-animation {
            border-right: 3px solid #00d4ff;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { border-color: transparent; }
            51%, 100% { border-color: #00d4ff; }
        }

        @media (max-width: 768px) {
            .name { font-size: 2.5rem; }
            .tagline { font-size: 1.2rem; }
            .section h2 { font-size: 2rem; }
            .section { padding: 20px; margin: 30px 0; }
        }
    </style>
</head>
<body>
    <div class="stars"></div>
    
    <div class="container">
        <div class="header">
            <div class="profile-pic">👨‍💻</div>
            <h1 class="name">YOUR NAME</h1>
            <p class="tagline typing-animation">Full Stack Developer & Tech Enthusiast</p>
        </div>

        <div class="section">
            <h2>🚀 About Me</h2>
            <p style="font-size: 1.2rem; line-height: 1.8; text-align: center;">
                Passionate developer with a love for creating amazing digital experiences. 
                Currently building the future, one line of code at a time. Always learning, 
                always growing, always coding! ✨
            </p>
        </div>

        <div class="section">
            <h2>🛠️ Tech Arsenal</h2>
            <div class="tech-grid">
                <div class="tech-item" style="--i: 0;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">⚛️</div>
                    <div>React</div>
                </div>
                <div class="tech-item" style="--i: 1;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">📱</div>
                    <div>React Native</div>
                </div>
                <div class="tech-item" style="--i: 2;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">🟢</div>
                    <div>Node.js</div>
                </div>
                <div class="tech-item" style="--i: 3;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">🐍</div>
                    <div>Python</div>
                </div>
                <div class="tech-item" style="--i: 4;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">🗄️</div>
                    <div>MongoDB</div>
                </div>
                <div class="tech-item" style="--i: 5;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">☁️</div>
                    <div>AWS</div>
                </div>
                <div class="tech-item" style="--i: 6;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">🔥</div>
                    <div>Firebase</div>
                </div>
                <div class="tech-item" style="--i: 7;">
                    <div style="font-size: 2rem; margin-bottom: 10px;">📊</div>
                    <div>GraphQL</div>
                </div>
            </div>
        </div>

        <div class="section">
            <h2>📊 GitHub Stats</h2>
            <div class="stats-container">
                <div class="stat-card" style="--i: 0;">
                    <div class="stat-number">100+</div>
                    <div>Repositories</div>
                </div>
                <div class="stat-card" style="--i: 1;">
                    <div class="stat-number">500+</div>
                    <div>Contributions</div>
                </div>
                <div class="stat-card" style="--i: 2;">
                    <div class="stat-number">50+</div>
                    <div>Stars Earned</div>
                </div>
                <div class="stat-card" style="--i: 3;">
                    <div class="stat-number">10+</div>
                    <div>Languages</div>
                </div>
            </div>
        </div>

        <div class="section">
            <h2>🔥 Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <h3 style="color: #00d4ff; margin-bottom: 15px;">🚀 Awesome Web App</h3>
                    <p>A full-stack application built with React and Node.js. Features real-time chat, user authentication, and responsive design.</p>
                </div>
                <div class="project-card">
                    <h3 style="color: #00d4ff; margin-bottom: 15px;">📱 Mobile App</h3>
                    <p>Cross-platform mobile application using React Native. Includes offline support, push notifications, and sleek UI.</p>
                </div>
                <div class="project-card">
                    <h3 style="color: #00d4ff; margin-bottom: 15px;">🤖 AI Assistant</h3>
                    <p>Machine learning project that helps automate daily tasks. Built with Python and TensorFlow for intelligent automation.</p>
                </div>
            </div>
        </div>

        <div class="section">
            <h2>🤝 Let's Connect</h2>
            <div class="contact-links">
                <a href="mailto:your.email@example.com" class="contact-link">📧 Email</a>
                <a href="https://linkedin.com/in/yourprofile" class="contact-link">💼 LinkedIn</a>
                <a href="https://twitter.com/yourhandle" class="contact-link">🐦 Twitter</a>
                <a href="https://yourwebsite.com" class="contact-link">🌐 Website</a>
            </div>
        </div>
    </div>

    <script>
        // Create animated stars
        function createStars() {
            const starsContainer = document.querySelector('.stars');
            const numberOfStars = 100;

            for (let i = 0; i < numberOfStars; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDelay = Math.random() * 3 + 's';
                star.style.animationDuration = (Math.random() * 3 + 2) + 's';
                starsContainer.appendChild(star);
            }
        }

        // Typing animation for tagline
        function typeWriter(element, text, speed = 100) {
            let i = 0;
            element.innerHTML = '';
            function typing() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(typing, speed);
                }
            }
            typing();
        }

        // Initialize animations
        document.addEventListener('DOMContentLoaded', function() {
            createStars();
            
            // Typing animation for tagline
            setTimeout(() => {
                const tagline = document.querySelector('.tagline');
                typeWriter(tagline, 'Full Stack Developer & Tech Enthusiast');
            }, 2000);

            // Intersection Observer for scroll animations
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            };

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.animation = entry.target.classList.contains('section') 
                            ? 'slideInLeft 1s ease' 
                            : 'fadeInUp 1s ease';
                    }
                });
            }, observerOptions);

            // Observe all sections
            document.querySelectorAll('.section').forEach(section => {
                observer.observe(section);
            });
        });

        // Mouse movement parallax effect
        document.addEventListener('mousemove', (e) => {
            const stars = document.querySelectorAll('.star');
            const x = e.clientX / window.innerWidth;
            const y = e.clientY / window.innerHeight;

            stars.forEach((star, index) => {
                const speed = (index % 3 + 1) * 0.5;
                star.style.transform = `translate(${x * speed}px, ${y * speed}px)`;
            });
        });
    </script>
</body>
</html>
