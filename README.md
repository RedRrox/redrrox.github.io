<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RedRrox Portfolio</title>

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: linear-gradient(-45deg, #1e3c72, #2a5298, #ff512f, #dd2476);
            background-size: 400% 400%;
            animation: gradientBG 12s ease infinite;
            color: white;
            text-align: center;
            overflow-x: hidden;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        section {
            padding: 80px 20px;
            max-width: 800px;
            margin: 0 auto;
        }

        h1 {
            font-size: 45px;
            text-shadow: 0 0 10px cyan, 0 0 20px cyan;
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
            transition: 1s ease-out;
        }

        .fade.show {
            opacity: 1;
            transform: translateY(0);
        }

        .btn {
            display: inline-block;
            margin: 15px 10px;
            padding: 12px 30px;
            background: white;
            color: black;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            transition: 0.4s;
        }

        .btn:hover {
            background: black;
            color: white;
            transform: scale(1.1) rotate(3deg);
        }

        canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }

        p {
            line-height: 1.6;
            font-size: 16px;
            margin-top: 20px;
        }

        /* --- Mobile Optimization --- */
        @media (max-width: 600px) {
            h1 { font-size: 32px; }
            .static-text { font-size: 18px; }
            section { padding: 50px 15px; }
            .btn { padding: 10px 20px; font-size: 14px; }
        }
    </style>
</head>

<body>

    <canvas id="particles"></canvas>

    <section>
        <h1>Hi, I'm RedRrox 😎</h1>
        <div class="static-text">Welcome to my Website 🔥</div>
        <a href="#contact" class="btn">Contact Me</a>
        <a href="http://www.youtube.com/@redrrox/" target="_blank" class="btn">My Channel</a>
    </section>

    <section class="fade">
        <h1>About Me</h1>
        <p>🎮 Welcome to My Gaming Universe 🎥<br><br>
        This isn’t just a website — this is my battlefield. I’m a passionate gamer and content creator on a mission to level up every single day. Gaming is not just a hobby for me, it’s a lifestyle. I create high-quality gameplay videos, exciting live streams, walkthroughs, and tips & tricks.</p>
    </section>

    <section id="contact" class="fade">
        <h1>Contact</h1>
        <p>Feel free to reach out for collaborations or gaming sessions!</p>
    </section>

    <script>
        /* Scroll Animation Logic */
        window.addEventListener("scroll", function() {
            document.querySelectorAll(".fade").forEach(function(el) {
                var position = el.getBoundingClientRect().top;
                var screenPosition = window.innerHeight / 1.3;
                if (position < screenPosition) {
                    el.classList.add("show");
                }
            });
        });

        /* Particle Animation Logic */
        const canvas = document.getElementById("particles");
        const ctx = canvas.getContext("2d");
        
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        let particlesArray = [];

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedX = Math.random() * 1 - 0.5;
                this.speedY = Math.random() * 1 - 0.5;
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;

                if (this.x > canvas.width) this.x = 0;
                if (this.x < 0) this.x = canvas.width;
                if (this.y > canvas.height) this.y = 0;
                if (this.y < 0) this.y = canvas.height;
            }
            draw() {
                ctx.fillStyle = "white";
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function init() {
            particlesArray = [];
            for (let i = 0; i < 80; i++) {
                particlesArray.push(new Particle());
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < particlesArray.length; i++) {
                particlesArray[i].update();
                particlesArray[i].draw();
            }
            requestAnimationFrame(animate);
        }

        init();
        animate();
    </script>

</body>
</html>
