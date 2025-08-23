<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Oats Cup Recipe — Image + Presentation + Video Player</title>
  <style>
    :root {
      --bg: #0b1220;
      --panel: #121a2b;
      --panel-2: #0f1728;
      --text: #e6ebff;
      --muted: #9db0ff;
      --accent: #7aa2ff;
      --ring: #335dff55;
      --border: #233055;
    }
    * { box-sizing: border-box; }
    html, body { height: 100%; }
    body {
      margin: 0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, "Noto Sans", "Apple Color Emoji", "Segoe UI Emoji";
      background: linear-gradient(180deg, var(--bg), #0a1020 40%, #0a0e1a);
      color: var(--text);
      line-height: 1.6;
    }
    .container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 24px;
    }
    header {
      position: sticky;
      top: 0;
      z-index: 10;
      background: linear-gradient(180deg, rgba(11,18,32,.95), rgba(11,18,32,.75));
      backdrop-filter: blur(8px);
      border-bottom: 1px solid var(--border);
    }
    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 14px 0;
    }
    .logo {
      width: 36px;
      height: 36px;
      border-radius: 10px;
      background: radial-gradient(circle at 30% 30%, #a6b8ff, #6f8eff);
      box-shadow: 0 10px 30px #335dff44, inset 0 2px 8px #fff2;
    }
    h1 { font-size: clamp(1.25rem, 2.5vw + 1rem, 2rem); margin: 0; }
    .muted { color: var(--muted); font-size: 0.95rem; }

    .grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 18px;
    }
    @media (min-width: 900px) {
      .grid { grid-template-columns: 1.1fr 0.9fr; }
    }

    .card {
      background: linear-gradient(180deg, var(--panel), var(--panel-2));
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 18px;
      box-shadow: 0 10px 30px #0006, inset 0 1px 0 #ffffff0d;
    }
    .card h2 { margin-top: 4px; font-size: 1.15rem; }

    .hero {
      display: grid;
      grid-template-columns: 1fr;
      gap: 16px;
      align-items: center;
    }
    @media (min-width: 900px) {
      .hero { grid-template-columns: 0.9fr 1.1fr; }
    }

    .img-wrap {
      position: relative;
      border-radius: 16px;
      overflow: hidden;
      background: #0a1122;
      border: 1px solid var(--border);
      min-height: 220px;
    }
    .img-wrap img { width: 100%; height: 100%; object-fit: cover; display: block; }

    .controls {
      display: flex; flex-wrap: wrap; gap: 10px; align-items: center;
    }
    .btn, .file {
      appearance: none;
      border: 1px solid var(--border);
      background: #0d1630;
      color: var(--text);
      padding: 10px 14px;
      border-radius: 12px;
      cursor: pointer;
      font-size: 0.95rem;
      transition: transform .04s ease, box-shadow .2s ease, border-color .2s ease;
      box-shadow: 0 6px 20px #0005, inset 0 1px 0 #ffffff1a;
    }
    .btn:hover, .file:hover { border-color: #3f62ff; box-shadow: 0 10px 30px #335dff33; }
    .btn:active { transform: translateY(1px); }

    .list { margin: 0; padding-left: 18px; }
    .list li { margin: 6px 0; }

    .video {
      width: 100%; border-radius: 16px; border: 1px solid var(--border); background: #000; display: block;
    }

    .note { font-size: 0.92rem; color: var(--muted); }

    .footer {
      text-align: center; opacity: 0.8; font-size: 0.9rem; padding: 24px 0 60px;
    }

    .top { position: fixed; right: 16px; bottom: 16px; }
  </style>
</head>
<body>
  <header>
    <div class="container brand">
      <div class="logo" aria-hidden="true"></div>
      <div>
        <h1>Oats Cup Recipe — Simple, Fast & Healthy</h1>
        <div class="muted">Add your own photo & play your own video from your device.</div>
      </div>
    </div>
  </header>

  <main class="container">
    <section class="card hero">
      <div class="img-wrap" id="imageBox">
        <img id="previewImg" alt="Your recipe photo" src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='1200' height='800'%3E%3Crect width='100%25' height='100%25' fill='%23111a3a'/%3E%3Ctext x='50%25' y='50%25' text-anchor='middle' fill='%239db0ff' font-size='28' font-family='sans-serif' dy='.3em'%3EUpload your recipe photo%3C/text%3E%3C/svg%3E" />
      </div>
      <div>
        <h2>Upload Your Photo</h2>
        <p class="muted">Choose an image from your device to display it on the page.</p>
        <div class="controls">
          <input class="file" type="file" id="imageInput" accept="image/*" />
          <button class="btn" id="clearImage">Clear Photo</button>
        </div>
        <p class="note">Tip: Use a bright, well-lit photo for the best look.</p>
      </div>
    </section>

    <section class="grid">
      <article class="card">
        <h2>Recipe Presentation (English)</h2>
        <p>
          This presentation explains how to make a quick <strong>Oats Cup</strong> — a warm, energizing cup you can prepare in minutes. Perfect for breakfast or a healthy snack.
        </p>
        <h3>Ingredients</h3>
        <ul class="list">
          <li>1/2 cup rolled oats</li>
          <li>1 cup milk (or water/plant-based milk)</li>
          <li>1–2 teaspoons honey or sugar (optional)</li>
          <li>A pinch of salt</li>
          <li>Extras: chopped banana, nuts, raisins, cinnamon (optional)</li>
        </ul>
        <h3>Steps</h3>
        <ol class="list">
          <li>In a small pot or microwave-safe mug, add oats and milk.</li>
          <li>Add a pinch of salt. Stir well.</li>
          <li>Cook on the stovetop for 3–5 minutes (low heat), or microwave for 2–3 minutes. Stir halfway.</li>
          <li>Sweeten with honey or sugar to taste.</li>
          <li>Top with banana, nuts, raisins, and a sprinkle of cinnamon. Serve hot.</li>
        </ol>
        <h3>Notes</h3>
        <ul class="list">
          <li>Thicker cup: add more oats or cook a bit longer.</li>
          <li>Creamier texture: use milk and stir continuously.</li>
          <li>For protein: add a spoon of peanut butter or yogurt after cooking.</li>
        </ul>
      </article>

      <aside class="card">
        <h2>Your Video Player</h2>
        <video class="video" id="player" controls preload="metadata"></video>
        <div class="controls" style="margin-top:10px">
          <input class="file" type="file" id="videoInput" accept="video/*" />
          <button class="btn" id="clearVideo">Clear Video</button>
        </div>
        <p class="note">Select a video file from your device (mp4, webm, etc.). Your file does not upload anywhere — it plays locally in your browser.</p>
      </aside>
    </section>

    <section class="card">
      <h2>Extra Tips for a Better Web Page</h2>
      <ul class="list">
        <li>Scroll is already enabled — add more content freely.</li>
        <li>Replace the text with your own English presentation anytime.</li>
        <li>This page works offline once saved. Just open the HTML file in a browser.</li>
      </ul>
    </section>

    <div class="footer">© 2025 Your Recipe Site • Built as a single-page website</div>
  </main>

  <div class="top">
    <button class="btn" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">Back to top ↑</button>
  </div>

  <script>
    const imgInput = document.getElementById('imageInput');
    const previewImg = document.getElementById('previewImg');
    const clearImgBtn = document.getElementById('clearImage');
    const defaultImg = previewImg.src;

    imgInput.addEventListener('change', () => {
      const file = imgInput.files?.[0];
      if (!file) return;
      const url = URL.createObjectURL(file);
      previewImg.src = url;
    });

    clearImgBtn.addEventListener('click', () => {
      previewImg.src = defaultImg;
      imgInput.value = '';
    });

    const videoInput = document.getElementById('videoInput');
    const player = document.getElementById('player');
    const clearVideoBtn = document.getElementById('clearVideo');
    let currentVideoURL = '';

    videoInput.addEventListener('change', () => {
      const file = videoInput.files?.[0];
      if (!file) return;
      if (currentVideoURL) URL.revokeObjectURL(currentVideoURL);
      currentVideoURL = URL.createObjectURL(file);
      player.src = currentVideoURL;
      player.play().catch(() => {/* autoplay might be blocked */});
    });

    clearVideoBtn.addEventListener('click', () => {
      if (currentVideoURL) URL.revokeObjectURL(currentVideoURL);
      currentVideoURL = '';
      player.removeAttribute('src');
      player.load();
      videoInput.value = '';
    });
  </script>
</body>
</html>
