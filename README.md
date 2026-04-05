<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RedRrox Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

    <style>
        :root {
            --bg-gradient: linear-gradient(-45deg, #1e3c72, #2a5298, #ff512f, #dd2476);
            --text-color: white;
            --btn-bg: white;
            --btn-text: black;
            --glow: cyan;
        }

        /* Dark Mode Colors */
        [data-theme="dark"] {
            --bg-gradient: linear-gradient(-45deg, #0f0c29, #302b63, #24243e);
            --text-color: #e0e0e0;
            --btn-bg: #444;
            --btn-text: white;
            --glow: #ff00ff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            transition: 0.5s ease;
        }

        body {
            min-height: 100vh;
            background: var(--bg-gradient);
            background-size: 400% 400%;
            animation: gradientBG 12s ease infinite;
            color: var(--text-color);
            text-align: center;
            overflow-x: hidden;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        section {
            padding: 100px 20px;
            max-width: 800px;
            margin: 0 auto;
        }

        h1 {
            font-size: 45px;
            text-shadow: 0 0 10px var(--glow), 0 0 20px var(--glow);
            margin-bottom: 20px;
        }

        .static-text {
            font-size: 22px;
            margin-top: 10px;
            font-weight: 300;
        }

        .fade {
            opacity: 0;
            transform: translateY(30px);
        }

        .fade.show {
            opacity: 1;
            transform: translateY(0);
        }

        .btn {
            display: inline-block;
            margin: 15px 10px;
            padding: 12px 30px;
            background: var(--btn-bg);
            color: var(--btn-text);
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .btn:hover {
            transform: scale(1.1) rotate(3deg);
            background: var(--btn-text);
            color: var(--btn-bg);
        }

        /* --- Theme Toggle Button (Top Right) --- */
        .theme-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            width: 55px;
            height: 55px;
            background: #ffdb58;
            border: none;
            border-radius: 50%;
            font-size: 24px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 0 15px rgba(255, 219, 88, 0.6);
            z-index: 1000;
            animation: sunPulse 3s infinite alternate;
        }

        [data-theme="dark"] .theme-toggle {
            background: #bdc3c7;
            box-shadow: 0 0 15px rgba(189, 195, 199, 0.4);
        }

        @keyframes sunPulse {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

        canvas { position: fixed; top: 0; left: 0; z-index: -1; }

        @media (max-width: 600px) {
            h1 { font-size: 32px; }
            .theme-toggle { width: 45px; height: 45px; top: 15px; right: 15px; font-size: 20px; }
            section { padding: 60px 15px; }
        }
    </style>
</head>

<body>

    <canvas id="particles"></canvas>

    <button class="theme-toggle" id="themeBtn" onclick="toggleTheme()" title="Switch Theme">☀️</button>

    <section>
        <h1>Hi, I'm RedRrox 😎</h1>
        <div class="static-text">Welcome to my Website 🔥</div>
        <a href="#contact" class="btn">Contact Me</a>
        <a href="http://www.youtube.com/@redrrox/" target="_blank" class="btn">My Channel</a>
    </section>

    <section class="fade">
        <h1>About Me</h1>
        <p>🎮 Welcome to My Gaming Universe 🎥<br><br>
        This isn’t just a website — this is my battlefield. I’m a passionate gamer and content creator on a mission to level up every single day.</p>
    </section>

    <section id="contact" class="fade">
        <h1>Contact</h1>
        <p>Feel free to reach out for collaborations or gaming sessions!</p>
    </section>

    <script>
        function toggleTheme() {
            const body = document.body;
            const btn = document.getElementById("themeBtn");
            
            if (body.getAttribute("data-theme") === "dark") {
                body.removeAttribute("data-theme");
                btn.innerText = "☀️";
                btn.style.background = "#ffdb58";
            } else {
                body.setAttribute("data-theme", "dark");
                btn.innerText = "🌙";
                btn.style.background = "#bdc3c7";
            }
        }

        /* Scroll Animation */
        window.addEventListener("scroll", function() {
            document.querySelectorAll(".fade").forEach(function(el) {
                if (el.getBoundingClientRect().top < window.innerHeight / 1.3) {
                    el.classList.add("show");
                }
            });
        });
        window.dispatchEvent(new Event('scroll'));

        /* Particle Logic */
        const canvas = document.getElementById("particles");
        const ctx = canvas.getContext("2d");
        
        function resize() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resize);
        resize();

        let particlesArray = [];
        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 1;
                this.speedX = Math.random() * 1 - 0.5;
                this.speedY = Math.random() * 1 - 0.5;
            }
            update() {
                this.x += this.speedX; this.y += this.speedY;
                if (this.x > canvas.width) this.x = 0;
                if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0;
                if (this.y < 0) this.y = canvas.height;
            }
            draw() {
                ctx.fillStyle = "white";
                ctx.beginPath(); ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2); ctx.fill();
            }
        }
        function init() { particlesArray = []; for (let i = 0; i < 80; i++) { particlesArray.push(new Particle()); } }
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < particlesArray.length; i++) {
                particlesArray[i].update(); particlesArray[i].draw();
            }
            requestAnimationFrame(animate);
        }
        init(); animate();
    </script>
</body>
</html>
