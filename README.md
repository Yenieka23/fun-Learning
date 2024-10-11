# fun-Learning
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fun Learning for Kids</title>
    <style>
        body {
            font-family: 'Comic Sans MS', sans-serif;
            background-color: #ffefd5;
            color: #333;
            margin: 0;
            padding: 0;
            text-align: center;
        }
        header {
            background-color: #ff6f61;
            padding: 20px;
        }
        header h1 {
            font-size: 3em;
            color: #ffffff;
            text-shadow: 2px 2px #ffa07a;
        }
        nav {
            background-color: #ffcc66;
            padding: 15px;
        }
        nav a {
            color: white;
            text-decoration: none;
            font-size: 1.4em;
            margin: 0 15px;
            background-color: #ff9966;
            padding: 10px 20px;
            border-radius: 25px;
            box-shadow: 2px 2px #f4a460;
        }
        nav a:hover {
            background-color: #ffcc66;
            text-decoration: underline;
        }
        .content {
            padding: 30px;
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }
        .category {
            background-color: #ffebcd;
            border: 2px solid #ddd;
            border-radius: 15px;
            padding: 20px;
            width: 300px;
            margin: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        footer {
            background-color: #ff9966;
            padding: 15px;
            margin-top: 20px;
            font-size: 1.2em;
            color: white;
        }
    </style>
</head>
<body>

<header>
    <h1>Fun Learning for Kids</h1>
</header>

<nav>
    <a href="#math">Math Games</a>
    <a href="#science">Science Fun</a>
    <a href="#reading">Story Time</a>
</nav>

<div class="content">
    <div class="category" id="math">
        <h2>Math Games</h2>
        <p>Sharpen your brain with colorful and exciting math games!</p>
        <button onclick="startMathGame()">Start Playing</button>
        <h3>Featured Games:</h3>
        <ul>
            <li><a href="#" onclick="startMathGame()">Addition Adventure</a></li>
        </ul>
    </div>

    <div class="category" id="science">
        <h2>Science Fun</h2>
        <p>Explore cool experiments and discover the world of science!</p>
        <button onclick="startScienceExperiment()">Discover More</button>
        <h3>Featured Experiments:</h3>
        <ul>
            <li><a href="#" onclick="startScienceExperiment()">Volcano Eruption</a></li>
        </ul>
    </div>

    <div class="category" id="reading">
        <h2>Story Time</h2>
        <p>Jump into magical stories that spark your imagination.</p>
        <button onclick="startReadingGame()">Read Now</button>
        <h3>Featured Stories:</h3>
        <ul>
            <li><a href="#" onclick="startReadingGame()">Complete the Story</a></li>
        </ul>
    </div>
</div>

<footer>
    <p>&copy; 2024 Fun Learning for Kids. Have a Fun-tastic Day!</p>
</footer>

<!-- Math Game: Addition Adventure -->
<div id="mathGame" style="display:none;">
    <h1>Addition Adventure</h1>
    <p id="mathQuestion"></p>
    <input type="number" id="mathAnswer" placeholder="Your answer" />
    <button onclick="checkMathAnswer()">Submit</button>
    <p class="result" id="mathResult"></p>
    <button onclick="generateMathQuestion()">Next Question</button>
</div>

<!-- Science Game: Volcano Eruption -->
<div id="scienceExperiment" style="display:none;">
    <h1>Volcano Eruption!</h1>
    <div id="volcano" style="width: 200px; height: 100px; background-color: brown; margin: 0 auto; position: relative;">
        <div id="lava" style="width: 50%; height: 0; background-color: red; position: absolute; bottom: 100%; left: 25%; transition: height 1s;"></div>
    </div>
    <button onclick="erupt()">Erupt!</button>
</div>

<!-- Reading Game: Story Completion -->
<div id="readingGame" style="display:none;">
    <h1>Complete the Story</h1>
    <p id="story"></p>
    <input type="text" id="userInput" placeholder="Finish the story!" />
    <button onclick="checkStoryCompletion()">Submit</button>
    <p id="storyFeedback"></p>
</div>

<script>
    // Math Game Functions
    let correctMathAnswer;

    function generateMathQuestion() {
        const num1 = Math.floor(Math.random() * 10);
        const num2 = Math.floor(Math.random() * 10);
        correctMathAnswer = num1 + num2;
        document.getElementById('mathQuestion').innerText = `What is ${num1} + ${num2}?`;
        document.getElementById('mathAnswer').value = '';
        document.getElementById('mathResult').innerText = '';
    }

    function checkMathAnswer() {
        const userAnswer = parseInt(document.getElementById('mathAnswer').value);
        if (userAnswer === correctMathAnswer) {
            document.getElementById('mathResult').innerText = 'Correct! 🎉';
        } else {
            document.getElementById('mathResult').innerText = `Wrong! The correct answer is ${correctMathAnswer}.`;
        }
    }

    function startMathGame() {
        document.querySelector('.content').style.display = 'none';
        document.getElementById('mathGame').style.display = 'block';
        generateMathQuestion();
    }

    // Science Experiment Functions
    function erupt() {
        const lava = document.getElementById('lava');
        lava.style.height = '50px'; // Erupting lava
        setTimeout(() => {
            lava.style.height = '0'; // Reset lava
        }, 2000); // Reset after 2 seconds
    }

    function startScienceExperiment() {
        document.querySelector('.content').style.display = 'none';
        document.getElementById('scienceExperiment').style.display = 'block';
    }

    // Reading Game Functions
    const storyStart = "Once upon a time in a magical forest, there lived a ";
    const correctStoryEnd = "witch";

    function startReadingGame() {
        document.querySelector('.content').style.display = 'none';
        document.getElementById('readingGame').style.display = 'block';
        document.getElementById('story').innerText = storyStart;
    }

    function checkStoryCompletion() {
        const userAnswer = document.getElementById('userInput').value.trim();
        if (userAnswer.toLowerCase() === correctStoryEnd.toLowerCase()) {
            document.getElementById('storyFeedback').innerText = "Great job! 🎉 You completed the story!";
        } else {
            document.getElementById('storyFeedback').innerText = "Not quite! Try again!";
        }
    }
</script>

</body>
</html>
