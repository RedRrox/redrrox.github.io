# redrrox.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My Cool Website</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

    <style>
        *{
            margin:0;
            padding:0;
            box-sizing:border-box;
            font-family:'Poppins', sans-serif;
        }

        body{
            background: linear-gradient(135deg,#1e3c72,#2a5298);
            color:white;
            text-align:center;
        }

        nav{
            background: rgba(0,0,0,0.3);
            padding:15px;
        }

        nav a{
            color:white;
            text-decoration:none;
            margin:0 15px;
            font-weight:600;
        }

        nav a:hover{
            color:yellow;
        }

        .hero{
            padding:100px 20px;
        }

        .hero h1{
            font-size:50px;
        }

        .hero p{
            margin-top:20px;
            font-size:20px;
        }

        .btn{
            display:inline-block;
            margin-top:30px;
            padding:12px 25px;
            background:yellow;
            color:black;
            border-radius:30px;
            text-decoration:none;
            font-weight:600;
            transition:0.3s;
        }

        .btn:hover{
            background:white;
        }

        footer{
            margin-top:80px;
            padding:20px;
            background:rgba(0,0,0,0.3);
        }
    </style>
</head>
<body>

    <nav>
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Contact</a>
    </nav>

    <section class="hero">
        <h1>Hi, I'm Crazy 😎</h1>
        <p>Welcome to my awesome website built with GitHub Pages!</p>
        <a href="#" class="btn">Contact Me</a>
    </section>

    <footer>
        <p>© 2026 Crazy | All Rights Reserved</p>
    </footer>

</body>
</html>
