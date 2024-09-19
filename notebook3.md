---
layout: page
title: notebook 3
permalink: notebook3
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notebook 2 - Random Image and Fact</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f5f5f5;
        }
        button {
            background-color: #00bcd4;
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 18px;
            border-radius: 50px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
        }
        button:hover {
            background-color: #4dd0e1;
            transform: scale(1.05);
        }
        #random-content {
            margin-top: 30px;
            font-size: 24px;
            color: #007BFF;
        }
        #random-image {
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <h1>Welcome to Notebook 2's Random Image and Fact Page</h1>
    <p>Click the button to generate a random image and fact.</p>

    <button onclick="generateRandomContent()">Generate Random Image and Fact</button>

    <div id="random-content"></div>
    <img id="random-image" src="" alt="Random Image" style="display: none; width: 300px; height: 200px; border-radius: 10px; margin-top: 20px;"/>

    <script>
        // Array of random facts
        const randomFacts = [
            "Honey never spoils. Archaeologists have found pots of honey in ancient Egyptian tombs that are over 3000 years old and still perfectly edible.",
            "Bananas are berries, but strawberries are not.",
            "The Eiffel Tower can grow more than 6 inches during the summer due to the expansion of iron in the heat.",
            "Wombat poop is cube-shaped to help it stay in place on sloped surfaces.",
            "Octopuses have three hearts, but they stop beating while the octopus swims.",
            "There are more trees on Earth than stars in the Milky Way galaxy."
        ];

        // Array of random images
        const randomImages = [
            "https://picsum.photos/300/200?random=1",
            "https://picsum.photos/300/200?random=2",
            "https://picsum.photos/300/200?random=3",
            "https://picsum.photos/300/200?random=4",
            "https://picsum.photos/300/200?random=5"
        ];

        // Function to generate random content
        function generateRandomContent() {
            // Choose a random fact
            const randomFact = randomFacts[Math.floor(Math.random() * randomFacts.length)];
            // Choose a random image
            const randomImage = randomImages[Math.floor(Math.random() * randomImages.length)];

            // Display the random fact and image in the respective elements
            document.getElementById('random-content').innerHTML = `<p><strong>Random Fact:</strong> "${randomFact}"</p>`;
            document.getElementById('random-image').src = randomImage;
            document.getElementById('random-image').style.display = 'block';
        }
    </script>

</body>
</html>
