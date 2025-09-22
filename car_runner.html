<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>3D Endless Car Runner</title>
<style>
  body {
    margin: 0;
    overflow: hidden;
    font-family: Arial, sans-serif;
    background: linear-gradient(#87ceeb, #e0f7ff); /* sky */
  }

  #game {
    position: relative;
    width: 100vw;
    height: 100vh;
    perspective: 900px;
    overflow: hidden;
  }

  /* Grass ground */
  .grass {
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    background: #3cb043;
    z-index: -2;
  }

  .road {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%) rotateX(60deg);
    width: 400px; /* extended road */
    height: 100%;
    background: #222;
    overflow: hidden;
    z-index: -1;
  }

  /* Road stripes */
  .stripe {
    position: absolute;
    width: 20px;
    height: 60px;
    background: white;
    left: 190px; /* centered on new road */
    opacity: 0.8;
    border-radius: 4px;
  }

  /* Lamborghini player car */
  .car {
    position: absolute;
    bottom: 120px;
    left: calc(50% - 50px);
    width: 100px;
    height: 150px;
    background: linear-gradient(to top, #ff0000, #aa0000);
    border-radius: 15px 15px 5px 5px;
    box-shadow: 0 0 15px rgba(0,0,0,0.6);
    transition: left 0.2s;
    z-index: 2;
  }
  .car::before {
    content:"";
    position: absolute;
    top: 10px;
    left: 15px;
    width: 70px;
    height: 40px;
    background: black;
    border-radius: 5px;
  }
  .car::after {
    content:"";
    position: absolute;
    bottom: -15px;
    left: 20px;
    width: 60px;
    height: 15px;
    background: #444;
    border-radius: 5px;
  }

  /* Traffic obstacle cars */
  .trafficCar {
    position: absolute;
    width: 100px;
    height: 150px;
    border-radius: 12px;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
    z-index: 1;
  }

  /* Trees */
  .tree {
    position: absolute;
    width: 40px;
    height: 100px;
    z-index: 1;
  }
  .trunk {
    width: 10px;
    height: 40px;
    background: #5a381e;
    margin: auto;
  }
  .leaves {
    width: 40px;
    height: 60px;
    background: green;
    border-radius: 50%;
  }

  #scoreBoard {
    position: absolute;
    top: 10px;
    left: 10px;
    font-size: 20px;
    color: black;
    font-weight: bold;
  }

  #gameOver {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%,-50%);
    font-size: 28px;
    display: none;
    text-align: center;
    color: black;
    z-index: 3;
  }

  #restartBtn {
    margin-top: 15px;
    padding: 10px 20px;
    font-size: 18px;
    border: none;
    background: #ff3b3b;
    color: white;
    border-radius: 6px;
    cursor: pointer;
  }

  /* Mobile controls */
  #controls {
    position: absolute;
    bottom: 20px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    padding: 0 40px;
    z-index: 3;
  }
  .ctrlBtn {
    width: 80px;
    height: 80px;
    background: rgba(0,0,0,0.5);
    color: white;
    font-size: 28px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    user-select: none;
    cursor: pointer;
  }
</style>
</head>
<body>
<div id="game">
  <div class="grass"></div>
  <div class="road" id="road"></div>
  <div class="car" id="car"></div>
  <div id="scoreBoard">Score: 0</div>
  <div id="gameOver">
    <p>Game Over</p>
    <button id="restartBtn">Restart</button>
  </div>
  <!-- Mobile controls -->
  <div id="controls">
    <div class="ctrlBtn" id="leftBtn">⟵</div>
    <div class="ctrlBtn" id="rightBtn">⟶</div>
  </div>
</div>

<!-- Sounds -->
<audio id="engineSound" src="https://actions.google.com/sounds/v1/transportation/car_engine.ogg" loop></audio>
<audio id="crashSound" src="https://actions.google.com/sounds/v1/cartoon/cartoon_boing.ogg"></audio>
<audio id="scoreSound" src="https://actions.google.com/sounds/v1/cartoon/wood_plank_flicks.ogg"></audio>

<script>
const game = document.getElementById('game');
const road = document.getElementById('road');
const car = document.getElementById('car');
const scoreBoard = document.getElementById('scoreBoard');
const gameOverScreen = document.getElementById('gameOver');
const restartBtn = document.getElementById('restartBtn');
const leftBtn = document.getElementById('leftBtn');
const rightBtn = document.getElementById('rightBtn');

const engineSound = document.getElementById('engineSound');
const crashSound = document.getElementById('crashSound');
const scoreSound = document.getElementById('scoreSound');

let lanes = [game.offsetWidth/2 - 200, game.offsetWidth/2 - 80, game.offsetWidth/2 + 40];
let currentLane = 1;
let traffic = [];
let trees = [];
let stripes = [];
let score = 0;
let running = true;

// Move car function
function moveCar(dir) {
  if(!running) return;
  if(dir === 'left' && currentLane > 0){
    currentLane--;
    car.style.left = lanes[currentLane] + 'px';
  }
  if(dir === 'right' && currentLane < 2){
    currentLane++;
    car.style.left = lanes[currentLane] + 'px';
  }
}

// Keyboard controls
document.addEventListener('keydown', (e) => {
  if(e.key === 'ArrowLeft') moveCar('left');
  if(e.key === 'ArrowRight') moveCar('right');
});

// Mobile controls
leftBtn.addEventListener('touchstart', () => moveCar('left'));
rightBtn.addEventListener('touchstart', () => moveCar('right'));

// Spawn traffic cars
function spawnTraffic(){
  if(!running) return;
  const lane = Math.floor(Math.random() * 3);
  const tCar = document.createElement('div');
  tCar.classList.add('trafficCar');
  tCar.style.left = lanes[lane] + 'px';
  tCar.style.top = '-160px';

  const colors = ["blue","yellow","purple","green","black"];
  tCar.style.background = colors[Math.floor(Math.random()*colors.length)];

  game.appendChild(tCar);
  traffic.push(tCar);
}

// Spawn trees
function spawnTree(){
  if(!running) return;
  const treeLeft = createTree();
  treeLeft.style.left = (lanes[0] - 100) + 'px';
  treeLeft.style.top = '-120px';
  game.appendChild(treeLeft);
  trees.push(treeLeft);

  const treeRight = createTree();
  treeRight.style.left = (lanes[2] + 160) + 'px';
  treeRight.style.top = '-120px';
  game.appendChild(treeRight);
  trees.push(treeRight);
}

function createTree(){
  const tree = document.createElement('div');
  tree.classList.add('tree');
  tree.innerHTML = '<div class="leaves"></div><div class="trunk"></div>';
  return tree;
}

// Spawn road stripes
function spawnStripe(){
  if(!running) return;
  const stripe = document.createElement('div');
  stripe.classList.add('stripe');
  stripe.style.top = '-80px';
  road.appendChild(stripe);
  stripes.push(stripe);
}

// Game loop
function update(){
  if(!running) return;

  // Traffic cars
  traffic.forEach((tCar, idx) => {
    let top = parseInt(tCar.style.top);
    tCar.style.top = (top + 7) + 'px';

    const carRect = car.getBoundingClientRect();
    const tRect = tCar.getBoundingClientRect();
    if(carRect.left < tRect.right &&
       carRect.right > tRect.left &&
       carRect.top < tRect.bottom &&
       carRect.bottom > tRect.top){
      gameOver();
    }

    if(top > window.innerHeight){
      tCar.remove();
      traffic.splice(idx,1);
      score += 10;
      scoreBoard.textContent = "Score: " + score;
      scoreSound.play();
    }
  });

  // Trees
  trees.forEach((tree, idx) => {
    let top = parseInt(tree.style.top);
    tree.style.top = (top + 6) + 'px';
    if(top > window.innerHeight){
      tree.remove();
      trees.splice(idx,1);
    }
  });

  // Stripes
  stripes.forEach((stripe, idx) => {
    let top = parseInt(stripe.style.top);
    stripe.style.top = (top + 10) + 'px';
    if(top > window.innerHeight){
      stripe.remove();
      stripes.splice(idx,1);
    }
  });

  requestAnimationFrame(update);
}

function gameOver(){
  running = false;
  engineSound.pause();
  crashSound.play();
  gameOverScreen.style.display = 'block';
}

function restart(){
  traffic.forEach(t => t.remove());
  traffic = [];
  trees.forEach(tree => tree.remove());
  trees = [];
  stripes.forEach(stripe => stripe.remove());
  stripes = [];
  score = 0;
  scoreBoard.textContent = "Score: 0";
  currentLane = 1;
  car.style.left = lanes[currentLane] + 'px';
  running = true;
  gameOverScreen.style.display = 'none';
  engineSound.play();
  update();
}

restartBtn.addEventListener('click', restart);

// Start game
engineSound.play();
update();
setInterval(spawnTraffic, 1500);
setInterval(spawnTree, 800);
setInterval(spawnStripe, 200);
</script>
</body>
</html>
