<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Math Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f8ff;
            color: #333;
        }
        #question {
            font-size: 24px;
            margin: 20px;
        }
        #result {
            font-size: 20px;
            margin-top: 20px;
        }
        input[type="number"] {
            padding: 10px;
            width: 100px;
            font-size: 18px;
            margin: 10px;
        }
        button {
            padding: 10px 15px;
            font-size: 18px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

    <h1>Math Challenge Game</h1>
    <div id="level">Level: 1</div>
    <div id="question"></div>
    <input type="number" id="answer" placeholder="Your answer" />
    <button onclick="checkAnswer()">Submit</button>
    <div id="result"></div>

    <script>
        let level = 1;
        let correctAnswer;

        function generateQuestion() {
            let num1, num2;
            if (level === 1) {
                num1 = Math.floor(Math.random() * 10);
                num2 = Math.floor(Math.random() * 10);
                correctAnswer = num1 + num2;
                document.getElementById('question').innerText = `What is ${num1} + ${num2}?`;
            } else if (level === 2) {
                num1 = Math.floor(Math.random() * 10) + 10; // higher numbers
                num2 = Math.floor(Math.random() * 10) + 10; // higher numbers
                correctAnswer = num1 * num2;
                document.getElementById('question').innerText = `What is ${num1} x ${num2}?`;
            }
        }

        function checkAnswer() {
            const userAnswer = parseInt(document.getElementById('answer').value);
            if (userAnswer === correctAnswer) {
                document.getElementById('result').innerText = "Correct! Moving to the next level.";
                level++;
                document.getElementById('level').innerText = "Level: " + level;
                document.getElementById('answer').value = '';
                if (level > 2) {
                    document.getElementById('question').innerText = "Congratulations! You've completed the game!";
                    document.getElementById('answer').style.display = 'none';
                    document.querySelector('button').style.display = 'none';
                } else {
                    generateQuestion();
                }
            } else {
                document.getElementById('result').innerText = "Wrong answer. Try again!";
            }
        }

        // Start the game
        generateQuestion();
    </script>
</body>
</html>
