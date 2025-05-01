# 🌐 Task Manager

A full-stack web application to streamline task management. Designed with scalability and usability in mind, this task manager enables users to manage and track on tasks efficiently in real-time.

---

## 📌 Project Overview

**The Task Manager** is built to address the inefficiencies of manual task tracking by offering:
- A **centralized platform** for task assignment and tracking.
- **Modern UI/UX** for intuitive interaction .

---

## ❓ Why This Project?

In today’s fast-paced work environments, managing tasks via spreadsheets or outdated systems can lead to reduced productivity. This platform solves that problem by:

- Automating task workflow.
- Enhancing visibility of work progress.

---

## 🧠 Background

With distributed teams becoming the norm, having a reliable digital task management tool is vital. This app uses a **FULL stack** approach to deliver a robust and responsive experience. The use of **Redux Toolkit**, **Tailwind CSS**, and **Headless UI** ensures a seamless and dynamic frontend while **MySQL**, **Sequelize** and **Express.js** power a solid backend.

---

## 👥 User Features

### 🔄 Task Interaction
- Change task status (`todo`, `in progress`, `completed`)
- View detailed task descriptions and metadata

### 💬 Communication
- Add comments and chat to task activities

---

## 🔐 General Features

- **Authentication & Authorization**
  - Secure login for users
- **User Dashboard**
  - Personalized task views and filters
  - Activity summary and quick status filters

---

## 🚀 Technologies Used

### 🖥️ Frontend
- [React (Vite)](https://vitejs.dev/)
- [Redux Toolkit](https://redux-toolkit.js.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Headless UI](https://headlessui.dev/)

### 🛠️ Backend
- [Node.js](https://nodejs.org/) + [Express.js](https://expressjs.com/)

### 💾 Database
- [MySQL Workbench](https://www.mysql.com/products/workbench/) — for managing and visualizing the database.
- [Sequelize](https://sequelize.org/) — as the ORM (Object Relational Mapper) for handling database queries and models in Node.js.

---

## ⚙️ Setup Instructions

### 🧩 Server Setup

#### 1. Create `.env` inside `/server`
```env
PORT=8800
MYSQL_HOST=localhost
MYSQL_USER=root
MYSQL_PASSWORD=your_mysqlWorkbench_password
MYSQL_DATABASE=your_mysqlWorkbench_database_name
JWT_SECRET=your_secret_key
NODE_ENV=development

## 🚀 Getting Started

### 🖥️ Server Setup

1. Navigate to the server directory and install dependencies:
   ```bash
   cd server
   npm install
   nodemon index
The server will run at:
👉 http://localhost:8800
```


### 🧩 Client Setup

#### 1. Create `.env` inside `/client`
```env
VITE_APP_BASE_URL=http://localhost:8800

## 🚀 Getting Started

### 🖥️ Client Setup

1. Navigate to the client directory and install dependencies:
   ```bash
   cd client
   npm install
   npm run dev
The server will run at:
👉 http://localhost:3000
```

## 🗃️ Database Schema

### 📍 Database Name: `task_manager`

### 👤 `users` Table

| Column     | Type           | Constraints                         |
|------------|----------------|-------------------------------------|
| `id`       | INT            | Primary Key, Auto Increment         |
| `name`     | VARCHAR(255)   | Not Null                            |
| `email`    | VARCHAR(255)   | Not Null, Unique                    |
| `password` | VARCHAR(255)   | Not Null                            |
| `isAdmin`  | BOOLEAN        | Default: FALSE                      |
| `isActive` | BOOLEAN        | Default: TRUE                       |

---

### ✅ `tasks` Table

| Column         | Type                                 | Constraints                                     |
|----------------|--------------------------------------|-------------------------------------------------|
| `id`           | INT                                  | Primary Key, Auto Increment                     |
| `title`        | VARCHAR(255)                         | Not Null                                        |
| `createdAtDate`| DATETIME                             | Default: CURRENT_TIMESTAMP                      |
| `dueDate`      | DATETIME                             | Optional                                        |
| `priority`     | ENUM('high', 'medium', 'normal', 'low') | Default: 'normal'                           |
| `stage`        | ENUM('todo', 'in progress', 'completed') | Default: 'todo'                             |
| `description`  | TEXT                                 | Optional                                        |
| `isTrashed`    | BOOLEAN                              | Default: FALSE                                  |
| `userId`       | INT                                  | Foreign Key → `users(id)`, On Delete CASCADE    |
| `createdAt`    | DATETIME                             | Default: CURRENT_TIMESTAMP                      |
| `updatedAt`    | DATETIME                             | Auto-update on modification                     |

---

### 📌 `task_activities` Table

| Column      | Type                                                            | Constraints                                             |
|-------------|-----------------------------------------------------------------|---------------------------------------------------------|
| `id`        | INT                                                             | Primary Key, Auto Increment                             |
| `taskId`    | INT                                                             | Foreign Key → `tasks(id)`, On Delete CASCADE            |
| `userId`    | INT                                                             | Foreign Key → `users(id)`, On Delete SET NULL           |
| `type`      | ENUM('assigned', 'started', 'in progress', 'bug', 'completed', 'commented') | Default: 'assigned'           |
| `activity`  | TEXT                                                            | Optional                                                 |
| `created_at`| TIMESTAMP                                                       | Default: CURRENT_TIMESTAMP                               |

---
