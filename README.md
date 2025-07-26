<!DOCTYPE html>
<html>
<head>
  <title>EcoHabit Tracker</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e6f5ec;
      color: #333;
      padding: 20px;
      max-width: 600px;
      margin: auto;
    }
    h1 {
      color: #2e7d32;
      text-align: center;
    }
    .habit {
      display: flex;
      align-items: center;
      margin: 10px 0;
      background: #fff;
      padding: 10px;
      border-radius: 10px;
    }
    .habit input {
      margin-right: 15px;
      transform: scale(1.5);
    }
    #streak {
      font-weight: bold;
      text-align: center;
      margin: 20px 0;
    }
    #eco-tip {
      background: #d0f0c0;
      padding: 10px;
      border-radius: 10px;
      margin-top: 20px;
    }
    button {
      background-color: #4caf50;
      color: white;
      padding: 10px;
      width: 100%;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>🌱 EcoHabit Tracker</h1>
  <div id="streak">Streak: 0 days 🔥</div>

  <div class="habit"><input type="checkbox" class="habit-check"> Turn off unused lights</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Use reusable bag</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Avoid plastic bottles</div>
  <div class="habit"><input type="checkbox" class="habit-check"> Walk or bike instead of drive</div>
  <div class="habit"><input type="checkbox" class="habit-check"> No meat today</div>

  <button onclick="saveProgress()">✅ Save Today's Progress</button>

  <div id="eco-tip">Tip: Small changes = Big impact! 💚</div>

  <script>
    let streak = parseInt(localStorage.getItem('streak') || '0');
    let lastDate = localStorage.getItem('lastDate');

    const today = new Date().toLocaleDateString();

    if (lastDate !== today) {
      document.querySelectorAll('.habit-check').forEach(c => c.checked = false);
    } else {
      document.querySelectorAll('.habit-check').forEach((c, i) => {
        const saved = localStorage.getItem('habit_' + i);
        if (saved === 'true') c.checked = true;
      });
    }

    document.getElementById('streak').textContent = `Streak: ${streak} days 🔥`;

    function saveProgress() {
      const checks = document.querySelectorAll('.habit-check');
      let allDone = true;

      checks.forEach((c, i) => {
        localStorage.setItem('habit_' + i, c.checked);
        if (!c.checked) allDone = false;
      });

      if (lastDate !== today && allDone) {
        streak++;
        localStorage.setItem('streak', streak);
        localStorage.setItem('lastDate', today);
        alert('Great job! 🌎 You completed all tasks today!');
      } else if (!allDone) {
        alert('Try to complete all eco tasks before saving 🌿');
      } else {
        alert('Already saved today ✅');
      }

      document.getElementById('streak').textContent = `Streak: ${streak} days 🔥`;
    }
  </script>
</body>
</html>
