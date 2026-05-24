#Helloooo
<!DOCTYPE html>
<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #000; /* Full black background */
      color: #fff;
      text-align: center;
      padding-top: 40px;
      overflow: hidden;
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
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1; /* Put canvas behind text */
    }
  </style>
</head>
<body>
  <h1>📊 Hi Sagar, Good Morning 📊</h1>
  <p>💹 "In trading, losses are lessons and profits are rewards." 💹</p>
  <p>💡 Get up, let’s start the day with lots of new things 💡</p>
  <p>🙏 Remember, God is with you always 🙏</p>

  <!-- Full-page Candlestick Wallpaper -->
  <canvas id="chart"></canvas>

  <script>
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    function drawCandles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      let candleWidth = 8;
      let gap = 6;
      let x = 20;

      while (x < canvas.width) {
        let open = canvas.height/2 + Math.random() * 100 - 50;
        let close = canvas.height/2 + Math.random() * 100 - 50;
        let high = Math.max(open, close) + Math.random() * 30;
        let low = Math.min(open, close) - Math.random() * 30;

        // Wick
        ctx.strokeStyle = "#aaa";
        ctx.beginPath();
        ctx.moveTo(x + candleWidth/2, low);
        ctx.lineTo(x + candleWidth/2, high);
        ctx.stroke();

        // Candle body
        ctx.fillStyle = close > open ? "#00ff00" : "#ff3333";
        ctx.fillRect(x, Math.min(open, close), candleWidth, Math.abs(close - open));

        x += candleWidth + gap;
      }
    }

    setInterval(drawCandles, 800);
    window.onresize = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };
  </script>
</body>
</html>
