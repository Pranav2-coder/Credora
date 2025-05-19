<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Animated Stopwatch with Theme Toggle</title>
  <style>
    :root {
      --bg-light: #f0f2f5;
      --bg-dark: #1e1e1e;
      --text-light: #333;
      --text-dark: #f0f0f0;
      --card-light: #fff;
      --card-dark: #2c2c2c;
      --shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    }

    body {
      font-family: 'Segoe UI', sans-serif;
      background: var(--bg-light);
      color: var(--text-light);
      transition: background 0.4s, color 0.4s;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    body.dark {
      background: var(--bg-dark);
      color: var(--text-dark);
    }

    .toggle-theme {
      position: absolute;
      top: 20px;
      right: 20px;
    }

    .switch {
      position: relative;
      display: inline-block;
      width: 60px;
      height: 34px;
    }

    .switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0; left: 0;
      right: 0; bottom: 0;
      background-color: #ccc;
      transition: .4s;
      border-radius: 34px;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 26px; width: 26px;
      left: 4px; bottom: 4px;
      background-color: white;
      transition: .4s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background-color: #2196F3;
    }

    input:checked + .slider:before {
      transform: translateX(26px);
    }

    h1 {
      font-size: 3rem;
      margin-bottom: 30px;
      animation: fadeInDown 0.6s ease-out;
    }

    #display {
      font-size: 2.8rem;
      margin-bottom: 20px;
      background: var(--card-light);
      padding: 20px 50px;
      border-radius: 20px;
      box-shadow: var(--shadow);
      transition: 0.4s;
      animation: pulse 1s infinite alternate;
    }

    body.dark #display {
      background: var(--card-dark);
    }

    .buttons button {
      font-size: 1.1rem;
      padding: 10px 20px;
      margin: 0 10px;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .start { background-color: #28a745; color: white; }
    .stop { background-color: #dc3545; color: white; }
    .reset { background-color: #ffc107; color: black; }

    .buttons button:hover {
      transform: scale(1.05);
    }

    /* Animations */
    @keyframes fadeInDown {
      from {
        transform: translateY(-20px);
        opacity: 0;
      }
      to {
        transform: translateY(0);
        opacity: 1;
      }
    }

    @keyframes pulse {
      from {
        box-shadow: 0 0 10px rgba(0,0,0,0.05);
      }
      to {
        box-shadow: 0 0 20px rgba(0,0,0,0.15);
      }
    }
  </style>
</head>
<body>

  <!-- Theme Toggle -->
  <div class="toggle-theme">
    <label class="switch">
      <input type="checkbox" id="themeToggle">
      <span class="slider"></span>
    </label>
  </div>

  <h1>Stopwatch</h1>
  <div id="display">00:00:00</div>
  <div class="buttons">
    <button class="start" onclick="start()">Start</button>
    <button class="stop" onclick="stop()">Stop</button>
    <button class="reset" onclick="reset()">Reset</button>
  </div>

  <script>
    let startTime, interval;
    let elapsed = 0;
    let running = false;

    function updateDisplay() {
      const time = Date.now() - startTime + elapsed;
      const milliseconds = Math.floor((time % 1000) / 10);
      const seconds = Math.floor((time / 1000) % 60);
      const minutes = Math.floor((time / (1000 * 60)) % 60);
      document.getElementById("display").textContent =
        `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}:${String(milliseconds).padStart(2, '0')}`;
    }

    function start() {
      if (!running) {
        running = true;
        startTime = Date.now();
        interval = setInterval(updateDisplay, 50);
      }
    }

    function stop() {
      if (running) {
        running = false;
        elapsed += Date.now() - startTime;
        clearInterval(interval);
      }
    }

    function reset() {
      running = false;
      clearInterval(interval);
      elapsed = 0;
      document.getElementById("display").textContent = "00:00:00";
    }

    // Theme Toggle
    const toggle = document.getElementById("themeToggle");
    toggle.addEventListener("change", () => {
      document.body.classList.toggle("dark", toggle.checked);
    });
  </script>

</body>
</html>
