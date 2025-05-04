# Clockapp-
# PROGRAM:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Enhanced Clock & Stopwatch</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Orbitron', sans-serif;
      background: linear-gradient(135deg, #2c5364, #203a43, #0f2027);
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background: rgba(255, 255, 255, 0.08);
      backdrop-filter: blur(12px);
      padding: 40px;
      border-radius: 20px;
      text-align: center;
      box-shadow: 0 8px 32px rgba(0,0,0,0.37);
      width: 90%;
      max-width: 500px;
    }
    h1 {
      font-size: 1.8rem;
      color: #00fff0;
      margin-bottom: 15px;
    }
    .time-display {
      font-size: 2.5rem;
      margin: 10px 0 30px;
      letter-spacing: 3px;
      background: rgba(0, 0, 0, 0.3);
      padding: 15px 20px;
      border-radius: 12px;
      box-shadow: inset 0 0 10px #00000040;
    }
    .buttons button {
      margin: 10px 10px;
      padding: 12px 25px;
      font-size: 1rem;
      background: linear-gradient(145deg, #00adb5, #007d84);
      border: none;
      border-radius: 10px;
      cursor: pointer;
      color: white;
      font-weight: bold;
      transition: 0.3s;
      box-shadow: 0 4px 10px rgba(0, 173, 181, 0.5);
    }
    .buttons button:hover {
      transform: translateY(-3px);
      background: #00ffe1;
      color: #000;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Digital Clock</h1>
    <div id="clock" class="time-display">00:00:00</div>

    <h1>Stopwatch</h1>
    <div id="stopwatch" class="time-display">00:00:00</div>

    <div class="buttons">
      <button id="start">Start</button>
      <button id="pause">Pause</button>
      <button id="reset">Reset</button>
    </div>
  </div>

  <script>
    // Digital Clock
    function updateClock() {
      const now = new Date();
      const time = now.toLocaleTimeString();
      document.getElementById('clock').textContent = time;
    }
    setInterval(updateClock, 1000);
    updateClock();

    // Stopwatch
    let stopwatchInterval = null;
    let [hours, minutes, seconds] = [0, 0, 0];
    let paused = false;

    function updateStopwatch() {
      seconds++;
      if (seconds === 60) {
        seconds = 0;
        minutes++;
      }
      if (minutes === 60) {
        minutes = 0;
        hours++;
      }

      document.getElementById("stopwatch").textContent =
        String(hours).padStart(2, "0") + ":" +
        String(minutes).padStart(2, "0") + ":" +
        String(seconds).padStart(2, "0");
    }

    document.getElementById("start").addEventListener("click", () => {
      if (!stopwatchInterval) {
        stopwatchInterval = setInterval(updateStopwatch, 1000);
        paused = false;
      }
    });

    document.getElementById("pause").addEventListener("click", () => {
      if (!paused) {
        clearInterval(stopwatchInterval);
        stopwatchInterval = null;
        paused = true;
      }
    });

    document.getElementById("reset").addEventListener("click", () => {
      clearInterval(stopwatchInterval);
      stopwatchInterval = null;
      [hours, minutes, seconds] = [0, 0, 0];
      document.getElementById("stopwatch").textContent = "00:00:00";
      paused = false;
    });
  </script>
</body>
</html>
```
# OUTPUT:

![image](https://github.com/user-attachments/assets/cd228389-c89c-4be0-97e9-cfa7c4b461af)
