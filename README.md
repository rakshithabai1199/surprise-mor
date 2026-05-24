<!HELLOOOOO>
<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #000; /* Full black background */
      color: #fff;
    }
    #chart {
      display: block;
      width: 100%;
      height: 78vh; /* Candlesticks take most of the page */
      background: #000;
    }
    .message-box {
      width: 100%;
      text-align: center;
      background: #111; /* Panel for text */
      padding: 25px 20px; /* Neat spacing */
      border-top: 2px solid #00ffcc;
      margin-top: 5px; /* Only a little gap */
    }
    h1 {
      font-size: 2em;
      color: #00ffcc;
      text-shadow: 2px 2px 10px #00ffaa;
      margin: 0;
    }
    p {
      font-size: 1.2em;
      margin: 8px 0;
    }
  </style>
</head>
<body>
  <!-- Candlestick Chart at the top -->
  <canvas id="chart"></canvas>

  <!-- Text Messages at the bottom, centered neatly -->
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
    canvas.height = window.innerHeight * 0.78; // Chart takes ~78% of page

    function drawCandles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      let candleWidth = 8;
      let gap = 5;
      let x = 0;

      while (x < canvas.width) {
        let open = canvas.height/2 + Math.random() * 150 - 75;
        let close = canvas.height/2 + Math.random() * 150 - 75;
        let high = Math.max(open, close) + Math.random() * 30;
        let low = Math.min(open, close) - Math.random() * 30;

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
      canvas.height = window.innerHeight * 0.78;
    };
  </script>
</body>
</html>
