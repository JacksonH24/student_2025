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
   <link href="https://fonts.googleapis.com/css2?family=Cookie&display=swap" rel="stylesheet">
   <style>
       body {
           display: flex;
           flex-direction: column;
           align-items: center;
           justify-content: center;
           background-color: #e0f7fa; /* Light teal background */
           font-family: Arial, sans-serif;
           height: 100vh;
           margin: 0;
           padding: 0;
       }

       header {
           width: 100%;
           height: 100px;
           background-color: #00796b; /* Dark teal */
           color: white;
           font-size: 2rem;
           display: flex;
           align-items: center;
           justify-content: center;
           position: fixed;
           top: 0;
           left: 0;
           z-index: 1000;
           box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Add a subtle shadow */
       }

       body {
           padding-top: 120px; /* Space to avoid content overlapping header */
       }

       h1 {
           font-family: 'Cookie', cursive;
           color: #004d40; /* Dark green */
           font-size: 3.5rem;
           margin-bottom: 20px;
       }

       #gameContainer {
           display: flex;
           flex-direction: column;
           align-items: center;
           justify-content: center;
           text-align: center;
       }

       #cookie {
           width: 180px;
           height: 180px;
           cursor: pointer;
           transition: transform 0.1s ease;
           margin-top: 20px;
       }

       #cookie:active {
           transform: scale(0.9);
       }

       #score {
           margin-top: 20px;
           font-size: 28px;
           color: #004d40; /* Dark green */
           font-weight: bold;
       }

       #upgrades {
           display: flex;
           flex-wrap: wrap;
           justify-content: center;
           gap: 15px;
           margin-top: 30px;
       }

       .upgrade {
           background-color: #ffca28; /* Yellow */
           padding: 15px;
           border: none;
           border-radius: 10px;
           cursor: pointer;
           color: #fff;
           font-size: 16px;
           font-weight: bold;
           width: 220px;
           transition: background-color 0.2s ease;
       }

       .upgrade:hover {
           background-color: #ffa000; /* Darker yellow */
       }

       #youWin {
           font-size: 32px;
           color: #d32f2f; /* Red */
           margin-top: 40px;
           display: none;
       }

       #playAgain {
           background-color: #388e3c; /* Green */
           color: white;
           padding: 12px 25px;
           border: none;
           border-radius: 10px;
           font-size: 18px;
           cursor: pointer;
           display: none;
           margin-top: 20px;
           transition: background-color 0.2s ease;
       }

       #playAgain:hover {
           background-color: #2e7d32; /* Darker green */
       }
   </style>
</head>
<body>

   <header>
       Cookie Clicker Game
   </header>

   <h1>Cookie Clicker</h1>
   
   <div id="gameContainer">
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

   <audio id="clickSound" src='{{site.baseurl}}/images/Mouse Click Sound Effect.mp3'></audio>

   <script>
       let cookies = 0;
       let cookiesPerClick = 1;
       let autoClicker = null;

       const scoreElement = document.getElementById("score");
       const cookieElement = document.getElementById("cookie");
       const youWinElement = document.getElementById("youWin");
       const playAgainButton = document.getElementById("playAgain");
       const clickSound = document.getElementById("clickSound");

       cookieElement.addEventListener("click", function () {
           cookies += cookiesPerClick;
           updateScore();
           checkWinCondition();
           clickSound.play(); // Play the sound on click
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
