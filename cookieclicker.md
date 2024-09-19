---
layout: page
title: Cookie Clicker
permalink: /cookieclicker/
---

<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
   <style>
       body {
           display: flex;
           flex-direction: column;
           align-items: center;
           justify-content: center;
           background-color: #f0f4f8;
           font-family: 'Poppins', sans-serif;
           height: 100vh;
           margin: 0;
           padding: 0;
       }

       header {
           width: 100%;
           height: 80px;
           background-color: #2c3e50;
           display: flex;
           justify-content: center;
           align-items: center;
           position: fixed;
           top: 0;
           left: 0;
           z-index: 1000;
           box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
       }

       header h1 {
           font-size: 2rem;
           color: #ecf0f1;
           font-weight: 600;
           margin: 0;
       }

       body {
           padding-top: 100px;
       }

       h1 {
           font-size: 3rem;
           color: #34495e;
           margin-bottom: 20px;
       }

       #gameContainer {
           text-align: center;
           margin-top: 50px;
       }

       #cookie {
           width: 180px;
           height: 180px;
           cursor: pointer;
           transition: transform 0.2s ease-in-out;
       }

       #cookie:hover {
           transform: scale(1.05);
       }

       #cookie:active {
           transform: scale(0.95);
       }

       #score {
           margin-top: 20px;
           font-size: 28px;
           color: #34495e;
           font-weight: 600;
       }

       #upgrades {
           margin-top: 30px;
           display: flex;
           flex-wrap: wrap;
           justify-content: center;
           gap: 15px;
       }

       .upgrade {
           background-color: #3498db;
           padding: 10px 20px;
           border: none;
           border-radius: 12px;
           cursor: pointer;
           color: #ecf0f1;
           font-size: 16px;
           font-weight: 600;
           transition: background-color 0.3s ease;
           box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
       }

       .upgrade:hover {
           background-color: #2980b9;
       }

       #youWin {
           font-size: 36px;
           color: #e74c3c;
           margin-top: 50px;
           display: none;
           font-weight: 600;
       }

       #playAgain {
           background-color: #2ecc71;
           color: white;
           padding: 12px 24px;
           border: none;
           border-radius: 12px;
           font-size: 18px;
           cursor: pointer;
           display: none;
           margin-top: 20px;
           font-weight: 600;
           transition: background-color 0.3s ease;
           box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
       }

       #playAgain:hover {
           background-color: #27ae60;
       }
   </style>
</head>
<body>

   <header>
       <h1>Cookie Clicker</h1>
   </header>

   <div id="gameContainer">
       <!-- Add your cookie image URL here -->
       <img id="cookie" src="https://prettysimplesweet.com/wp-content/uploads/2020/07/Big-Chocolate-Chip-Cookies-150x150.jpg" alt="Cookie">
       <div id="score">Cookies: 0</div>

       <div id="upgrades">
           <button class="upgrade" onclick="buyUpgrade(10, 1)">+1 Cookie per Click (Cost: 10)</button>
           <button class="upgrade" onclick="buyUpgrade(100, 10)">+10 Cookies per Click (Cost: 100)</button>
           <button class="upgrade" onclick="buyUpgrade(500, 25)">+25 Cookies per Click (Cost: 500)</button>
           <button class="upgrade" onclick="buyUpgrade(1000, 50)">+50 Cookies per Click (Cost: 1000)</button>
           <button class="upgrade" onclick="buyUpgrade(5000, 100)">+100 Cookies per Click (Cost: 5000)</button>
           <button class="upgrade" onclick="buyAutoClicker(500)">Auto Clicker (Cost: 500)</button>
           <button class="upgrade" onclick="buyGoldenCookie(3000)">Golden Cookie (Cost: 3000)</button>
       </div>

       <div id="youWin">You Win! Cookies are raining down!</div>
       <button id="playAgain" onclick="resetGame()">Play Again</button>
   </div>

   <script>
       let cookies = 0;
       let cookiesPerClick = 1;
       let autoClicker = null;

       const scoreElement = document.getElementById("score");
       const cookieElement = document.getElementById("cookie");
       const youWinElement = document.getElementById("youWin");
       const playAgainButton = document.getElementById("playAgain");

       cookieElement.addEventListener("click", function () {
           cookies += cookiesPerClick;
           updateScore();
           checkWinCondition();
       });

       function buyUpgrade(cost, increment) {
           if (cookies >= cost) {
               cookies -= cost;
               cookiesPerClick += increment;
               updateScore();
           }
       }

       function buyAutoClicker(cost) {
           if (cookies >= cost && !autoClicker) {
               cookies -= cost;
               updateScore();
               autoClicker = setInterval(() => {
                   cookies += cookiesPerClick;
                   updateScore();
                   checkWinCondition();
               }, 1000);
           }
       }

       function buyGoldenCookie(cost) {
           if (cookies >= cost) {
               cookies -= cost;
               cookiesPerClick *= 2;
               updateScore();
           }
       }

       function updateScore() {
           scoreElement.textContent = `Cookies: ${cookies}`;
       }

       function checkWinCondition() {
           if (cookies >= 10000) {
               clearInterval(autoClicker);
               cookieElement.style.display = "none";
               youWinElement.style.display = "block";
               playAgainButton.style.display = "block";
               document.body.style.backgroundImage = 'url("https://prettysimplesweet.com/wp-content/uploads/2020/07/Big-Chocolate-Chip-Cookies-150x150.jpg")';
               document.body.style.backgroundRepeat = "repeat";
           }
       }

       function resetGame() {
           cookies = 0;
           cookiesPerClick = 1;
           updateScore();
           youWinElement.style.display = "none";
           playAgainButton.style.display = "none";
           cookieElement.style.display = "block";
           document.body.style.backgroundImage = "none";
           clearInterval(autoClicker);
           autoClicker = null;
       }
   </script>

</body>
</html>
