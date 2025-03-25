# Playnow
A game
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shooting Game</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <canvas id="gameCanvas"></canvas>
  <script src="script.js"></script>
</body>
</html>
body {
  margin: 0;
  overflow: hidden;
}

canvas {
  display: block;
  background-color: #f5f5f5;
  margin: 0 auto;
}
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const player = {
  x: canvas.width / 2,
  y: canvas.height - 50,
  width: 50,
  height: 50,
  speed: 7
};

const bullets = [];
const targets = [];

let score = 0;

// Event listeners for player movement and shooting
document.addEventListener("keydown", (e) => {
  if (e.key === "ArrowLeft") {
    player.x -= player.speed;
  } else if (e.key === "ArrowRight") {
    player.x += player.speed;
  } else if (e.key === " ") {
    shootBullet();
  }
});

function shootBullet() {
  bullets.push({
    x: player.x + player.width / 2,
    y: player.y,
    width: 5,
    height: 10,
    speed: 5
  });
}

function createTarget() {
  const x = Math.random() * canvas.width;
  const y = Math.random() * (canvas.height / 2); // Targets appear in the upper half of the screen
  const size = 30 + Math.random() * 30;

  targets.push({
    x,
    y,
    size,
    speed: 1 + Math.random() * 3
  });
}

function update() {
  // Clear the canvas
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // Draw player
  ctx.fillStyle = "blue";
  ctx.fillRect(player.x, player.y, player.width, player.height);

  // Draw bullets
  for (let i = 0; i < bullets.length; i++) {
    const bullet = bullets[i];
    bullet.y -= bullet.speed;

    // Remove bullets when they go out of screen
    if (bullet.y < 0) {
      bullets.splice(i, 1);
      i--;
      continue;
    }

    ctx.fillStyle = "red";
    ctx.fillRect(bullet.x - bullet.width / 2, bullet.y, bullet.width, bullet.height);

    // Check for collisions with targets
    for (let j = 0; j < targets.length; j++) {
      const target = targets[j];

      if (bullet.x >
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shooting Game</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <canvas id="gameCanvas"></canvas>
  <div id="gameOver" class="game-message">Game Over!</div>
  <div id="gameWin" class="game-message">You Win!</div>
  <div id="timer">Time Left: <span id="timeLeft">60</span> seconds</div>
  <script src="script.js"></script>
</body>
</html>
body {
  margin: 0;
  overflow: hidden;
  font-family: Arial, sans-serif;
  color: #fff;
}

canvas {
  display: block;
  background-color: #f5f5f5;
  margin: 0 auto;
}

#gameOver, #gameWin, #timer {
  position: absolute;
  top: 10px;
  left: 10px;
  font-size: 20px;
  background-color: rgba(0, 0, 0, 0.7);
  padding: 10px;
  border-radius: 5px;
}

.game-message {
  display: none;
}

#timer {
  top: 50px;
}
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const player = {
  x: canvas.width / 2,
  y: canvas.height - 50,
  width: 50,
  height: 50,
  speed: 7
};

const bullets = [];
const targets = [];
let score = 0;
let timeLeft = 60;
let gameInterval;
let timerInterval;
let level = 1;
let gameOver = false;

const levelSettings = {
  1: { targetSpeed: 2, targetSize: 30, numTargets: 5, timeLimit: 60 },
  2: { targetSpeed: 3, targetSize: 40, numTargets: 7, timeLimit: 45 },
  3: { targetSpeed: 4, targetSize: 50, numTargets: 10, timeLimit: 30 }
};

function resetGame() {
  player.x = canvas.width / 2;
  player.y = canvas.height - 50;
  bullets.length = 0;
  targets.length = 0;
  score = 0;
  timeLeft = levelSettings[level].timeLimit;
  gameOver = false;
  document.getElementById('gameOver').style.display = 'none';
  document.getElementById('gameWin').style.display = 'none';
  document.getElementById('timer').style.display = 'block';
  startGame();
}

function startGame() {
  // Start the game loop
 const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const player = {
  x: canvas.width / 2,
  y: canvas.height - 50,
  width: 50,
  height: 50,
  speed: 7
};

const bullets = [];
const targets = [];
let score = 0;
let timeLeft = 60;
let gameInterval;
let timerInterval;
let level = 1;
let gameOver = false;

const levelSettings = {
  1: { targetSpeed: 2, targetSize: 30, numTargets: 5, timeLimit: 60 },
  2: { targetSpeed: 3, targetSize: 40, numTargets: 7, timeLimit: 45 },
  3: { targetSpeed: 4, targetSize: 50, numTargets: 10, timeLimit: 30 }
};

function resetGame() {
  player.x = canvas.width / 2;
  player.y = canvas.height - 50;
  bullets.length = 0;
  targets.length = 0;
  score = 0;
  timeLeft = levelSettings[level].timeLimit;
  gameOver = false;
  document.getElementById('gameOver').style.display = 'none';
  document.getElementById('gameWin').style.display = 'none';
  document.getElementById('timer').style.display = 'block';
  startGame();
}

function startGame() {
  // Start the game loop
 

