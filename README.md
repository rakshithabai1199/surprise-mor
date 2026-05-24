#helloooo
<!DOCTYPE html>
<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #000; /* Full black background */
      color: #fff;
      overflow: hidden;
    }
    #chart {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0; /* Candlesticks behind */
    }
    .message-box {
      position: relative;
      z-index: 1; /* Text above candles */
      text-align: center;
      margin-top: 60px;
      background: rgba(0,0,0,0.7); /* Semi-transparent panel */
      padding: 30px;
      border-radius: 10px;
      width: 70%;
      margin-left: auto;
      margin-right: auto;
    }
    h1 {
      font-size: 2.5em;
      color: #00ffcc;
      text-shadow: 2px 2px 12px #00ffaa;
    }
    p {
      font-size: 1.3em;
      margin: 12px 0;
    }
  </style>
</head>
<body>
  <!-- Candlestick Wallpaper -->
  <canvas id="chart"></canvas>

  <!-- Neat Text Panel AFTER candles -->
  <div class="message-box">
    <h1>📊 Hi Sagar, Good Morning 📊</h1>
    <p>💹 "Trade with patience, profits will come." 💹</p>
    <p>💡 Get up, let’s start the day with lots of new things 💡</p>
    <p>🙏 Remember, God is with you always 🙏</p>
  </div>

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
