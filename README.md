<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #000; /* Full black background */
      color: #fff;
      display: flex;
      flex-direction: column;
      height: 100vh; /* Use full screen height */
    }
    .top-message {
      text-align: center;
      background: #111;
      padding: 15px;
      border-bottom: 2px solid #00ffcc;
    }
    .top-message h1 {
      font-size: 1.8em;
      color: #00ffcc;
      text-shadow: 2px 2px 8px #00ffaa;
      margin: 0;
    }
    #chart {
      flex: 1; /* Chart fills middle space */
      width: 100%;
      background: #000;
    }
    .bottom-message {
      text-align: center;
      background: #111;
      padding: 20px;
      border-top: 2px solid #00ffcc;
    }
    .bottom-message p {
      font-size: 1.1em;
      margin: 6px 0;
    }
  </style>
</head>
<body>
  <!-- Top Greeting -->
  <div class="top-message">
    <h1>📊 Hi Sagar, Good Morning 📊</h1>
  </div>

  <!-- Candlestick Chart in the middle -->
  <canvas id="chart"></canvas>

  <!-- Bottom Motivational Messages -->
  <div class="bottom-message">
    <p>💹 "Trade with patience, profits will come." 💹</p>
    <p>💡 Get up, let’s start the day with lots of new things 💡</p>
    <p>🙏 Remember, God is with you always 🙏</p>
  </div>

  <script>
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = document.body.clientHeight 
                      - document.querySelector('.top-message').offsetHeight 
                      - document.querySelector('.bottom-message').offsetHeight;
    }

    resizeCanvas();
    window.onresize = resizeCanvas;

    function drawCandles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      let candleWidth = 8;
      let gap = 4;
      let x = 0;

      while (x < canvas.width) {
        let open = canvas.height/2 + Math.random() * 120 - 60;
        let close = canvas.height/2 + Math.random() * 120 - 60;
        let high = Math.max(open, close) + Math.random() * 25;
        let low = Math.min(open, close) - Math.random() * 25;

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
  </script>
</body>
</html>
