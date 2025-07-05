---
layout: default
title: Quiz Library
description: Test your traffic safety knowledge with our comprehensive collection of interactive quizzes
---

<section class="features" style="padding-top: 4rem;">
    <div class="container">
        <header class="text-center mb-3">
            <h1>🎯 Traffic Safety Quizzes</h1>
            <p>Challenge yourself with our collection of interactive quizzes designed to test and improve your traffic safety knowledge.</p>
        </header>

        <div class="features-grid">
            {% for quiz in site.quizzes %}
            <div class="feature-card">
                <div class="feature-icon">
                    {% if quiz.title contains 'Basic' %}🚥
                    {% elsif quiz.title contains 'Defensive' %}🛡️
                    {% elsif quiz.title contains 'Weather' %}🌧️
                    {% elsif quiz.title contains 'Signs' %}🚧
                    {% elsif quiz.title contains 'Highway' %}🛣️
                    {% else %}🚗
                    {% endif %}
                </div>
                <h3>{{ quiz.title }}</h3>
                <p>{{ quiz.description }}</p>
                <div class="quiz-meta">
                    <span class="quiz-difficulty {{ quiz.difficulty | default: 'medium' }}">
                        <i class="fas fa-star"></i>
                        {{ quiz.difficulty | default: 'Medium' | capitalize }}
                    </span>
                    {% if quiz.questions %}
                    <span class="quiz-questions">
                        <i class="fas fa-question-circle"></i>
                        {{ quiz.questions.size }} Questions
                    </span>
                    {% endif %}
                </div>
                <a href="{{ quiz.url | relative_url }}" class="btn btn-primary">Start Quiz</a>
            </div>
            {% endfor %}
        </div>

        {% if site.quizzes.size == 0 %}
        <div class="text-center">
            <p>More quizzes coming soon! Check back regularly for new challenges.</p>
        </div>
        {% endif %}
    </div>
</section>

<section class="features" style="background: var(--light-bg);">
    <div class="container">
        <h2 class="text-center">Quiz Categories</h2>
        <p class="text-center">Browse quizzes by topic to focus on areas you want to improve.</p>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🚦</div>
                <h3>Basic Traffic Rules</h3>
                <p>Fundamental rules every driver should know including right-of-way, speed limits, and basic signaling.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🛡️</div>
                <h3>Defensive Driving</h3>
                <p>Advanced techniques for anticipating hazards, managing risk, and avoiding dangerous situations.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🚧</div>
                <h3>Road Signs & Signals</h3>
                <p>Comprehensive coverage of warning signs, regulatory signs, and traffic signals.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🌦️</div>
                <h3>Weather Conditions</h3>
                <p>Safe driving techniques for rain, snow, ice, fog, and other challenging weather conditions.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🛣️</div>
                <h3>Highway Safety</h3>
                <p>Merging, lane changes, high-speed driving, and highway-specific safety considerations.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🚨</div>
                <h3>Emergency Situations</h3>
                <p>How to handle vehicle breakdowns, accidents, and other emergency situations safely.</p>
            </div>
        </div>
    </div>
</section>

<section class="features">
    <div class="container">
        <h2 class="text-center">How Our Quizzes Work</h2>
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">📝</div>
                <h3>Take the Quiz</h3>
                <p>Answer multiple-choice questions at your own pace. Each quiz includes detailed explanations for every answer.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🎯</div>
                <h3>Get Your Score</h3>
                <p>Receive immediate feedback with your score and see which questions you got right or wrong.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">📚</div>
                <h3>Learn from Explanations</h3>
                <p>Read detailed explanations for each question to understand the reasoning behind correct answers.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🔄</div>
                <h3>Retake and Improve</h3>
                <p>Retake quizzes as many times as you want to reinforce your learning and track improvement.</p>
            </div>
        </div>
    </div>
</section>

<style>
.quiz-meta {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin: 1rem 0;
    font-size: 0.875rem;
}

.quiz-difficulty.easy { color: var(--success-color); }
.quiz-difficulty.medium { color: var(--warning-color); }
.quiz-difficulty.hard { color: var(--danger-color); }

.quiz-questions, .quiz-difficulty {
    display: flex;
    align-items: center;
    gap: 0.25rem;
}
</style>
