#Helloo
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
      text-shadow: 2px 2px 12px #00ffaa;
      position: relative;
      z-index: 1;
    }
    p {
      font-size: 1.3em;
      margin: 12px 0;
      position: relative;
      z-index: 1;
    }
    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6); /* Dark overlay so text is visible */
      z-index: 0;
    }
    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: -1; /* Candlestick wallpaper behind everything */
    }
  </style>
</head>
<body>
  <h1>📊 Hi Sagar, Good Morning 📊</h1>
  <p>💹 "Trade with patience, profits will come." 💹</p>
  <p>💡 Get up, let’s start the day with lots of new things 💡</p>
  <p>🙏 Remember, God is with you always 🙏</p>

  <!-- Overlay to keep text readable -->
  <div class="overlay"></div>

  <!-- Full-page Candlestick Wallpaper -->
  <canvas id="chart"></canvas>

  <script>
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    function drawCandles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      let candleWidth = 6;
      let gap = 4;
      let x = 0;

      while (x < canvas.width) {
        let open = canvas.height/2 + Math.random() * 200 - 100;
        let close = canvas.height/2 + Math.random() * 200 - 100;
        let high = Math.max(open, close) + Math.random() * 40;
        let low = Math.min(open, close) - Math.random() * 40;

        // Wick
        ctx.strokeStyle = "#666";
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

    setInterval(drawCandles, 1000);

    window.onresize = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };
  </script>
</body>
</html>
