# Hellooooooooo 
<!DOCTYPE html>
<html>
<head>
  <title>Trading Surprise</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #0f2027;
      background: linear-gradient(to right, #2c5364, #203a43, #0f2027);
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
    table {
      margin: 30px auto;
      border-collapse: collapse;
      width: 60%;
      background: #111;
    }
    th, td {
      border: 1px solid #444;
      padding: 10px;
      text-align: center;
    }
    th {
      background: #222;
      color: #00ffcc;
    }
    .profit { color: #00ff00; }
    .loss { color: #ff3333; }
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
  <p>💹 "Trade with discipline, profit will follow." 💹</p>
  <p>💡 Get up, let’s start the day with lots of new things 💡</p>
  <p>🙏 Remember, God is with you always 🙏</p>

  <!-- Profit/Loss Table -->
  <table>
    <tr>
      <th>Trade</th>
      <th>Status</th>
      <th>Result</th>
    </tr>
    <tr>
      <td>Stock AAPL</td>
      <td>Closed</td>
      <td class="profit">+ $250</td>
    </tr>
    <tr>
      <td>Crypto BTC</td>
      <td>Open</td>
      <td class="loss">- $120</td>
    </tr>
    <tr>
      <td>Stock TSLA</td>
      <td>Closed</td>
      <td class="profit">+ $400</td>
    </tr>
    <tr>
      <td>Forex EUR/USD</td>
      <td>Closed</td>
      <td class="loss">- $75</td>
    </tr>
  </table>

  <!-- Fake Trading Chart -->
  <canvas id="chart" width="600" height="200"></canvas>

  <script>
    const canvas = document.getElementById('chart');
    const ctx = canvas.getContext('2d');

    function drawLine() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.beginPath();
      ctx.moveTo(0, 100);
      for (let x = 0; x < canvas.width; x++) {
        let y = 100 + 40 * Math.sin(x * 0.05 + Date.now() * 0.002);
        ctx.lineTo(x, y);
      }
      ctx.strokeStyle = '#00ffcc';
      ctx.lineWidth = 2;
      ctx.stroke();
    }

    setInterval(drawLine, 50);
  </script>
</body>
</html>
