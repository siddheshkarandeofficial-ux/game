let score = 0;
let timeLeft = 30;
let gameInterval;
let timerInterval;

const box = document.getElementById("box");
const scoreText = document.getElementById("score");
const timeText = document.getElementById("time");
const gameArea = document.getElementById("gameArea");

function randomPosition() {
    const maxX = gameArea.clientWidth - 40;
    const maxY = gameArea.clientHeight - 40;

    const x = Math.random() * maxX;
    const y = Math.random() * maxY;

    box.style.left = x + "px";
    box.style.top = y + "px";
    box.style.display = "block";
}

box.addEventListener("click", () => {
    score++;
    scoreText.innerText = score;
    randomPosition();
});

function startGame() {
    score = 0;
    timeLeft = 30;
    scoreText.innerText = score;
    timeText.innerText = timeLeft;

    randomPosition();

    gameInterval = setInterval(randomPosition, 800);

    timerInterval = setInterval(() => {
        timeLeft--;
        timeText.innerText = timeLeft;

        if (timeLeft === 0) {
            clearInterval(gameInterval);
            clearInterval(timerInterval);
            box.style.display = "none";
            alert("Game Over! Your score is " + score);
        }
    }, 1000);
}
