
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Happy Birthday Adiba 🎉</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      color: #fff;
      background: linear-gradient(270deg, #ff9a9e, #fad0c4, #fbc2eb, #a6c1ee);
      background-size: 800% 800%;
      animation: bgMove 12s ease infinite;
    }
    @keyframes bgMove {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    .container {
      position: relative;
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 16px;
      text-align: center;
      padding: 16px;
    }
    h1 {
      font-size: clamp(28px, 5vw, 48px);
      background: rgba(0,0,0,0.25);
      padding: 12px 20px;
      border-radius: 14px;
      box-shadow: 0 10px 30px rgba(0,0,0,.25);
    }
    .btn {
      padding: 14px 26px;
      font-size: 18px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      color: #fff;
      transition: transform .1s ease;
      position: relative;
    }
    .btn:active { transform: scale(0.96); }
    #celebrateBtn { background: #2ecc71; }
    #dontBtn { background: #e74c3c; }

    /* floating balloons */
    .balloon {
      position: absolute;
      bottom: -120px;
      width: 40px;
      height: 55px;
      border-radius: 50% 50% 45% 45%;
      animation: floatUp linear infinite;
      opacity: .9;
    }
    .balloon::after {
      content: '';
      position: absolute;
      left: 50%;
      bottom: -18px;
      width: 2px;
      height: 18px;
      background: rgba(255,255,255,.7);
      transform: translateX(-50%);
    }
    @keyframes floatUp {
      from { transform: translateY(0); }
      to { transform: translateY(-120vh); }
    }

    /* celebration page */
    .celebratePage {
      position: fixed;
      inset: 0;
      display: none;
      align-items: center;
      justify-content: center;
      background: radial-gradient(circle at top, #ffd1dc, #ff758c);
      overflow: hidden;
    }
    .celebrateCard {
      text-align: center;
      background: rgba(0,0,0,.25);
      padding: 24px 28px;
      border-radius: 18px;
      box-shadow: 0 15px 40px rgba(0,0,0,.35);
      animation: pop .6s ease;
    }
    @keyframes pop { from { transform: scale(.7); opacity: 0; } to { transform: scale(1); opacity: 1; } }
    .confetti {
      position: absolute;
      top: -10px;
      width: 10px;
      height: 14px;
      animation: fall 3s linear infinite;
    }
    @keyframes fall { to { transform: translateY(110vh) rotate(360deg); } }
  </style>
</head>
<body>
  <!-- Background music (may require user interaction to start) -->
  <audio id="song" src="happy-birthday.mp3" loop autoplay></audio>

  <div class="container" id="home">
    <h1>Happy birthday to you ADIBA 🎂</h1>
    <button class="btn" id="celebrateBtn">Celebrate your Birthday</button>
    <button class="btn" id="dontBtn">Don't celebrate Your Birthday</button>
  </div>

  <div class="celebratePage" id="celebratePage">
    <div class="celebrateCard">
      <h1>HAPPY BIRTHDAY TO YOU ADIBA 🎉🎉</h1>
      <p>Have a wonderful day full of smiles 💖</p>
    </div>
    <div style="position:fixed; right:10px; bottom:10px; font-size:14px; opacity:0.8; background:rgba(0,0,0,0.3); padding:6px 10px; border-radius:8px;">CELEBRATED BY arnob.exe_</div>

  <script>
    const celebrateBtn = document.getElementById('celebrateBtn');
    const dontBtn = document.getElementById('dontBtn');
    const page = document.getElementById('celebratePage');
    const song = document.getElementById('song');

    // teleport green button instantly on click
    celebrateBtn.addEventListener('click', () => {
      const x = Math.random() * (window.innerWidth - celebrateBtn.offsetWidth);
      const y = Math.random() * (window.innerHeight - celebrateBtn.offsetHeight);
      celebrateBtn.style.position = 'absolute';
      celebrateBtn.style.left = x + 'px';
      celebrateBtn.style.top = y + 'px';
    });

    // red button opens celebration page with animation
    dontBtn.addEventListener('click', () => {
      page.style.display = 'flex';
      try { song.play(); } catch(e) {}
      launchConfetti();
    });

    // balloons
    const colors = ['#ff7675','#74b9ff','#55efc4','#ffeaa7','#fd79a8'];
    for (let i = 0; i < 18; i++) {
      const b = document.createElement('div');
      b.className = 'balloon';
      b.style.left = Math.random()*100 + 'vw';
      b.style.background = colors[i % colors.length];
      b.style.animationDuration = 6 + Math.random()*6 + 's';
      document.body.appendChild(b);
    }

    function launchConfetti() {
      for (let i = 0; i < 120; i++) {
        const c = document.createElement('div');
        c.className = 'confetti';
        c.style.left = Math.random()*100 + 'vw';
        c.style.background = colors[Math.floor(Math.random()*colors.length)];
        c.style.animationDuration = 2 + Math.random()*3 + 's';
        c.style.opacity = Math.random();
        document.body.appendChild(c);
        setTimeout(() => c.remove(), 5000);
      }
    }
  </script>
</body>
</html>
