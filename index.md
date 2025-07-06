---
layout: default
title: Home
description: Test your traffic safety knowledge and learn essential driving tips
---

<section class="hero">
    <div class="container">
        <h1>🚦 Traffic Safety Hub</h1>
        <p>Test your knowledge of traffic rules and learn essential driving tips to become a safer, more confident driver on the road.</p>
        <div class="hero-actions">
            <a href="{{ '/quizzes/' | relative_url }}" class="btn btn-primary">Start Quiz</a>
            <a href="{{ '/about/' | relative_url }}" class="btn btn-outline">Learn More</a>
        </div>
    </div>
</section>

<section class="features">
    <div class="container">
        <h2 class="text-center">Why Traffic Safety Matters</h2>
        <p class="text-center">Learn through interactive experiences designed to make you a safer, more confident driver.</p>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🧠</div>
                <h3>Interactive Quizzes</h3>
                <p>Test your knowledge with carefully crafted questions covering all aspects of traffic safety, from basic rules to advanced scenarios.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">📚</div>
                <h3>Educational Tips</h3>
                <p>Learn with practical advice, real-world scenarios, and best practices for defensive driving and road safety.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🎯</div>
                <h3>Immediate Feedback</h3>
                <p>Get instant results and detailed explanations to help you understand traffic safety concepts more effectively.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">⚡</div>
                <h3>Quick Learning</h3>
                <p>Short, focused lessons and quizzes that fit into your busy schedule while maximizing learning impact.</p>
            </div>
        </div>
    </div>
</section>

<section class="features" style="background: var(--light-bg);">
    <div class="container">
        <h2 class="text-center">Popular Quizzes</h2>
        <p class="text-center">Start with these popular quizzes to test your traffic safety knowledge.</p>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🚥</div>
                <h3><a href="{{ '/quiz/basic-traffic-rules/' | relative_url }}">Basic Traffic Rules</a></h3>
                <p>Essential traffic rules every driver should know. Perfect for new drivers or a refresher course.</p>
                <a href="{{ '/quiz/basic-traffic-rules/' | relative_url }}" class="btn btn-primary">Start Quiz</a>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🛡️</div>
                <h3><a href="{{ '/quiz/defensive-driving/' | relative_url }}">Defensive Driving</a></h3>
                <p>Learn advanced techniques to anticipate and avoid potential road hazards and dangerous situations.</p>
                <a href="{{ '/quiz/defensive-driving/' | relative_url }}" class="btn btn-primary">Start Quiz</a>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🌧️</div>
                <h3><a href="{{ '/quiz/weather-driving/' | relative_url }}">Weather Conditions</a></h3>
                <p>Master driving in challenging weather conditions including rain, snow, fog, and extreme temperatures.</p>
                <a href="{{ '/quiz/weather-driving/' | relative_url }}" class="btn btn-primary">Start Quiz</a>
            </div>
        </div>
    </div>
</section>

<section class="features">
    <div class="container">
        <h2 class="text-center">Latest Safety Tips</h2>
        <p class="text-center">Stay updated with the latest traffic safety advice and defensive driving techniques.</p>
        
        <div class="blog-grid">
            {% for post in site.posts limit:3 %}
            <article class="blog-card">
                <div class="blog-image">
                    {% if post.icon %}{{ post.icon }}{% else %}📰{% endif %}
                </div>
                <div class="blog-content">
                    <div class="blog-meta">
                        <span>{{ post.date | date: "%B %d, %Y" }}</span>
                        {% if post.reading_time %} • {{ post.reading_time }} min read{% endif %}
                    </div>
                    <h3 class="blog-title">
                        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                    </h3>
                    <p>{{ post.excerpt | strip_html | truncate: 120 }}</p>
                    <a href="{{ post.url | relative_url }}" class="btn btn-outline">Read More</a>
                </div>
            </article>
            {% endfor %}
        </div>
        
        <div class="text-center mt-3">
            <a href="{{ '/blog/' | relative_url }}" class="btn btn-secondary">View All Articles</a>
        </div>
    </div>
</section>
