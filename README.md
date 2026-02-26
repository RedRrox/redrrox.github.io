# redrrox.github.io
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ultimate Animated Website</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Poppins', sans-serif;
}

body{
    background: linear-gradient(-45deg, #1e3c72, #2a5298, #ff512f, #dd2476);
    background-size:400% 400%;
    animation: gradientBG 12s ease infinite;
    color:white;
    text-align:center;
    overflow-x:hidden;
}

@keyframes gradientBG {
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
}

section{
    padding:100px 20px;
}

h1{
    font-size:50px;
}

.typing{
    font-size:22px;
    margin-top:20px;
    border-right:3px solid white;
    width:0;
    overflow:hidden;
    white-space:nowrap;
    animation: typing 4s steps(30,end) forwards, blink .8s infinite;
}

@keyframes typing{
    from{width:0}
    to{width:100%}
}

@keyframes blink{
    50%{border-color:transparent}
}

.fade{
    opacity:0;
    transform:translateY(40px);
    transition:1s;
}

.fade.show{
    opacity:1;
    transform:translateY(0);
}

.btn{
    display:inline-block;
    margin-top:30px;
    padding:12px 30px;
    background:white;
    color:black;
    border-radius:30px;
    text-decoration:none;
    font-weight:600;
    transition:0.4s;
}

.btn:hover{
    background:black;
    color:white;
    transform:scale(1.1) rotate(3deg);
}

/* Particle Canvas */
canvas{
    position:fixed;
    top:0;
    left:0;
    z-index:-1;
}
</style>
</head>

<body>

<canvas id="particles"></canvas>

<section>
    <h1>Hi, I'm RedRrox 😎</h1>
    <div class="typing">Welcome to my Ultimate Animated Website 🔥</div>
    <a href="#" class="btn">Explore More</a>
</section>

<section class="fade">
    <h1>About Me</h1>
    <p>I build cool websites using GitHub Pages 🚀</p>
</section>

<section class="fade">
    <h1>Contact</h1>
    <p>Email: your@email.com</p>
</section>

<script>
/* Scroll Animation */
window.addEventListener("scroll", function(){
    document.querySelectorAll(".fade").forEach(function(el){
        var position = el.getBoundingClientRect().top;
        var screenPosition = window.innerHeight / 1.3;
        if(position < screenPosition){
            el.classList.add("show");
        }
    });
});

/* Particle Animation */
const canvas = document.getElementById("particles");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particlesArray = [];

class Particle{
    constructor(){
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 3 + 1;
        this.speedX = Math.random() * 1 - 0.5;
        this.speedY = Math.random() * 1 - 0.5;
    }
    update(){
        this.x += this.speedX;
        this.y += this.speedY;
    }
    draw(){
        ctx.fillStyle = "white";
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI*2);
        ctx.fill();
    }
}

function init(){
    for(let i=0;i<100;i++){
        particlesArray.push(new Particle());
    }
}

function animate(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    for(let i=0;i<particlesArray.length;i++){
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
