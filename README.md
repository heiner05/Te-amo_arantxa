<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Te Amo Arantxa</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: black;
    }
    canvas {
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 0;
    }
    h1 {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: #ff69b4;
      font-family: monospace;
      font-size: 2.5em;
      text-align: center;
      z-index: 1;
    }
  </style>
</head>
<body>
  <canvas id="canvas"></canvas>
 
  <h1>Te Amo Arantxa 💖</h1>
  <script>
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    function drawHeart(x, y, size) {
      ctx.beginPath();
      ctx.moveTo(x, y);
      ctx.bezierCurveTo(x, y - size / 2, x - size, y - size / 2, x - size, y);
      ctx.bezierCurveTo(x - size, y + size, x, y + size * 1.5, x, y + size * 2);
      ctx.bezierCurveTo(x, y + size * 1.5, x + size, y + size, x + size, y);
      ctx.bezierCurveTo(x + size, y - size / 2, x, y - size / 2, x, y);
      ctx.fillStyle = '#ff69b4';
      ctx.fill();
    }

    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      for (let i = 0; i < 50; i++) {
        drawHeart(
          Math.random() * canvas.width,
          Math.random() * canvas.height,
          10 + Math.random() * 20
        );
      }
      requestAnimationFrame(animate);
    }

    animate();
  </script>
</body>
</html>
