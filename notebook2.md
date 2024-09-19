---
layout: page
title: notebook 2
permalink: notebook2
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notebook 2 - Random Page</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f0f8ff;
        }
        button {
            background-color: #ffcc00;
            color: black;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 50px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
        }
        button:hover {
            background-color: #ffee58;
            transform: scale(1.05);
        }
        #random-content {
            margin-top: 30px;
            font-size: 24px;
            color: #007BFF;
        }
    </style>
</head>
<body>

    <h1>Welcome to Notebook 2's Random Page</h1>
    <p>Click the button below to generate random content.</p>

    <button onclick="generateRandomContent()">Generate Random Content</button>

    <div id="random-content"></div>

    <script>
        // Array of random quotes
        const randomQuotes = [
            "The only limit to our realization of tomorrow is our doubts of today.",
            "Success is not final, failure is not fatal: It is the courage to continue that counts.",
            "Don’t watch the clock; do what it does. Keep going.",
            "You miss 100% of the shots you don’t take.",
            "The best way to predict the future is to create it.",
            "Act as if what you do makes a difference. It does."
        ];

        // Array of random numbers
        const randomNumbers = Array.from({ length: 10 }, () => Math.floor(Math.random() * 100));

        // Function to generate random content
        function generateRandomContent() {
            // Choose a random quote and a random number
            const randomQuote = randomQuotes[Math.floor(Math.random() * randomQuotes.length)];
            const randomNumber = randomNumbers[Math.floor(Math.random() * randomNumbers.length)];

            // Display the random content in the div
            document.getElementById('random-content').innerHTML = `
                <p><strong>Random Quote:</strong> "${randomQuote}"</p>
                <p><strong>Random Number:</strong> ${randomNumber}</p>
            `;
        }
    </script>

</body>
</html>
