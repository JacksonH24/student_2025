---
layout: page
title: Tetris
permalink: /tetris/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tetris Game</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #333;
            color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .tetris-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .game-grid {
            display: flex;
        }

        .grid {
            display: grid;
            grid-template-rows: repeat(20, 30px);
            grid-template-columns: repeat(10, 30px);
            gap: 1px;
            border: 2px solid #fff;
        }

        .grid div {
            width: 30px;
            height: 30px;
            background-color: black;
            border: 1px solid #333;
        }

        .mini-grid {
            display: grid;
            grid-template-rows: repeat(4, 30px);
            grid-template-columns: repeat(4, 30px);
            margin-left: 20px;
            border: 2px solid #fff;
        }

        .mini-grid div {
            width: 30px;
            height: 30px;
            background-color: black;
        }

        .info {
            text-align: center;
            margin-top: 10px;
        }

        h1 {
            margin-bottom: 20px;
        }

        .tetromino {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div class="tetris-container">
        <div class="game-grid">
            <div class="grid"></div>
            <div class="mini-grid"></div>
        </div>
        <div class="info">
            <h1>Tetris</h1>
            <h3>Score: <span id="score">0</span></h3>
            <h3>Lines Cleared: <span id="lines">0</span></h3>
            <button id="start-button">Start Game</button>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const grid = document.querySelector('.grid');
            const miniGrid = document.querySelector('.mini-grid');
            const scoreDisplay = document.getElementById('score');
            const linesDisplay = document.getElementById('lines');
            const startButton = document.getElementById('start-button');
            const width = 10;
            let timerId;
            let score = 0;
            let lines = 0;
            const colors = ['orange', 'red', 'purple', 'green', 'blue'];

            // Create grid
            for (let i = 0; i < 200; i++) {
                const div = document.createElement('div');
                grid.appendChild(div);
            }
            for (let i = 0; i < 10; i++) {
                const div = document.createElement('div');
                div.classList.add('taken');
                grid.appendChild(div);
            }

            // Mini grid for next tetromino
            for (let i = 0; i < 16; i++) {
                const div = document.createElement('div');
                miniGrid.appendChild(div);
            }

            // The Tetrominoes
            const lTetromino = [
                [1, width + 1, width * 2 + 1, 2],
                [width, width + 1, width + 2, width * 2 + 2],
                [1, width + 1, width * 2 + 1, width * 2],
                [width, width * 2, width * 2 + 1, width * 2 + 2]
            ];

            const zTetromino = [
                [0, width, width + 1, width * 2 + 1],
                [width + 1, width + 2, width * 2, width * 2 + 1],
                [0, width, width + 1, width * 2 + 1],
                [width + 1, width + 2, width * 2, width * 2 + 1]
            ];

            const tTetromino = [
                [1, width, width + 1, width + 2],
                [1, width + 1, width + 2, width * 2 + 1],
                [width, width + 1, width + 2, width * 2 + 1],
                [1, width, width + 1, width * 2 + 1]
            ];

            const oTetromino = [
                [0, 1, width, width + 1],
                [0, 1, width, width + 1],
                [0, 1, width, width + 1],
                [0, 1, width, width + 1]
            ];

            const iTetromino = [
                [1, width + 1, width * 2 + 1, width * 3 + 1],
                [width, width + 1, width + 2, width + 3],
                [1, width + 1, width * 2 + 1, width * 3 + 1],
                [width, width + 1, width + 2, width + 3]
            ];

            const tetrominoes = [lTetromino, zTetromino, tTetromino, oTetromino, iTetromino];
            let currentPosition = 4;
            let currentRotation = 0;
            let random = Math.floor(Math.random() * tetrominoes.length);
            let current = tetrominoes[random][currentRotation];

            // Draw the tetromino
            function draw() {
                current.forEach(index => {
                    grid.children[currentPosition + index].classList.add('tetromino');
                    grid.children[currentPosition + index].style.backgroundColor = colors[random];
                });
            }

            // Undraw the tetromino
            function undraw() {
                current.forEach(index => {
                    grid.children[currentPosition + index].classList.remove('tetromino');
                    grid.children[currentPosition + index].style.backgroundColor = '';
                });
            }

            // Move the tetromino down
            function moveDown() {
                undraw();
                currentPosition += width;
                draw();
                freeze();
            }

            // Freeze the tetromino in place when it hits the bottom
            function freeze() {
                if (current.some(index => grid.children[currentPosition + index + width].classList.contains('taken'))) {
                    current.forEach(index => grid.children[currentPosition + index].classList.add('taken'));
                    random = Math.floor(Math.random() * tetrominoes.length);
                    current = tetrominoes[random][currentRotation];
                    currentPosition = 4;
                    draw();
                    addScore();
                    gameOver();
                }
            }

            // Move the tetromino left, unless it's at the edge
            function moveLeft() {
                undraw();
                const isAtLeftEdge = current.some(index => (currentPosition + index) % width === 0);
                if (!isAtLeftEdge) currentPosition -= 1;
                if (current.some(index => grid.children[currentPosition + index].classList.contains('taken'))) {
                    currentPosition += 1;
                }
                draw();
            }

            // Move the tetromino right, unless it's at the edge
            function moveRight() {
                undraw();
                const isAtRightEdge = current.some(index => (currentPosition + index) % width === width - 1);
                if (!isAtRightEdge) currentPosition += 1;
                if (current.some(index => grid.children[currentPosition + index].classList.contains('taken'))) {
                    currentPosition -= 1;
                }
                draw();
            }

            // Rotate the tetromino
            function rotate() {
                undraw();
                currentRotation++;
                if (currentRotation === current.length) {
                    currentRotation = 0;
                }
                current = tetrominoes[random][currentRotation];
                draw();
            }

            // Assign controls to keys
            function control(e) {
                if (e.keyCode === 37) {
                    moveLeft();
                } else if (e.keyCode === 38) {
                    rotate();
                } else if (e.keyCode === 39) {
                    moveRight();
                } else if (e.keyCode === 40) {
                    moveDown();
                }
            }

            document.addEventListener('keydown', control);

            // Add score when lines are completed
            function addScore() {
                for (let i = 0; i < 199; i += width) {
                    const row = [i, i + 1, i + 2, i + 3, i + 4, i + 5, i + 6, i + 7, i + 8, i + 9];
                    if (row.every(index => grid.children[index].classList.contains('taken'))) {
                        score += 10;
                        lines += 1;
                        scoreDisplay.innerHTML = score;
                        linesDisplay.innerHTML = lines;
                        row.forEach(index => {
                            grid.children[index].classList.remove('taken');
                            grid.children[index].classList.remove('tetromino');
                            grid.children[index].style.backgroundColor = '';
                        });
                        const removedSquares = grid.querySelectorAll('.grid div');
                        const squares = Array.from(removedSquares);
                        const removedRow = squares.splice(i, width);
                        grid.prepend(...removedRow);
                    }
                }
            }

            // Game over
            function gameOver() {
                if (current.some(index => grid.children[currentPosition + index].classList.contains('taken'))) {
                    scoreDisplay.innerHTML = 'GAME OVER';
                    clearInterval(timerId);
                }
            }

            // Start/Pause the game
            startButton.addEventListener('click', () => {
                if (timerId) {
                    clearInterval(timerId);
                    timerId = null;
                } else {
                    draw();
                    timerId = setInterval(moveDown, 1000);
                }
            });
        });
    </script>
</body>
</html>
