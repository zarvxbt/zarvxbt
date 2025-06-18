<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Old Computer Text Animation</title>
  <style>
    body {
      background: #000;
      color: #0f0;
      font-family: 'Courier New', Courier, monospace;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      overflow: hidden;
    }
    .terminal {
      position: relative;
      padding: 20px;
      border: 2px solid #0f0;
      background: #000;
      animation: glitch 0.5s infinite alternate;
    }
    .text {
      font-size: 1.5em;
      white-space: pre-wrap;
      animation: type 4s steps(40, end) infinite;
    }
    .cursor {
      animation: blink 0.7s step-end infinite;
    }
    @keyframes type {
      0% { width: 0; }
      100% { width: 100%; }
    }
    @keyframes blink {
      50% { opacity: 0; }
    }
    @keyframes glitch {
      0% { transform: translate(0); }
      20% { transform: translate(-2px, 2px); }
      40% { transform: translate(2px, -2px); }
      60% { transform: translate(-2px, -2px); }
      80% { transform: translate(2px, 2px); }
      100% { transform: translate(0); }
    }
    /* Optional CRT effect */
    .terminal::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to bottom, transparent, #0005);
      pointer-events: none;
    }
  </style>
</head>
<body>
  <div class="terminal">
    <div class="text">Welcome to [YourUsername] GitHub<span class="cursor">_</span></div>
  </div>

  <script>
    // Optional: Add random glitch text
    function glitchText() {
      const textElement = document.querySelector('.text');
      setInterval(() => {
        const originalText = 'Welcome to [YourUsername] GitHub';
        let glitched = originalText.split('').map(char => {
          return Math.random() > 0.9 ? String.fromCharCode(33 + Math.floor(Math.random() * 94)) : char;
        }).join('');
        textElement.textContent = glitched + '_';
      }, 200);
    }
    glitchText();
  </script>
</body>
</html>
