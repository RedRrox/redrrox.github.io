# redrrox.github.io
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Animated Website</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Poppins', sans-serif;
}

body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background: linear-gradient(-45deg, #1e3c72, #2a5298, #ff512f, #dd2476);
    background-size:400% 400%;
    animation: gradientBG 10s ease infinite;
    color:white;
    text-align:center;
}

@keyframes gradientBG {
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
}

.container{
    animation: fadeIn 2s ease-in-out;
}

@keyframes fadeIn {
    from{opacity:0; transform:translateY(30px);}
    to{opacity:1; transform:translateY(0);}
}

h1{
    font-size:50px;
    animation: slideIn 2s ease-in-out;
}

@keyframes slideIn{
    from{letter-spacing:20px; opacity:0;}
    to{letter-spacing:2px; opacity:1;}
}

p{
    margin-top:20px;
    font-size:20px;
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
    transform:scale(1.1);
}
</style>
</head>

<body>

<div class="container">
    <h1>Hi, I'm Crazy 😎</h1>
    <p>This website has cool animations 🔥</p>
    <a href="#" class="btn">Explore</a>
</div>

</body>
</html>
