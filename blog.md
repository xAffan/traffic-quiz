---
layout: default
title: Safety Blog
description: Expert tips, guides, and insights for safer driving
---

<section class="features" style="padding-top: 4rem;">
    <div class="container">
        <header class="text-center mb-3">
            <h1>📰 Traffic Safety Blog</h1>
            <p>Stay informed with the latest safety tips, driving techniques, and expert insights to help you become a safer, more confident driver.</p>
        </header>

        {% if site.posts.size > 0 %}
        <div class="blog-grid">
            {% for post in site.posts %}
            <article class="blog-card">
                {% if post.featured_image %}
                <div class="blog-image">
                    <img src="{{ post.featured_image | relative_url }}" alt="{{ post.title }}">
                </div>
                {% else %}
                <div class="blog-image">
                    {% if post.icon %}{{ post.icon }}{% else %}📰{% endif %}
                </div>
                {% endif %}
                
                <div class="blog-content">
                    <div class="blog-meta">
                        <span>{{ post.date | date: "%B %d, %Y" }}</span>
                        {% if post.author %} • By {{ post.author }}{% endif %}
                        {% if post.reading_time %} • {{ post.reading_time }} min read{% endif %}
                    </div>
                    
                    <h2 class="blog-title">
                        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
                    </h2>
                    
                    <p>{{ post.excerpt | strip_html | truncate: 150 }}</p>
                    
                    {% if post.tags %}
                    <div class="post-tags">
                        {% for tag in post.tags limit:3 %}
                        <span class="tag">{{ tag }}</span>
                        {% endfor %}
                    </div>
                    {% endif %}
                    
                    <a href="{{ post.url | relative_url }}" class="btn btn-outline">Read Article</a>
                </div>
            </article>
            {% endfor %}
        </div>
        {% else %}
        <div class="text-center">
            <p>Blog posts are coming soon! Check back regularly for new safety tips and driving guides.</p>
        </div>
        {% endif %}
    </div>
</section>

<section class="features" style="background: var(--light-bg);">
    <div class="container">
        <h2 class="text-center">Popular Topics</h2>
        <p class="text-center">Explore our most popular safety topics and driving guides.</p>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🛡️</div>
                <h3>Defensive Driving</h3>
                <p>Learn advanced techniques to anticipate hazards, manage risk, and avoid accidents through proactive driving strategies.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🌦️</div>
                <h3>Weather Safety</h3>
                <p>Master driving in challenging conditions including rain, snow, ice, fog, and extreme weather situations.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🚧</div>
                <h3>Road Signs Guide</h3>
                <p>Comprehensive guides to understanding traffic signs, signals, and road markings for safer navigation.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🚗</div>
                <h3>Vehicle Safety</h3>
                <p>Essential vehicle maintenance tips, safety equipment guides, and pre-trip inspection checklists.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🛣️</div>
                <h3>Highway Driving</h3>
                <p>Safe merging, lane changing, and high-speed driving techniques for confident highway travel.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🎯</div>
                <h3>New Driver Tips</h3>
                <p>Essential guidance for new drivers covering everything from basic skills to building confidence on the road.</p>
            </div>
        </div>
    </div>
</section>

<section class="features">
    <div class="container">
        <h2 class="text-center">Stay Updated</h2>
        <p class="text-center">Don't miss our latest safety tips and driving guides.</p>
        
        <div class="text-center">
            <div style="max-width: 500px; margin: 0 auto; padding: 2rem; background: white; border-radius: 1rem; box-shadow: var(--shadow);">
                <h3>📧 Subscribe to Our Newsletter</h3>
                <p>Get weekly safety tips and new quiz notifications delivered to your inbox.</p>
                <form style="display: flex; gap: 1rem; margin-top: 1.5rem;">
                    <input type="email" placeholder="Enter your email" style="flex: 1; padding: 0.75rem; border: 2px solid var(--border-color); border-radius: 0.5rem;">
                    <button type="submit" class="btn btn-primary">Subscribe</button>
                </form>
                <p style="font-size: 0.875rem; color: var(--text-secondary); margin-top: 1rem;">We respect your privacy. Unsubscribe at any time.</p>
            </div>
        </div>
    </div>
</section>
</script>
