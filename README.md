# Adaptive AI Job Application Bot

## Overview

An intelligent, self-learning automation tool that finds and fills job application forms directly on company websites. The system automatically recognizes and adapts to new input fields, learning from past interactions to handle increasingly diverse form variations.

Designed as a personal assistant and research tool - not for large-scale scraping or automated mass applications.

---

## Core Concept

1. Detects and analyzes input fields on career or job application pages
2. Reads each field's attributes (label, placeholder, name, etc.)
3. Matches these attributes to known categories (e.g. "Name", "Email", "Upload CV")
4. Prompts for decisions when encountering unknown fields (skip, fill, or custom response)
5. Stores new rules for future use
6. Learns over time, improving accuracy with each site visited

---

## Key Features

- Form field detection using browser automation
- Intelligent field mapping through fuzzy matching and AI models
- Persistent local database of learned field rules
- Configurable filters and preferences
- Optional dashboard for reviewing or editing learned data

---

## Suggested Tech Stack

### Programming Language

**Python** (Recommended for rapid prototyping, scraping, and AI integration)
- Alternative: Node.js if you prefer JavaScript across the stack

### Web Automation

**Playwright** (Modern and reliable browser automation for dynamic websites)
- Alternative: Selenium (wider community support, slightly slower)

### Data Parsing

**BeautifulSoup4** (Easy HTML parsing for static pages)
- Alternative: lxml (faster but more complex)

### Storage

**SQLite** (Simple file-based database for storing rules and form mappings)
- Alternative: PostgreSQL for multi-user or scalable versions

### Fuzzy Matching and Semantic Analysis

**FuzzyWuzzy or RapidFuzz** (For simple string similarity)
- Optional: Sentence Transformers (e.g. `all-MiniLM-L6-v2`) for semantic matching using embeddings

### Backend / API (if dashboard is added)

**Flask or FastAPI** (Lightweight Python web frameworks)
- Alternative: Laravel (PHP) or Express.js (Node.js)

### Frontend (for dashboard)

**React or Vue.js** (For managing field mappings visually)
- Alternative: Basic HTML templates with Flask for simpler setups

### Scheduling

**Cron or Celery** (To run periodic scans or updates)

### Optional AI Integration

**OpenAI API** (To generate cover letters or predict field meanings)
- Alternative: Local language models using `transformers` library for offline use

---

## Learning Method

The bot uses a layered recognition system:

1. **Rule-based** - Direct text checks (e.g. "if 'email' in label")
2. **Fuzzy matching** - Detects close matches like "E-mail" or "Contact Email"
3. **Semantic comparison** - Uses vector similarity to detect meaning
4. **User input** - Stores new instructions when unknown fields appear

---

## Example Data Flow

1. Bot visits a company career page
2. It finds all form elements (`input`, `textarea`, `select`)
3. For each field, it identifies its purpose using rules and text similarity
4. If the field is recognized, it auto-fills it
5. If the field is unknown, it logs the label and asks for guidance
6. It stores the decision so next time it knows what to do automatically

---

## Database Example

| Field Label | Normalized Intent | Action | Value | Confidence |
|-------------|-------------------|--------|-------|------------|
| Full Name | name | fill | Liam Nugent | 1.00 |
| E-mail Address | email | fill | liamnugent@hizhub.com | 0.95 |
| Upload Resume | cv_upload | fill | /path/to/cv.pdf | 0.98 |
| Preferred Pronouns | pronouns | skip | NULL | 0.90 |

---

## Development Roadmap

1. Create scraper for static job pages
2. Add Playwright to handle dynamic pages
3. Implement rule-based matching and fuzzy logic
4. Build local database for saving field knowledge
5. Add learning layer for new fields
6. Optionally add a web dashboard for review and control
7. Experiment with AI-assisted cover letter or resume matching

---

## Important Notes

- This project should respect website `robots.txt` files and legal restrictions
- It should not perform automated submissions without explicit user consent
- Intended for personal use as a research and productivity tool
- Always review applications before final submission
