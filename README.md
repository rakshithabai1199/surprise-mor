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
    /* Green line with arrow animation */
    .loading-line {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 0;
      height: 0;
      border-left: 4px solid #00ff00;
      transform-origin: bottom left;
      animation: rise 2s forwards;
    }
    .loading-line::after {
      content: '';
      position: absolute;
      top: 0;
      left: -6px;
      border-left: 10px solid transparent;
      border-right: 10px solid transparent;
      border-bottom: 15px solid #00ff00; /* Arrowhead */
    }
    @keyframes rise {
      to { height: 100%; }
    }
    /* Hide content until animation ends */
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
  <!-- Green loading line with arrow -->
  <div class="loading-line"></div>

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
    // Show content after line animation
    setTimeout(() => {
      document.querySelector('.content').classList.add('show');
      document.querySelector('.loading-line').style.display = 'none';
    }, 2000);

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
