# birdjjc
bird bring seed for babies
<!DOCTYPE html>
<html lang="sadfasdf">
<head>
  <meta charset="UTF-8">
  <title>Bird Feeding Animation</title>
  <style>
    body {
      background: skyblue;
      overflow: hidden;
      margin: 0;
    }
    canvas {
      display: block;
      margin: auto;
      background: #aee6ff;
    }
  </style>
</head>
<body>
<canvas id="scene" width="600" height="400"></canvas>

<script>
const canvas = document.getElementById("scene");
const ctx = canvas.getContext("2d");

let birdX = -50, birdY = 100;
let seedX, seedY;
let dropping = false;
let babiesOpen = false;

function drawNest() {
  ctx.fillStyle = "saddlebrown";
  ctx.beginPath();
  ctx.ellipse(300, 320, 80, 30, 0, 0, Math.PI * 2);
  ctx.fill();

  // Baby birds
  ctx.fillStyle = babiesOpen ? "yellow" : "orange";
  ctx.beginPath();
  ctx.arc(280, 300, 15, 0, Math.PI * 2); // left baby
  ctx.arc(300, 300, 15, 0, Math.PI * 2); // middle baby
  ctx.arc(320, 300, 15, 0, Math.PI * 2); // right baby
  ctx.fill();
}

function drawBird() {
  ctx.fillStyle = "blue";
  ctx.beginPath();
  ctx.arc(birdX, birdY, 20, 0, Math.PI * 2); // body
  ctx.fill();

  // Wing
  ctx.fillStyle = "lightblue";
  ctx.beginPath();
  ctx.arc(birdX - 10, birdY, 15, 0, Math.PI * 2);
  ctx.fill();

  // Eye
  ctx.fillStyle = "white";
  ctx.beginPath();
  ctx.arc(birdX + 5, birdY - 5, 5, 0, Math.PI * 2);
  ctx.fill();

  // Beak
  ctx.fillStyle = "orange";
  ctx.beginPath();
  ctx.moveTo(birdX + 20, birdY);
  ctx.lineTo(birdX + 35, birdY - 5);
  ctx.lineTo(birdX + 20, birdY + 5);
  ctx.fill();

  // Seed in beak
  if (!dropping) {
    ctx.fillStyle = "brown";
    ctx.beginPath();
    ctx.arc(birdX + 28, birdY, 5, 0, Math.PI * 2);
    ctx.fill();
  }
}

function drawSeed() {
  if (dropping) {
    ctx.fillStyle = "brown";
    ctx.beginPath();
    ctx.arc(seedX, seedY, 5, 0, Math.PI * 2);
    ctx.fill();
  }
}

function update() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  drawNest();

  // Bird movement
  if (birdX < 280) {
    birdX += 2;
  } else if (!dropping) {
    dropping = true;
    seedX = birdX + 28;
    seedY = birdY;
  }

  // Seed dropping
  if (dropping && seedY < 300) {
    seedY += 3;
  } else if (dropping && seed
