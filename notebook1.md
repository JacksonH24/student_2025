---
layout: page
title: notebook 1
permalink: notebook1
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Boxing Joke Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        #joke {
            font-size: 1.5em;
            margin: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 1.2em;
            cursor: pointer;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

    <h1>Random Boxing Joke Generator</h1>
    <div id="joke">Click the button to get a boxing joke!</div>
    <button onclick="generateJoke()">Get a Joke</button>

    <script>
        const jokes = [
            "Why did the boxer go to the bank? To get his punch line!",
            "I tried boxing, but I couldn’t hit the punchline.",
            "What do you call a boxer who’s also a stand-up comedian? A punch-liner!",
            "Why do boxers make great comedians? Because they always deliver a punch!",
            "I thought about becoming a boxer, but I didn’t want to get knocked out of my career.",
            "Why did the boxer bring a ladder to the fight? He wanted to go to the next level!"
        ];

        function generateJoke() {
            const randomIndex = Math.floor(Math.random() * jokes.length);
            document.getElementById('joke').innerText = jokes[randomIndex];
        }
    </script>

</body>
</html>
