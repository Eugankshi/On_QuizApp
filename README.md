# On_QuizApp

#frontendcode

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Online Quiz Application</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .quiz-container {
            max-width: 600px;
            margin: 0 auto;
        }
        .question {
            font-size: 1.2em;
            margin-bottom: 10px;
        }
        .answers {
            list-style-type: none;
            padding: 0;
        }
        .answers li {
            margin-bottom: 10px;
        }
        .result {
            margin-top: 20px;
            font-size: 1.5em;
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <h1>Online Quiz</h1>
        <div id="quiz"></div>
        <button onclick="submitQuiz()">Submit</button>
        <div class="result" id="result"></div>
    </div>

    <script>
        const questions = [
            {
                question: "What is the capital of France?",
                options: ["Berlin", "Madrid", "Paris", "Rome"],
                correctAnswer: "Paris"
            },
            {
                question: "Which planet is known as the Red Planet?",
                options: ["Earth", "Mars", "Jupiter", "Saturn"],
                correctAnswer: "Mars"
            },
            {
                question: "Who wrote 'Hamlet'?",
                options: ["Charles Dickens", "William Shakespeare", "Leo Tolstoy", "Mark Twain"],
                correctAnswer: "William Shakespeare"
            }
        ];

        let quiz = document.getElementById("quiz");

        // Display quiz questions
        questions.forEach((q, index) => {
            let questionElement = document.createElement("div");
            questionElement.className = "question";
            questionElement.innerHTML = `<p>${q.question}</p>`;

            let optionsList = document.createElement("ul");
            optionsList.className = "answers";
            
            q.options.forEach((option, i) => {
                optionsList.innerHTML += `
                    <li>
                        <input type="radio" name="question${index}" value="${option}">
                        ${option}
                    </li>
                `;
            });

            questionElement.appendChild(optionsList);
            quiz.appendChild(questionElement);
        });

        // Submit quiz and calculate score
        function submitQuiz() {
            let score = 0;
            questions.forEach((q, index) => {
                let userAnswer = document.querySelector(`input[name="question${index}"]:checked`);
                if (userAnswer && userAnswer.value === q.correctAnswer) {
                    score++;
                }
            });
            document.getElementById("result").innerHTML = `You scored ${score} out of ${questions.length}`;
        }
    </script>
</body>
</html>

