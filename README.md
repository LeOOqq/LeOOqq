<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>GitHub Banner</title>
<link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&display=swap" rel="stylesheet">

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: "Fira Code", monospace;
    }

    body {
        background: #000;
        overflow: hidden;
    }

    .banner {
        position: relative;
        width: 1920px;
        height: 600px;
        background: radial-gradient(circle at center, #0a0f2c, #000);
        overflow: hidden;
    }

    /* Matrix digital rain */
    canvas {
        position: absolute;
        width: 100%;
        height: 100%;
        z-index: 1;
        opacity: 0.4;
    }

    /* Floating code fragments */
    .code {
        position: absolute;
        color: #00aaff;
        font-size: 14px;
        opacity: 0.6;
        animation: floatCode 12s linear infinite;
    }

    @keyframes floatCode {
        0% { transform: translateY(600px) rotate(0deg); }
        100% { transform: translateY(-600px) rotate(720deg); }
    }

    /* Hologram glowing UI Panel */
    .panel {
        position: absolute;
        top: 40px;
        left: 40px;
        width: 500px;
        height: 200px;
        border: 2px solid rgba(0, 170, 255, 0.7);
        background: rgba(0, 20, 40, 0.4);
        box-shadow: 0 0 25px #0099ff;
        border-radius: 10px;
        backdrop-filter: blur(6px);
        z-index: 3;
        animation: glow 3s ease-in-out infinite alternate;
    }

    @keyframes glow {
        0% { box-shadow: 0 0 20px #0066ff; }
        100% { box-shadow: 0 0 40px #00aaff; }
    }

    /* Text typing effect */
    .typing {
        color: #00c8ff;
        font-size: 32px;
        font-weight: bold;
        margin: 20px;
        white-space: nowrap;
        overflow: hidden;
        border-right: 2px solid #00c8ff;
        width: 0;
        animation: typing 4s steps(40, end) forwards, blink .7s infinite;
    }

    @keyframes typing {
        from { width: 0; }
        to { width: 460px; }
    }

    @keyframes blink {
        0% { border-color: transparent; }
        50% { border-color: #00c8ff; }
        100% { border-color: transparent; }
    }

    .subtitle {
        color: #9bdcff;
        font-size: 20px;
        margin-left: 20px;
        opacity: 0;
        animation: fadeIn 4s ease 4s forwards;
    }

    @keyframes fadeIn {
        to { opacity: 1; }
    }

    /* Neon Octocat */
    .octocat {
        position: absolute;
        right: 80px;
        bottom: 50px;
        width: 260px;
        filter: drop-shadow(0 0 20px #8e00ff);
        animation: float 6s ease-in-out infinite;
        z-index: 3;
    }

    @keyframes float {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-18px); }
    }

</style>
</head>

<body>
<div class="banner">

    <!-- Matrix Rain -->
    <canvas id="matrix"></canvas>

    <!-- Floating code fragments -->
    <div class="code" style="left: 300px; animation-duration: 14s;">for(int i=0;i<10;i++)</div>
    <div class="code" style="left: 900px; animation-duration: 11s;">print("Hello World");</div>
    <div class="code" style="left: 1500px; animation-duration: 13s;">if(user.isAdmin)</div>

    <!-- Hologram Panel -->
    <div class="panel">
        <div class="typing">Mehmet Yasin Çaldıran</div>
        <div class="subtitle">Computer Engineering • Mobile Development • Cyber Security</div>
    </div>

    <!-- Neon Octocat -->
    <img class="octocat" src="https://github.githubassets.com/images/modules/logos_page/Octocat.png" />

</div>

<script>
    // MATRIX RAIN ANIMATION
    const canvas = document.getElementById("matrix");
    const ctx = canvas.getContext("2d");

    canvas.width = 1920;
    canvas.height = 600;

    const letters = "01";
    const fontSize = 16;
    const columns = canvas.width / fontSize;

    const drops = Array(Math.floor(columns)).fill(1);

    function drawMatrix() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        ctx.fillStyle = "#00ffff";
        ctx.font = fontSize + "px monospace";

        drops.forEach((y, i) => {
            const text = letters[Math.floor(Math.random() * letters.length)];
            ctx.fillText(text, i * fontSize, y * fontSize);

            if (y * fontSize > canvas.height && Math.random() > 0.975) {
                drops[i] = 0;
            }

            drops[i]++;
        });
    }

    setInterval(drawMatrix, 33);
</script>

</body>
</html>
