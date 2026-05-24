<!HELLO TRADER>
<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #000;
      color: #fff;
      overflow: hidden;
    }
    /* Canvas for animated profit line */
    #profitLineCanvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 10;
      pointer-events: none; /* Don't block clicks */
    }
    .content {
      opacity: 0;
      transition: opacity 1s ease;
    }
    .content.show {
      opacity: 1;
    }
    #chart {
      display: block;
      width: 100%;
      height: 70vh;
      background: #000;
    }
    .top-message, .bottom-message {
      text-align: center;
      background: #111;
      padding: 15px;
      border-top: 2px solid #00ffcc;
      border-bottom: 2px solid #00ffcc;
    }
    .top-message h1 {
      font-size: 1.8em;
      color: #00ffcc;
      text-shadow: 2px 2px 8px #00ffaa;
      margin: 0;
    }
    .bottom-message p {
      font-size: 1.1em;
      margin: 6px 0;
    }
  </style>
</head>
<body>
  <!-- Canvas for profit line -->
  <canvas id="profitLineCanvas"></canvas>

  <!-- Hidden content until animation finishes -->
  <div class="content">
    <div class="top-message">
      <h1>📊 Hi Sagar, Good Morning 📊</h1>
    </div>

    <canvas id="chart"></canvas>

    <div class="bottom-message">
      <p>💹 "Trade with patience, profits will come." 💹</p>
      <p>💡 Get up, let’s start the day with lots of new things 💡</p>
      <p>🙏 Remember, God is with you always 🙏</p>
    </div>
  </div>

  <script>
    // Profit line animation
    const lineCanvas = document.getElementById('profitLineCanvas');
    const lineCtx = lineCanvas.getContext('2d');
    lineCanvas.width = window.innerWidth;
    lineCanvas.height = window.innerHeight;

    let progress = 0;
    function animateLine() {
      lineCtx.clearRect(0, 0, lineCanvas.width, lineCanvas.height);
      lineCtx.strokeStyle = "#00ff00";
      lineCtx.lineWidth = 4;
      lineCtx.beginPath();
      lineCtx.moveTo(0, lineCanvas.height); // bottom-left
      lineCtx.lineTo(progress, lineCanvas.height - progress); // diagonal up-right
      lineCtx.stroke();

      // Arrowhead attached to line end
      if (progress > 20) {
        lineCtx.fillStyle = "#00ff00";
        lineCtx.beginPath();
        lineCtx.moveTo(progress, lineCanvas.height - progress);
        lineCtx.lineTo(progress - 10, lineCanvas.height - progress - 20);
        lineCtx.lineTo(progress + 10, lineCanvas.height - progress - 20);
        lineCtx.closePath();
        lineCtx.fill();
      }

      progress += 15;
      if (progress < Math.min(lineCanvas.width, lineCanvas.height)) {
        requestAnimationFrame(animateLine);
      } else {
        // Show content after animation
        document.querySelector('.content').classList.add('show');
        lineCanvas.style.display = 'none';
      }
    }
    animateLine();

    // Candlestick chart
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight * 0.7;
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

        ctx.strokeStyle = "#666";
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
