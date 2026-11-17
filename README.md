# StudyMate AI

An intelligent study assistant for university students. Students save their own lessons, then use AI to turn them into simpler summaries, practice quizzes, and answers to questions. Quiz results are stored so students can see what to review next.

**Course:** Web 3
**Team:** Dani Ghanem and Firas Barakeh

## Features

- User registration and login with personal accounts
- Lesson management: create, organize by subject, edit, and delete
- AI summary generator: simpler explanations, key points, and revision notes
- AI quiz generator: multiple-choice questions with scores and explanations
- AI study assistant: ask questions about a saved lesson
- Progress dashboard: quizzes taken, average score, and lessons to review

Summaries and quizzes are the core of the first version. The study assistant and the dashboard are built on top of them.

## Tech stack

| Technology | Purpose |
|---|---|
| HTML, CSS, Bootstrap 5 | Structure, design, responsive layout |
| JavaScript | Interactive pages, quizzes, API calls |
| PHP | Backend logic and AI API integration |
| MySQL | Users, lessons, summaries, quizzes, results, chat |
| XAMPP | Local development environment |
| AI API (e.g. OpenAI) | Generates summaries, questions, and explanations |

## How the AI integration works

1. The student saves a lesson.
2. The browser sends a request to a PHP endpoint.
3. PHP validates the content and calls the AI API.
4. The result is saved in MySQL and shown on the page.

The AI API key is stored only on the server, in `api/config.php`. It is never included in JavaScript or HTML, and it is not committed to this repository.

## Database

| Table | Content |
|---|---|
| `users` | Student accounts and password hashes |
| `subjects` | Subjects such as Programming or Databases |
| `lessons` | Lesson titles and original content |
| `summaries` | AI-generated summaries linked to lessons |
| `quizzes` | Quiz information and generated questions |
| `questions` | Individual questions, options, and correct answers (optional) |
| `quiz_results` | Scores and completion dates |
| `chat_messages` | Study assistant conversations per lesson |

## Project structure

```
studymate-ai/
├── index.html          Landing page
├── register.html       Create account
├── login.html          Log in
├── dashboard.html      Lessons, stats, review list
├── lesson.html         Lesson, summary, quiz, and assistant tabs
├── assets/
│   ├── style.css
│   └── app.js          Shared helpers and API contract (see top comment)
├── api/                PHP endpoints
│   ├── config.example.php
│   └── ...
└── database/
    └── schema.sql
```

## Getting started

### Requirements

- [XAMPP](https://www.apachefriends.org/) (Apache, PHP, MySQL)
- An API key from an AI provider

### Setup

1. Copy the project folder into `C:\xampp\htdocs\studymate-ai` (or your XAMPP `htdocs` path).
2. Start **Apache** and **MySQL** from the XAMPP control panel.
3. Open `http://localhost/phpmyadmin`, create a database named `studymate`, and import `database/schema.sql`.
4. Copy `api/config.example.php` to `api/config.php` and fill in your database details and AI API key.
5. Open `http://localhost/studymate-ai/` in your browser.

## Security

- Passwords are hashed, never stored as plain text.
- Database queries use prepared statements.
- The AI API key stays on the server.
- Quiz answers are checked on the server, so correct answers are not sent to the browser before submission.
- `api/config.php` is listed in `.gitignore`.

## Limitations

- Lesson content is sent to an external AI API, which raises privacy considerations.
- The AI API needs an internet connection and may have costs and rate limits.
- The platform is meant to support learning, not replace it.

## Possible future improvements

- Difficulty selection (beginner, intermediate, advanced)
- Explanations in English and French
- Automatic review recommendations after low quiz scores
- PDF lesson uploads


