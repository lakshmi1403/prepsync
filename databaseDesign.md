# Database Schema Design (Conceptual)

This document outlines the structure of the tables, their columns, and relationships for a PostgreSQL database.

## Table: users

- **id** (BIGSERIAL PRIMARY KEY): Unique identifier for the user.
- **email** (VARCHAR(255) UNIQUE NOT NULL): User's email, used for login, must be unique.
- **password** (VARCHAR(255) NOT NULL): Hashed password for the user.
- **last_activity_date** (DATE): Date of the user's last activity (for streak tracking).
- **created_at** (TIMESTAMP DEFAULT CURRENT_TIMESTAMP): Timestamp when the user account was created.
- **updated_at** (TIMESTAMP DEFAULT CURRENT_TIMESTAMP): Timestamp when the user account was last updated.

## Table: questions

- **id** (BIGSERIAL PRIMARY KEY): Unique identifier for the question.
- **user_id** (BIGINT NOT NULL REFERENCES users(id)): Foreign key linking to the user who owns this question.
- **title** (VARCHAR(255) NOT NULL): Title of the coding question.
- **url** (VARCHAR(500)): Optional URL to the question (e.g., LeetCode link).
- **difficulty** (VARCHAR(50) NOT NULL): Difficulty level (e.g., 'Easy', 'Medium', 'Hard').
- **topic** (VARCHAR(100) NOT NULL): Topic of the question (e.g., 'Arrays', 'Trees', 'Dynamic Programming').
- **status** (VARCHAR(50) NOT NULL): Current status (e.g., 'To Do', 'In Progress', 'Solved').
- **created_at** (TIMESTAMP DEFAULT CURRENT_TIMESTAMP): Timestamp when the question was added.
- **updated_at** (TIMESTAMP DEFAULT CURRENT_TIMESTAMP): Timestamp when the question was last updated.

## Table: notes

- **id** (BIGSERIAL PRIMARY KEY): Unique identifier for the note.
- **user_id** (BIGINT NOT NULL REFERENCES users(id)): Foreign key linking to the user who owns this note.
- **title** (VARCHAR(255) NOT NULL): Title of the note.
- **content** (TEXT NOT NULL): Markdown content of the note.
- **created_at** (TIMESTAMP DEFAULT CURRENT_TIMESTAMP): Timestamp when the note was added.
- **updated_at** (TIMESTAMP DEFAULT CURRENT_TIMESTAMP): Timestamp when the note was last updated.
