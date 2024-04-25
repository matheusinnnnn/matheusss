<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Click Game</title>
<style>
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
  }
  #game-container {
    position: relative;
    width: 400px;
    height: 400px;
    border: 2px solid black;
  }
  .circle {
    position: absolute;
    border-radius: 50%;
    cursor: pointer;
  }
</style>
</head>
<body>
<div id="game-container"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {
  const gameContainer = document.getElementById("game-container");
  let score = 0;
  let totalClicks = 0;
  const maxClicks = 10;

  function createCircle() {
    const circle = document.createElement("div");
    circle.classList.add("circle");
    circle.style.width = "50px";
    circle.style.height = "50px";
    circle.style.backgroundColor = "red";
    circle.style.left = `${Math.random() * (gameContainer.clientWidth - 50)}px`;
    circle.style.top = `${Math.random() * (gameContainer.clientHeight - 50)}px`;
    circle.addEventListener("click", () => {
      score++;
      totalClicks++;
      if (totalClicks >= maxClicks) {
        alert(`Game over! Your score is ${score}.`);
        score = 0;
        totalClicks = 0;
      } else {
        updateScore();
        gameContainer.removeChild(circle);
        createCircle();
      }
    });
    gameContainer.appendChild(circle);
  }

  function updateScore() {
    document.getElementById("score").textContent = `Score: ${score}`;
  }

  createCircle();
  updateScore();
});
</script>
</body>
</html>
