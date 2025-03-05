<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Пранк сайт</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 50px;
      margin: 0;
      overflow: hidden;
    }

    .jump-button {
      font-size: 20px;
      padding: 20px;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      position: relative;
      transition: 0.2s;
    }

    .celebration {
      font-size: 50px;
      font-weight: bold;
      color: transparent;
      background-image: linear-gradient(45deg, red, yellow, blue, green, purple);
      background-clip: text;
      animation: colorShift 3s infinite;
      margin-top: 50px;
      display: none;
    }

    @keyframes colorShift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .fireworks {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }

    .firework {
      position: absolute;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      animation: fireworkAnimation 1s ease-out forwards;
    }

    @keyframes fireworkAnimation {
      0% {
        transform: scale(0);
        opacity: 1;
      }
      50% {
        transform: scale(2);
        opacity: 0.5;
      }
      100% {
        transform: scale(0);
        opacity: 0;
      }
    }

    .haha {
      font-size: 60px;
      font-weight: bold;
      color: #ff0000;
      margin-top: 20px;
      display: none;
      animation: hahaAnimation 2s ease-in-out forwards;
    }

    @keyframes hahaAnimation {
      0% { opacity: 0; }
      100% { opacity: 1; }
    }

  </style>
</head>
<body>

  <h1>Попробуй кликнуть на кнопку!</h1>

  <button class="jump-button" id="jumpButton">Нажми меня!</button>

  <div class="celebration" id="celebration">Ты победил!</div>
  <div class="haha" id="haha">ХАХАХА!</div>

  <div class="fireworks" id="fireworks"></div>

  <script>
    const button = document.getElementById('jumpButton');
    const celebrationText = document.getElementById('celebration');
    const hahaText = document.getElementById('haha');
    const fireworksContainer = document.getElementById('fireworks');
    let jumpCounter = 0; // Счётчик прыжков кнопки

    button.addEventListener('mouseenter', () => {
      // Случайное положение кнопки на экране
      const maxX = window.innerWidth - button.offsetWidth;
      const maxY = window.innerHeight - button.offsetHeight;

      const randomX = Math.random() * maxX;
      const randomY = Math.random() * maxY;

      button.style.position = 'absolute';
      button.style.left = `${randomX}px`;
      button.style.top = `${randomY}px`;

      jumpCounter++;

      // Когда кнопка улетела 50 раз, показываем "ХАХАХА"
      if (jumpCounter === 50) {
        hahaText.style.display = 'block';
      }
    });

    button.addEventListener('click', () => {
      // Показать сообщение и запустить салют
      celebrationText.style.display = 'block';
      launchFireworks();
    });

    // Функция для запуска салюта
    function launchFireworks() {
      for (let i = 0; i < 10; i++) {
        const firework = document.createElement('div');
        firework.classList.add('firework');
        firework.style.left = `${Math.random() * window.innerWidth}px`;
        firework.style.top = `${Math.random() * window.innerHeight}px`;
        firework.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 50%)`;

        fireworksContainer.appendChild(firework);
      }
    }
  </script>

</body>
</html>
