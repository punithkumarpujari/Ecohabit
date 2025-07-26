<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>EcoHabit - by Punith Kumar</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #e8f5e9;
      color: #2e7d32;
      text-align: center;
      padding: 20px;
      overflow-x: hidden;
    }

    h1 {
      font-size: 2.5em;
      margin-bottom: 10px;
      animation: fadeIn 1s ease-out;
    }

    .subtitle {
      font-size: 1em;
      color: #4caf50;
      margin-bottom: 20px;
      animation: slideIn 1s ease-in-out;
    }

    .habit {
      font-size: 18px;
      margin: 12px 0;
      opacity: 0;
      animation: fadeUp 0.8s ease forwards;
    }

    .habit:nth-child(3) { animation-delay: 0.2s; }
    .habit:nth-child(4) { animation-delay: 0.4s; }
    .habit:nth-child(5) { animation-delay: 0.6s; }
    .habit:nth-child(6) { animation-delay: 0.8s; }
    .habit:nth-child(7) { animation-delay: 1s; }

    input[type="checkbox"] {
      transform: scale(1.3);
      margin-right: 10px;
    }

    .tip {
      background: #c8e6c9;
      padding: 12px;
      margin: 25px auto;
      border-radius: 10px;
      max-width: 400px;
      font-style: italic;
      animation: fadeIn 1s ease-in;
    }

    .streak {
      font-weight: bold;
      font-size: 1.2em;
      margin-top: 20px;
      animation: fadeIn 1.5s ease;
    }

    .footer {
      font-size: 13px;
      margin-top: 40px;
      color: #1b5e20;
      animation: slideIn 2s ease-in;
    }

    @keyframes fadeIn {
      from { opacity: 0 }
      to { opacity: 1 }
    }

    @keyframes slideIn {
      from { transform: translateY(-20px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    @keyframes fadeUp {
      0% { transform: translateY(20px); opacity: 0 }
      100% { transform: translateY(0); opacity: 1 }
    }
  </style>
</head>
<body>

  <h1>EcoHabit 🌱</h1>
  <div class="subtitle">Make everyday a green step</div>

  <div class="habit"><input type="checkbox" class="habit-check"> Turn off unused lights</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Avoid plastic bags</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Use reusable water bottles</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Walk or cycle instead of drive</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Don’t waste water</div>

  <div class="tip" id="eco-tip">Loading eco tip...</div>

  <div class="streak">Current Streak: <span id="streak">0</span> days</div>

  <div class="footer">Developed with 🌍 by <strong>Punith Kumar</strong></div>

  <script>
    const tips = [
      "Bring your own cloth bag when shopping.",
      "Skip plastic straws — use steel or bamboo.",
      "Switch to LED bulbs to save energy.",
      "Plant one tree every month.",
      "Turn off taps while brushing your teeth.",
      "Repurpose jars and containers.",
      "Walk for short distances instead of driving."
    ];

    const tipElement = document.getElementById("eco-tip");
    tipElement.innerText = tips[Math.floor(Math.random() * tips.length)];

    const checks = document.querySelectorAll(".habit-check");
    const streakElement = document.getElementById("streak");
    let streak = localStorage.getItem("eco-streak") || 0;
    streakElement.textContent = streak;

    checks.forEach(check => {
      check.addEventListener("change", () => {
        const allChecked = Array.from(checks).every(c => c.checked);
        if (allChecked) {
          streak++;
          localStorage.setItem("eco-streak", streak);
          streakElement.textContent = streak;
          alert("✅ Well done! Keep it up!");
        }
      });
    });
  </script>

</body>
</html>
