---
layout: base
title: Student Home 
description: Home Page
hide: true
---

# <span style="font-family: 'Georgia', serif; color: #ff6347;">Welcome to My Journey</span>


<!-- Navigation buttons section -->
<div style="display: flex; justify-content: center; gap: 30px; padding: 40px; background-color: #e0f7fa; border-radius: 20px; box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.2);">
  <div style="text-align: center;">
     <a href="notebook1" style="text-decoration: none;">
        <button style="background-color: #ff6f61; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
           Notebook 1
        </button>
     </a>
  </div>

  <div style="text-align: center;">
     <a href="notebook2" style="text-decoration: none;">
        <button style="background-color: #ffcc00; color: black; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
           Notebook 2
        </button>
     </a>
  </div>

  <div style="text-align: center;">
     <a href="notebook3" style="text-decoration: none;">
        <button style="background-color: #00bcd4; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
           Notebook 3
        </button>
     </a>
  </div>
</div>


<style>
  button:hover {
    background-color: #ff8a80;
    transform: scale(1.1);
  }

  button:active {
    transform: scale(0.95);
  }

  a:nth-child(2) button:hover {
    background-color: #ffee58;
  }

  a:nth-child(3) button:hover {
    background-color: #80deea;
  }
</style>

<!-- Introduction section -->
<div style="text-align: center; margin: 40px 0;">
    <h2 style="color: navy; font-family: 'Arial', sans-serif;">
        My journey starts here.
    </h2>
</div>

<!-- First interactive box -->
<div style="border: 2px solid #007BFF; border-radius: 8px; padding: 20px; margin: 20px auto; width: 60%; text-align: center; background-color: #f9f9f9;">
    <p style="color: #007BFF; font-size: 18px; font-family: 'Arial', sans-serif;">
        Mysterious... Click This
    </p>
    <button style="background-color: white; border: 2px solid #007BFF; color: #007BFF; padding: 10px 20px; font-size: 16px; border-radius: 5px; cursor: pointer; transition: background-color 0.3s ease, color 0.3s ease;">
        Button
    </button> 
</div>

<!-- Clippers section -->
<div style="border: 2px solid #007BFF; border-radius: 8px; padding: 20px; margin: 20px auto; width: 60%; text-align: center; background-color: #f9f9f9;">
    <p style="color: #007BFF; font-size: 18px; font-family: 'Arial', sans-serif;">
        LA Clippers Basketball
    </p>
    <a href="https://www.nba.com/clippers/" style="text-decoration: none;">
        <button style="background-color: white; border: 2px solid #007BFF; color: #007BFF; padding: 10px 20px; font-size: 16px; border-radius: 5px; cursor: pointer; transition: background-color 0.3s ease, color 0.3s ease;">
            Clippers News
        </button> 
    </a>
    <a href="https://www.nba.com/clippers/roster" style="text-decoration: none; margin-left: 10px;">
        <button style="background-color: white; border: 2px solid #007BFF; color: #007BFF; padding: 10px 20px; font-size: 16px; border-radius: 5px; cursor: pointer; transition: background-color 0.3s ease, color 0.3s ease;">
            Clippers Roster
        </button> 
    </a>
</div>

<!-- Mario Animation -->
<div style="text-align: center; margin: 40px 0;">
    <a href="shhh.html">
        <img src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/457fe2ae-23dd-4459-b703-2d1404bac6ad/dfzzdt1-21d8812f-c0c7-4df5-b36a-fee9d88a0a77.gif?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcLzQ1N2ZlMmFlLTIzZGQtNDQ1OS1iNzAzLTJkMTQwNGJhYzZhZFwvZGZ6emR0MS0yMWQ4ODEyZi1jMGM3LTRkZjUtYjM2YS1mZWU5ZDg4YTBhNzcuZ2lmIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.xVbRCIhFGArRr7XSn8oTQtf4FNI8iJQffpTphvg3shw" alt="Mario walking" style="border-radius: 8px; width: 300px; height: 120px;"/>
    </a>
</div>

<!-- Styling for animation and hover effects -->
<style>
 img {
   position: fixed;
   bottom: 0;
   left: 0;
   width: 150px;
   height: 60px;
   animation: walk 10s linear infinite;
 }

 button:hover {
   background-color: #007BFF;
   color: white;
 }

 @keyframes walk {
   from { transform: translateX(-100%); }
   to { transform: translateX(100vw); }
 }
</style>


<div style="text-align: center;">
     <a href="calculator" style="text-decoration: none;">
        <button style="background-color: #00bcd4; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
           Calculator
        </button>
     </a>
  </div>

  <div style="text-align: center;">
     <a href="snakegame" style="text-decoration: none;">
        <button style="background-color: #00bcd4; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
           Snake Game
        </button>
     </a>
  </div>

<div style="text-align: center;">
     <a href="cookieclicker" style="text-decoration: none;">
        <button style="background-color: #00bcd4; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
          Cookie Clicker
        </button>
     </a>
  </div>

  <div style="text-align: center;">
     <a href="emojis" style="text-decoration: none;">
        <button style="background-color: #00bcd4; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
          Emojis
        </button>
     </a>
  </div>

  <div style="text-align: center;">
     <a href="tetris" style="text-decoration: none;">
        <button style="background-color: #00bcd4; color: white; border: none; padding: 20px 50px; font-size: 18px; border-radius: 50px; cursor: pointer; transition: background-color 0.3s, transform 0.3s;">
          Tetris
        </button>
     </a>
  </div>

  