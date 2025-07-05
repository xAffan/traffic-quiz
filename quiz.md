---
layout: default
title: Traffic Rules Quiz
permalink: /quiz/
---

<section class="quiz-section">
    <div class="container">
        <div class="quiz-header">
            <h1><i class="fas fa-graduation-cap"></i> Traffic Rules Quiz</h1>
            <p>Test your knowledge of Pakistan's traffic rules and road safety. Choose the best answer for each question.</p>
            
            <div class="quiz-stats">
                <div class="stat">
                    <span class="stat-label">Total Questions:</span>
                    <span class="stat-value" id="total-questions">20</span>
                </div>
                <div class="stat">
                    <span class="stat-label">Your Score:</span>
                    <span class="stat-value" id="current-score">0</span>
                </div>
                <div class="stat">
                    <span class="stat-label">Percentage:</span>
                    <span class="stat-value" id="percentage">0%</span>
                </div>
            </div>
        </div>

        <div class="quiz-container">
            <div class="progress-bar">
                <div class="progress-fill" id="progress-fill"></div>
            </div>
            
            <div id="quiz-content">
                <!-- Questions will be loaded here -->
            </div>

            <div class="quiz-controls">
                <button id="prev-btn" class="btn btn-secondary" disabled>
                    <i class="fas fa-chevron-left"></i> Previous
                </button>
                <button id="next-btn" class="btn btn-primary">
                    Next <i class="fas fa-chevron-right"></i>
                </button>
                <button id="submit-btn" class="btn btn-success" style="display: none;">
                    <i class="fas fa-check"></i> Submit Quiz
                </button>
            </div>
        </div>

        <div id="quiz-results" class="quiz-results" style="display: none;">
            <div class="results-header">
                <h2><i class="fas fa-trophy"></i> Quiz Results</h2>
                <div class="score-circle">
                    <div class="score-text">
                        <span id="final-score">0</span>
                        <small>out of 20</small>
                    </div>
                </div>
            </div>
            
            <div class="results-breakdown">
                <div class="result-item correct">
                    <i class="fas fa-check-circle"></i>
                    <span>Correct: <strong id="correct-count">0</strong></span>
                </div>
                <div class="result-item incorrect">
                    <i class="fas fa-times-circle"></i>
                    <span>Incorrect: <strong id="incorrect-count">0</strong></span>
                </div>
                <div class="result-item percentage">
                    <i class="fas fa-percentage"></i>
                    <span>Percentage: <strong id="final-percentage">0%</strong></span>
                </div>
            </div>

            <div class="results-actions">
                <button id="restart-btn" class="btn btn-primary">
                    <i class="fas fa-redo"></i> Retake Quiz
                </button>
                <a href="{{ '/blog/' | relative_url }}" class="btn btn-secondary">
                    <i class="fas fa-book"></i> Read Safety Tips
                </a>
            </div>
        </div>
    </div>
</section>

<script>
// Quiz Data
const quizQuestions = [
    {
        question: "What does a red traffic light indicate?",
        options: ["Stop completely", "Slow down slightly", "Turn left only", "Honk and proceed"],
        correct: 0,
        explanation: "A red light means complete stop. You must wait until the light turns green before proceeding."
    },
    {
        question: "What is the default speed limit in urban areas (Pakistan)?",
        options: ["40 km/h", "50 km/h", "60 km/h", "80 km/h"],
        correct: 2,
        explanation: "The default speed limit in urban areas of Pakistan is 60 km/h unless otherwise posted."
    },
    {
        question: "What shape is a standard stop sign?",
        options: ["Circle", "Triangle", "Rectangle", "Octagon"],
        correct: 3,
        explanation: "Stop signs are octagonal (8-sided) with red background and white text."
    },
    {
        question: "At a zebra crossing, you should:",
        options: ["Stop to let pedestrians cross", "Honk and continue", "Ignore if in a hurry", "Speed up"],
        correct: 0,
        explanation: "Pedestrians have the right of way at zebra crossings. Always stop and let them cross safely."
    },
    {
        question: "When turning right at a green light, you must:",
        options: ["Yield to oncoming traffic", "Drive fast to beat traffic", "Honk for right of way", "Only turn when no cars are behind"],
        correct: 0,
        explanation: "Even with a green light, you must yield to oncoming traffic when making a right turn."
    },
    {
        question: "The maximum speed limit on most motorways in Pakistan is:",
        options: ["80 km/h", "100 km/h", "120 km/h", "140 km/h"],
        correct: 2,
        explanation: "The maximum speed limit on motorways in Pakistan is typically 120 km/h."
    },
    {
        question: "Yellow light means:",
        options: ["Prepare to stop", "Ignore and proceed", "Only turn left", "Pedestrians must go"],
        correct: 0,
        explanation: "Yellow light is a warning to prepare to stop. Do not try to beat the red light."
    },
    {
        question: "When changing lanes on a highway, you should:",
        options: ["Signal and check mirrors", "Swerve quickly", "Honk continuously", "Speed up without looking"],
        correct: 0,
        explanation: "Always signal your intention, check mirrors and blind spots before changing lanes safely."
    },
    {
        question: "On a roundabout, priority is given to:",
        options: ["Vehicles already in the roundabout", "Vehicles entering from the left", "No one, it's a free-for-all", "Fastest cars first"],
        correct: 0,
        explanation: "Vehicles already circulating in the roundabout have the right of way over entering vehicles."
    },
    {
        question: "Driving without fastening seat belts is:",
        options: ["Safe at low speed", "Against the law", "Recommended on highways", "Optional for front seat"],
        correct: 1,
        explanation: "Wearing seat belts is mandatory by law in Pakistan for all passengers in the vehicle."
    },
    {
        question: "A diamond-shaped road sign usually indicates:",
        options: ["Warning or hazard", "Mandatory action", "Service area", "Speed zone"],
        correct: 0,
        explanation: "Diamond-shaped signs are warning signs that alert drivers to potential hazards ahead."
    },
    {
        question: "If an ambulance approaches with sirens on, you must:",
        options: ["Give way immediately", "Race it to the next signal", "Ignore if you're in a hurry", "Stop in the middle of the road"],
        correct: 0,
        explanation: "Emergency vehicles have the right of way. Pull over safely to allow them to pass."
    },
    {
        question: "In poor visibility conditions (fog), you should:",
        options: ["Use low beam headlights", "Use high beams continuously", "Turn lights off to save battery", "Drive faster to clear fog"],
        correct: 0,
        explanation: "Use low beam headlights in fog. High beams reflect off fog and reduce visibility further."
    },
    {
        question: "Before opening your car door on a busy road, you should:",
        options: ["Check side mirrors and blind spot", "Open quickly without looking", "Honk before opening", "Wait for someone to pass you"],
        correct: 0,
        explanation: "Always check mirrors and look over your shoulder before opening doors to avoid accidents."
    },
    {
        question: "Tailgating (driving very close) to the vehicle ahead is:",
        options: ["Dangerous and discouraged", "A good way to save fuel", "Required on narrow roads", "Mandatory in heavy traffic"],
        correct: 0,
        explanation: "Tailgating is dangerous and increases the risk of rear-end collisions. Maintain safe following distance."
    },
    {
        question: "When can you overtake another vehicle on the left side?",
        options: ["Generally never in Pakistan", "Only when the driver in front signals right", "You feel they are driving slowly", "You have a better car"],
        correct: 1,
        explanation: "Overtaking on the left is generally prohibited, except when the vehicle ahead is turning right."
    },
    {
        question: "A 'No U-turn' sign indicates:",
        options: ["You cannot make a U-turn", "You can stop anytime", "You must turn around at will", "Turn only if traffic is clear"],
        correct: 0,
        explanation: "No U-turn signs prohibit making U-turns at that location. Look for designated U-turn points."
    },
    {
        question: "You should always use your indicator when:",
        options: ["Turning or changing lanes", "The street is empty", "You don't feel like it", "Traffic signals are working"],
        correct: 0,
        explanation: "Always use indicators when turning or changing lanes to communicate your intentions to other drivers."
    },
    {
        question: "Driving under the influence of alcohol in Pakistan is:",
        options: ["Illegal and punishable", "Permitted in rural areas only", "Allowed if window is open", "Fine if you drive slowly"],
        correct: 0,
        explanation: "Driving under the influence is illegal throughout Pakistan and carries severe penalties."
    },
    {
        question: "If you hear a strange noise from your vehicle on a highway, you must:",
        options: ["Pull over safely and inspect", "Ignore and continue your journey", "Drive faster to reduce noise", "Stop in the middle of the road"],
        correct: 0,
        explanation: "Strange noises indicate potential mechanical problems. Pull over safely and inspect your vehicle."
    }
];

// Quiz State
let currentQuestion = 0;
let userAnswers = new Array(quizQuestions.length).fill(null);
let quizCompleted = false;

// DOM Elements
const quizContent = document.getElementById('quiz-content');
const prevBtn = document.getElementById('prev-btn');
const nextBtn = document.getElementById('next-btn');
const submitBtn = document.getElementById('submit-btn');
const progressFill = document.getElementById('progress-fill');
const currentScore = document.getElementById('current-score');
const percentage = document.getElementById('percentage');
const quizResults = document.getElementById('quiz-results');
const restartBtn = document.getElementById('restart-btn');

// Initialize Quiz
function initQuiz() {
    currentQuestion = 0;
    userAnswers = new Array(quizQuestions.length).fill(null);
    quizCompleted = false;
    quizResults.style.display = 'none';
    document.querySelector('.quiz-container').style.display = 'block';
    loadQuestion();
    updateProgress();
    updateControls();
}

// Load Current Question
function loadQuestion() {
    const question = quizQuestions[currentQuestion];
    
    quizContent.innerHTML = `
        <div class="question-card">
            <div class="question-header">
                <span class="question-number">Question ${currentQuestion + 1} of ${quizQuestions.length}</span>
                <div class="question-icons">
                    <i class="fas fa-lightbulb"></i>
                </div>
            </div>
            <h3 class="question-text">${question.question}</h3>
            <div class="options-grid">
                ${question.options.map((option, index) => `
                    <button class="option-btn ${userAnswers[currentQuestion] === index ? 'selected' : ''}" 
                            onclick="selectOption(${index})">
                        <span class="option-letter">${String.fromCharCode(65 + index)}</span>
                        <span class="option-text">${option}</span>
                    </button>
                `).join('')}
            </div>
        </div>
    `;
}

// Select Option
function selectOption(optionIndex) {
    userAnswers[currentQuestion] = optionIndex;
    updateScore();
    
    // Update button styles
    document.querySelectorAll('.option-btn').forEach((btn, index) => {
        btn.classList.toggle('selected', index === optionIndex);
    });
    
    updateControls();
}

// Update Progress
function updateProgress() {
    const progress = ((currentQuestion + 1) / quizQuestions.length) * 100;
    progressFill.style.width = progress + '%';
}

// Update Score Display
function updateScore() {
    const answered = userAnswers.filter(answer => answer !== null).length;
    let correct = 0;
    
    userAnswers.forEach((answer, index) => {
        if (answer !== null && answer === quizQuestions[index].correct) {
            correct++;
        }
    });
    
    currentScore.textContent = correct;
    percentage.textContent = answered > 0 ? Math.round((correct / answered) * 100) + '%' : '0%';
}

// Update Controls
function updateControls() {
    prevBtn.disabled = currentQuestion === 0;
    
    if (currentQuestion === quizQuestions.length - 1) {
        nextBtn.style.display = 'none';
        submitBtn.style.display = 'inline-block';
    } else {
        nextBtn.style.display = 'inline-block';
        submitBtn.style.display = 'none';
    }
}

// Navigation Functions
function nextQuestion() {
    if (currentQuestion < quizQuestions.length - 1) {
        currentQuestion++;
        loadQuestion();
        updateProgress();
        updateControls();
    }
}

function prevQuestion() {
    if (currentQuestion > 0) {
        currentQuestion--;
        loadQuestion();
        updateProgress();
        updateControls();
    }
}

// Submit Quiz
function submitQuiz() {
    quizCompleted = true;
    showResults();
}

// Show Results
function showResults() {
    const correct = userAnswers.filter((answer, index) => answer === quizQuestions[index].correct).length;
    const incorrect = quizQuestions.length - correct;
    const finalPercentage = Math.round((correct / quizQuestions.length) * 100);
    
    document.getElementById('final-score').textContent = correct;
    document.getElementById('correct-count').textContent = correct;
    document.getElementById('incorrect-count').textContent = incorrect;
    document.getElementById('final-percentage').textContent = finalPercentage + '%';
    
    document.querySelector('.quiz-container').style.display = 'none';
    quizResults.style.display = 'block';
    
    // Animate score circle
    animateScoreCircle(finalPercentage);
}

// Animate Score Circle
function animateScoreCircle(percentage) {
    const circle = document.querySelector('.score-circle');
    circle.style.background = `conic-gradient(#4CAF50 ${percentage * 3.6}deg, #e0e0e0 0deg)`;
}

// Event Listeners
nextBtn.addEventListener('click', nextQuestion);
prevBtn.addEventListener('click', prevQuestion);
submitBtn.addEventListener('click', submitQuiz);
restartBtn.addEventListener('click', initQuiz);

// Initialize quiz on page load
document.addEventListener('DOMContentLoaded', initQuiz);
</script>
