# Hellooooooooo 
<!DOCTYPE html>
<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #000; /* Entire page black */
      color: #fff;
      text-align: center;
      padding-top: 40px;
    }
    h1 {
      font-size: 2.5em;
      color: #00ffcc;
      text-shadow: 2px 2px 8px #00ffaa;
    }
    p {
      font-size: 1.2em;
      margin: 10px 0;
    }
    canvas {
      display: block;
      margin: 30px auto;
      background: #111;
      border: 1px solid #444;
    }
  </style>
</head>
<body>
  <h1>📊 Hi Sagar, Good Morning 📊</h1>
  <p>💹 "Trade smart, accept losses, ride profits." 💹</p>
  <p>💡 Get up, let’s start the day with lots of new things 💡</p>
  <p>🙏 Remember, God is with you always 🙏</p>

  <!-- Animated Trading Line -->
  <canvas id="chart" width="600" height="250"></canvas>

  <script>
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');

    function drawLine() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.beginPath();
      ctx.moveTo(0, 150);
      for (let x = 0; x < canvas.width; x++) {
        // Simulate profit/loss waves
        let y = 150 + 60 * Math.sin(x * 0.05 + Date.now() * 0.003);
        ctx.lineTo(x, y);
      }
      ctx.strokeStyle = '#00ff00'; // Green line for profit/loss
      ctx.lineWidth = 2;
      ctx.stroke();
    }

    setInterval(drawLine, 50);
  </script>
</body>
</html>
