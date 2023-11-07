# -data-driven-UI-UX-challenges.


#1st Question------------------------------------------------------------------------------
import json

# Load the quiz data from a JSON file
with open('quiz_data.json', 'r') as file:
    quiz_data = json.load(file)

# Iterate through the quiz questions
for question in quiz_data:
    print("Question:", question["question"])
    print("Options:", ", ".join(question["options"]))
    print("Correct Answer:", question["answer"])
    print("\n")

    2nd question ------------------------------------------------------------------------

   # Create your HTML structure with placeholders for the question, answer options, and a button to submit the answer.
   <!DOCTYPE html>
<html>
<head>
    <title>Quiz App</title>
</head>
<body>
    <div id="question-container">
        <h1 id="question">Question Text</h1>
        <ul id="options">
            <li>Option 1</li>
            <li>Option 2</li>
            <li>Option 3</li>
            <li>Option 4</li>
        </ul>
    </div>
    <button id="next-button">Next</button>

    <script src="quiz.js"></script>
</body>
</html>

#Create a JavaScript file (quiz.js) to handle the dynamic rendering of questions:
// Sample quiz data (you can replace this with your JSON data)
const quizData = [
    {
        question: "What is the capital of France?",
        options: ["New York", "London", "Paris", "Dublin"],
        answer: "Paris"
    },
    {
        question: "Who painted the Mona Lisa?",
        options: ["Vincent Van Gogh", "Pablo Picasso", "Leonardo Da Vinci", "Claude Monet"],
        answer: "Leonardo Da Vinci"
    }
    // Add more questions as needed
];

const questionContainer = document.getElementById("question-container");
const questionElement = document.getElementById("question");
const optionsList = document.getElementById("options");
const nextButton = document.getElementById("next-button");

let currentQuestionIndex = 0;

function showQuestion(questionIndex) {
    const question = quizData[questionIndex];
    questionElement.textContent = question.question;

    optionsList.innerHTML = ''; // Clear previous options

    question.options.forEach((option, index) => {
        const li = document.createElement("li");
        li.textContent = option;
        li.addEventListener("click", () => checkAnswer(option));
        optionsList.appendChild(li);
    });
}

function checkAnswer(selectedOption) {
    const currentQuestion = quizData[currentQuestionIndex];
    if (selectedOption === currentQuestion.answer) {
        // Handle correct answer, e.g., update the score
    }
    // Move to the next question
    currentQuestionIndex++;
    
    if (currentQuestionIndex < quizData.length) {
        showQuestion(currentQuestionIndex);
    } else {
        // Quiz is complete
        questionContainer.innerHTML = "<h2>Quiz Complete</h2>";
    }
}

// Initial question display
showQuestion(currentQuestionIndex);

3rd question -------------------------------------------------------------------------------

#To allow the user to select an answer and submit it to move to the next question, you can modify the previous code. Here's an updated example that includes answer selection and submission functionality:

HTML (quiz.html):
<!DOCTYPE html>
<html>
<head>
    <title>Quiz App</title>
</head>
<body>
    <div id="question-container">
        <h1 id="question">Question Text</h1>
        <ul id="options">
            <li>Option 1</li>
            <li>Option 2</li>
            <li>Option 3</li>
            <li>Option 4</li>
        </ul>
    </div>
    <button id="submit-button">Submit</button>
    <button id="next-button">Next</button>

    <script src="quiz.js"></script>
</body>
</html>

#javaScript (quiz.js):
.const quizData = [
    {
        question: "What is the capital of France?",
        options: ["New York", "London", "Paris", "Dublin"],
        answer: "Paris"
    },
    {
        question: "Who painted the Mona Lisa?",
        options: ["Vincent Van Gogh", "Pablo Picasso", "Leonardo Da Vinci", "Claude Monet"],
        answer: "Leonardo Da Vinci"
    }
    // Add more questions as needed
];

const questionContainer = document.getElementById("question-container");
const questionElement = document.getElementById("question");
const optionsList = document.getElementById("options");
const submitButton = document.getElementById("submit-button");
const nextButton = document.getElementById("next-button");

let currentQuestionIndex = 0;
let selectedAnswer = null;

function showQuestion(questionIndex) {
    const question = quizData[questionIndex];
    questionElement.textContent = question.question;

    optionsList.innerHTML = ''; // Clear previous options

    question.options.forEach((option, index) => {
        const li = document.createElement("li");
        li.textContent = option;
        li.addEventListener("click", () => selectAnswer(option));
        optionsList.appendChild(li);
    });
}

function selectAnswer(option) {
    // Highlight the selected option
    const options = optionsList.getElementsByTagName("li");
    for (let i = 0; i < options.length; i++) {
        options[i].classList.remove("selected");
    }
    selectedAnswer = option;
    event.target.classList.add("selected");
}

function checkAnswer() {
    if (selectedAnswer === null) {
        alert("Please select an answer before submitting.");
        return;
    }

    const currentQuestion = quizData[currentQuestionIndex];
    if (selectedAnswer === currentQuestion.answer) {
        // Handle correct answer, e.g., update the score
    }

    // Move to the next question
    currentQuestionIndex++;

    if (currentQuestionIndex < quizData.length) {
        showQuestion(currentQuestionIndex);
        selectedAnswer = null; // Reset selected answer
    } else {
        // Quiz is complete
        questionContainer.innerHTML = "<h2>Quiz Complete</h2>";
    }
}

// Add click event handlers for buttons
submitButton.addEventListener("click", checkAnswer);
nextButton.addEventListener("click", () => showQuestion(currentQuestionIndex));

// Initial question display
showQuestion(currentQuestionIndex);

 4th question--------------------------------------------
 #HTML (quiz.html):

 <!DOCTYPE html>
<html>
<head>
    <title>Quiz App</title>
</head>
<body>
    <div id="question-container">
        <h1 id="question">Question Text</h1>
        <ul id="options">
            <li>Option 1</li>
            <li>Option 2</li>
            <li>Option 3</li>
            <li>Option 4</li>
        </ul>
    </div>
    <button id="submit-button">Submit</button>
    <button id="next-button">Next</button>
    <div id="score-container">
        <p id="score">Score: 0</p>
    </div>

    <script src="quiz.js"></script>
</body>
</html>

#javaScript (quiz.js):
const quizData = [
    {
        question: "What is the capital of France?",
        options: ["New York", "London", "Paris", "Dublin"],
        answer: "Paris"
    },
    {
        question: "Who painted the Mona Lisa?",
        options: ["Vincent Van Gogh", "Pablo Picasso", "Leonardo Da Vinci", "Claude Monet"],
        answer: "Leonardo Da Vinci"
    }
    // Add more questions as needed
];

const questionContainer = document.getElementById("question-container");
const questionElement = document.getElementById("question");
const optionsList = document.getElementById("options");
const submitButton = document.getElementById("submit-button");
const nextButton = document.getElementById("next-button");
const scoreContainer = document.getElementById("score-container");
const scoreElement = document.getElementById("score");

let currentQuestionIndex = 0;
let selectedAnswer = null;
let score = 0;

function showQuestion(questionIndex) {
    const question = quizData[questionIndex];
    questionElement.textContent = question.question;

    optionsList.innerHTML = ''; // Clear previous options

    question.options.forEach((option, index) => {
        const li = document.createElement("li");
        li.textContent = option;
        li.addEventListener("click", () => selectAnswer(option));
        optionsList.appendChild(li);
    });
}

function selectAnswer(option) {
    // Highlight the selected option
    const options = optionsList.getElementsByTagName("li");
    for (let i = 0; i < options.length; i++) {
        options[i].classList.remove("selected");
    }
    selectedAnswer = option;
    event.target.classList.add("selected");
}

function checkAnswer() {
    if (selectedAnswer === null) {
        alert("Please select an answer before submitting.");
        return;
    }

    const currentQuestion = quizData[currentQuestionIndex];
    if (selectedAnswer === currentQuestion.answer) {
        // Handle correct answer and update the score
        score++;
    }

    // Move to the next question
    currentQuestionIndex++;

    if (currentQuestionIndex < quizData.length) {
        showQuestion(currentQuestionIndex);
        selectedAnswer = null; // Reset selected answer
    } else {
        // Quiz is complete, display the final score
        questionContainer.innerHTML = "<h2>Quiz Complete</h2>";
        scoreElement.textContent = "Score: " + score;
    }
}

// Add click event handlers for buttons
submitButton.addEventListener("click", checkAnswer);
nextButton.addEventListener("click", () => showQuestion(currentQuestionIndex));

// Initial question display
showQuestion(currentQuestionIndex);

5th question ----------------------------------------------------------------
#HTML (quiz.html):
<!DOCTYPE html>
<html>
<head>
    <title>Quiz App</title>
</head>
<body>
    <div id="question-container">
        <h1 id="question">Question Text</h1>
        <ul id="options">
            <li>Option 1</li>
            <li>Option 2</li>
            <li>Option 3</li>
            <li>Option 4</li>
        </ul>
    </div>
    <button id="submit-button">Submit</button>
    <button id="next-button">Next</button>
    <div id="score-container">
        <p id="score">Score: 0</p>
    </div>
    <div id="result-container" style="display: none;">
        <h2>Quiz Complete</h2>
        <p id="result-message">Your personalized message will appear here.</p>
    </div>

    <script src="quiz.js"></script>
</body>
</html>

#JavaScript (quiz.js):
const quizData = [
    {
        question: "What is the capital of France?",
        options: ["New York", "London", "Paris", "Dublin"],
        answer: "Paris"
    },
    {
        question: "Who painted the Mona Lisa?",
        options: ["Vincent Van Gogh", "Pablo Picasso", "Leonardo Da Vinci", "Claude Monet"],
        answer: "Leonardo Da Vinci"
    }
    // Add more questions as needed
];

const questionContainer = document.getElementById("question-container");
const questionElement = document.getElementById("question");
const optionsList = document.getElementById("options");
const submitButton = document.getElementById("submit-button");
const nextButton = document.getElementById("next-button");
const scoreContainer = document.getElementById("score-container");
const scoreElement = document.getElementById("score");
const resultContainer = document.getElementById("result-container");
const resultMessageElement = document.getElementById("result-message");

let currentQuestionIndex = 0;
let selectedAnswer = null;
let score = 0;

function showQuestion(questionIndex) {
    const question = quizData[questionIndex];
    questionElement.textContent = question.question;

    optionsList.innerHTML = ''; // Clear previous options

    question.options.forEach((option, index) => {
        const li = document.createElement("li");
        li.textContent = option;
        li.addEventListener("click", () => selectAnswer(option));
        optionsList.appendChild(li);
    });
}

function selectAnswer(option) {
    // Highlight the selected option
    const options = optionsList.getElementsByTagName("li");
    for (let i = 0; i < options.length; i++) {
        options[i].classList.remove("selected");
    }
    selectedAnswer = option;
    event.target.classList.add("selected");
}

function checkAnswer() {
    if (selectedAnswer === null) {
        alert("Please select an answer before submitting.");
        return;
    }

    const currentQuestion = quizData[currentQuestionIndex];
    if (selectedAnswer === currentQuestion.answer) {
        // Handle correct answer and update the score
        score++;
    }

    // Move to the next question
    currentQuestionIndex++;

    if (currentQuestionIndex < quizData.length) {
        showQuestion(currentQuestionIndex);
        selectedAnswer = null; // Reset selected answer
    } else {
        // Quiz is complete, display the final score and personalized message
        questionContainer.style.display = "none";
        scoreContainer.style.display = "none";
        resultContainer.style.display = "block";
        scoreElement.textContent = "Score: " + score;

        // Define personalized messages based on the score
        let resultMessage = "";
        if (score === quizData.length) {
            resultMessage = "Congratulations! You got a perfect score!";
        } else if (score >= quizData.length / 2) {
            resultMessage = "Well done! You did a good job!";
        } else {
            resultMessage = "Keep practicing. You can do better!";
        }
        resultMessageElement.textContent = resultMessage;
    }
}

// Add click event handlers for buttons
submitButton.addEventListener("click", checkAnswer);
nextButton.addEventListener("click", () => showQuestion(currentQuestionIndex));

// Initial question display
showQuestion(currentQuestionIndex);

6th question ----------------------------------------------------------------
#Create a CSS file (e.g., style.css) and link it to your HTML file.
<!DOCTYPE html>
<html>
<head>
    <title>Quiz App</title>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
    <!-- ...rest of your HTML content... -->

    <script src="quiz.js"></script>
</body>
</html>

#CSS (style.css):
/* Basic styling for the question container */
#question-container {
    text-align: center;
    margin: 20px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f5f5f5;
    box-shadow: 2px 2px 5px #888888;
}

/* Styling for the question text */
#question {
    font-size: 20px;
    margin-bottom: 10px;
}

/* Styling for answer options */
#options {
    list-style-type: none;
    padding: 0;
}

#options li {
    margin: 5px 0;
    cursor: pointer;
    padding: 5px 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #fff;
    transition: background-color 0.2s;
}

#options li:hover {
    background-color: #f0f0f0;
}

#options li.selected {
    background-color: #33a1ff;
    color: #fff;
    font-weight: bold;
}

/* Styling for buttons */
#submit-button, #next-button {
    margin: 10px;
    padding: 10px 20px;
    border: none;
    background-color: #33a1ff;
    color: #fff;
    cursor: pointer;
    border-radius: 5px;
    font-size: 16px;
}

#submit-button:hover, #next-button:hover {
    background-color: #1c87c9;
}

/* Styling for the score and result container */
#score-container, #result-container {
    text-align: center;
    margin: 20px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f5f5f5;
    box-shadow: 2px 2px 5px #888888;
}

#score {
    font-size: 18px;
    margin: 10px;
}

#result-message {
    font-size: 20px;
    font-weight: bold;
}




