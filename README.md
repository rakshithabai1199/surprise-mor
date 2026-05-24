#Hellooooooo
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
  <p>💹 "In trading, losses are lessons and profits are rewards." 💹</p>
  <p>💡 Get up, let’s start the day with lots of new things 💡</p>
  <p>🙏 Remember, God is with you always 🙏</p>

  <!-- Candlestick Chart -->
  <canvas id="chart" width="600" height="300"></canvas>

  <script>
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');

    function drawCandles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      let candleWidth = 20;
      let gap = 10;
      let x = 30;

      for (let i = 0; i < 20; i++) {
        // Random open/close values
        let open = 150 + Math.random() * 80 - 40;
        let close = 150 + Math.random() * 80 - 40;
        let high = Math.max(open, close) + Math.random() * 20;
        let low = Math.min(open, close) - Math.random() * 20;

        // Candle color: green if close > open, red otherwise
        ctx.strokeStyle = "#fff";
        ctx.beginPath();
        ctx.moveTo(x + candleWidth/2, low);
        ctx.lineTo(x + candleWidth/2, high);
        ctx.stroke();

        ctx.fillStyle = close > open ? "#00ff00" : "#ff3333";
        ctx.fillRect(x, Math.min(open, close), candleWidth, Math.abs(close - open));

        x += candleWidth + gap;
      }
    }

    setInterval(drawCandles, 1000);
  </script>
</body>
</html>
