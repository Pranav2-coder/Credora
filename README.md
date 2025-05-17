# Credora
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Stopwatch</title>
  <style>
    :root {
      --bg-color: #ffffff;
      --text-color: #000000;
      --btn-color: #dddddd;
    }

    body.dark {
      --bg-color: #1e1e1e;
      --text-color: #f5f5f5;
      --btn-color: #333333;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-color);
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      transition: all 0.3s ease-in-out;
    }

    .stopwatch {
      font-size: 3em;
      margin-bottom: 20px;
    }

    .controls button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 1em;
      cursor: pointer;
      background-color: var(--btn-color);
      border: none;
      border-radius: 8px;
    }

    .theme-toggle {
      position: absolute;
      top: 20px;
      right: 20px;
      padding: 8px 16px;
      background-color: var(--btn-color);
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <button class="theme-toggle" onclick="toggleTheme()">Toggle Theme</button>

  <div class="stopwatch" id="display">00:00:00</div>
  <div class="controls">
    <button onclick="start()">Start</button>
    <button onclick="stop()">Stop</button>
    <button onclick="reset()">Reset</button>
  </div>

  <script>
    let [hours, minutes, seconds] = [0, 0, 0];
    let display = document.getElementById("display");
    let interval = null;

    function updateDisplay() {
      let h = hours.toString().padStart(2, '0');
      let m = minutes.toString().padStart(2, '0');
      let s = seconds.toString().padStart(2, '0');
      display.textContent = `${h}:${m}:${s}`;
    }

    function stopwatch() {
      seconds++;
      if (seconds == 60) {
        seconds = 0;
        minutes++;
      }
      if (minutes == 60) {
        minutes = 0;
        hours++;
      }
      updateDisplay();
    }

    function start() {
      if (interval === null) {
        interval = setInterval(stopwatch, 1000);
      }
    }

    function stop() {
      clearInterval(interval);
      interval = null;
    }

    function reset() {
      [hours, minutes, seconds] = [0, 0, 0];
      stop();
      updateDisplay();
    }

    function toggleTheme() {
      document.body.classList.toggle("dark");
    }
  </script>
</body>
</html>