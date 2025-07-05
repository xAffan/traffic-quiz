# 🚦 Traffic Safety Hub

A comprehensive traffic safety education website built with Jekyll, featuring interactive quizzes, expert safety tips, and modern responsive design.

## 🌟 Features

### Interactive Quizzes
- **Multiple Choice Questions**: Carefully crafted questions covering all aspects of traffic safety
- **Instant Feedback**: Immediate results with detailed explanations for each answer
- **Progress Tracking**: Visual progress indicators and scoring system
- **Difficulty Levels**: Quizzes ranging from basic to advanced topics
- **Retake Capability**: Users can retake quizzes to reinforce learning

### Safety Blog
- **Expert Articles**: In-depth guides on defensive driving, weather safety, and road signs
- **Practical Tips**: Real-world advice that drivers can immediately apply
- **Regular Updates**: Fresh content covering the latest in traffic safety
- **Easy Navigation**: Well-organized topics and search functionality

### Modern Design
- **Responsive Layout**: Optimized for desktop, tablet, and mobile devices
- **Professional UI**: Clean, modern design with intuitive navigation
- **Accessibility**: Built with web accessibility standards in mind
- **Fast Loading**: Optimized performance for quick loading times

## 🚀 Getting Started

### Prerequisites
- Ruby 3.0 or higher
- Bundler gem
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/traffic-quiz.git
   cd traffic-quiz
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```

3. **Run the development server**
   ```bash
   bundle exec jekyll serve
   ```

4. **Open your browser**
   Visit `http://localhost:4000` to see the site

### Building for Production

```bash
bundle exec jekyll build
```

The built site will be in the `_site` directory.

## � Project Structure

```
traffic-quiz/
├── _config.yml          # Jekyll configuration
├── _layouts/             # Page layouts
│   ├── default.html      # Main site layout
│   ├── post.html         # Blog post layout
│   └── quiz.html         # Quiz layout
├── _posts/               # Blog posts
├── _quizzes/             # Quiz content
├── assets/
│   ├── css/
│   │   └── main.css      # Main stylesheet
│   └── js/
│       └── main.js       # JavaScript functionality
├── pages/
│   ├── about.md          # About page
│   ├── blog.md           # Blog listing
│   └── quizzes.md        # Quiz listing
└── index.md              # Homepage
```

## 🎯 Creating Content

### Adding a New Quiz

1. Create a new file in `_quizzes/` directory
2. Use the following front matter format:

```yaml
---
layout: quiz
title: "Your Quiz Title"
description: "Brief description of the quiz"
difficulty: easy # easy, medium, hard
questions:
  - question: "Your question text"
    options:
      - "Option A"
      - "Option B"
      - "Option C"
      - "Option D"
    correct: 0 # Index of correct answer (0-3)
    explanation: "Explanation of why this answer is correct"
---
```

### Adding a Blog Post

1. Create a new file in `_posts/` directory with format: `YYYY-MM-DD-title.md`
2. Use the following front matter:

```yaml
---
layout: post
title: "Your Article Title"
date: YYYY-MM-DD
author: "Author Name"
reading_time: 5
icon: "🚗"
tags: ["tag1", "tag2"]
excerpt: "Brief description of the article"
---
```

## 💡 Contributing
Feel free to **fork** the repo and submit a PR with improvements, new quizzes, or blog articles!

---

**Built with ❤️ for road safety education**

Made with ❤️ using **HTML, CSS, and JavaScript**.  
Stay safe on the roads! 🚦  
