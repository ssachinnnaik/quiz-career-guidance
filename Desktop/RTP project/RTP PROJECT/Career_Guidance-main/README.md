# Career Guidance Application

A comprehensive web application designed to help users discover their ideal career paths through personalized quizzes, job recommendations, and career planning tools.

## Table of Contents
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Deployment](#deployment)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

## Features

### 🔐 User Authentication
- Secure user registration and login
- Password hashing with bcrypt
- Session management

### 📝 Career Assessment Quiz
- 6-question personality quiz to determine career preferences
- Multiple choice questions covering skills, work style, and interests
- Personalized career recommendations based on quiz results

### 💼 Job Search & Recommendations
- Integration with JSearch API for real-time job listings
- Location-based job search (focused on Indian cities)
- Salary range filtering
- Job category filtering

### 🗺️ Career Roadmaps
- Detailed career progression paths
- Step-by-step guidance for skill development
- Salary expectations and workload information

### ⚖️ Career Comparison Tool
- Side-by-side comparison of different career paths
- Resume builder integration
- Career metrics comparison (salary, work-life balance, growth)

### 📄 Resume Builder
- Interactive resume creation tool
- Multiple templates and customization options
- Export functionality

## Technologies Used

### Frontend
- **HTML5** - Structure and content
- **CSS3** - Styling and responsive design
- **JavaScript (ES6+)** - Client-side logic and interactivity

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **PostgreSQL** - Database
- **bcrypt** - Password hashing
- **CORS** - Cross-origin resource sharing

### External APIs
- **JSearch API** - Job search and listings
- **Axios** - HTTP client for API requests

### Deployment
- **Render** - Cloud hosting platform

## Project Structure

```
Career_Guidance-main/
├── assets/
│   ├── css/           # Stylesheets for each page
│   ├── js/            # JavaScript files for functionality
│   └── data/          # Static data files (careers.json)
├── node_modules/      # Dependencies (auto-generated)
├── .gitignore         # Git ignore rules
├── auth.html          # Login/Signup page
├── compare.html       # Career comparison tool
├── index.html         # Landing page
├── jobs.html          # Job search page
├── package.json       # Project dependencies and scripts
├── quiz.html          # Career assessment quiz
├── recommendation.html # Career recommendations display
├── render.yaml        # Render deployment configuration
├── resume-builder.html # Resume creation tool
├── roadmap.html       # Career roadmap display
├── server.js          # Main server file
└── simple-server.js   # Alternative server implementation
```

## Prerequisites

Before running this application, make sure you have the following installed:

- **Node.js** (version 18 or higher)
- **PostgreSQL** (version 13 or higher)
- **Git** (for version control)
- **npm** (comes with Node.js)

## Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ssachinnaik/quiz-career-guidance.git
   cd Career_Guidance-main
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Environment Setup:**
   Create a `.env` file in the root directory with the following variables:
   ```env
   PORT=3000
   RAPIDAPI_KEY=your_rapidapi_key_here
   DATABASE_URL=postgresql://username:password@localhost:5432/mydb
   ```

## Database Setup

1. **Create PostgreSQL Database:**
   ```sql
   CREATE DATABASE mydb;
   CREATE USER myuser WITH PASSWORD 'mypassword';
   GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;
   ```

2. **Database Connection:**
   The application will automatically create the required tables on startup.

## Running the Application

1. **Start the server:**
   ```bash
   npm start
   ```

2. **Access the application:**
   Open your browser and navigate to `http://localhost:3000`

3. **First-time setup:**
   - Visit the authentication page to create an account
   - Take the career assessment quiz
   - Explore job listings and career recommendations

## API Endpoints

### Authentication
- `POST /signup` - User registration
- `POST /login` - User login

### Jobs
- `GET /api/jobs` - Fetch job listings with filters
- `GET /api/locations` - Get location suggestions

## Deployment

### Render Deployment
The application is configured for deployment on Render:

1. Connect your GitHub repository to Render
2. Use the `render.yaml` configuration file
3. Set environment variables in Render dashboard
4. Deploy the application

### Environment Variables for Production
```env
NODE_ENV=production
PORT=10000
RAPIDAPI_KEY=your_production_api_key
DATABASE_URL=your_production_database_url
```

## Screenshots

### Landing Page
![Landing Page](screenshots/landing-page.png)
*The main landing page with navigation and feature overview*

### Career Quiz
![Career Quiz](screenshots/career-quiz.png)
*Interactive quiz to assess career preferences*

### Job Search
![Job Search](screenshots/job-search.png)
*Job search interface with filters and results*

### Career Recommendations
![Career Recommendations](screenshots/recommendations.png)
*Personalized career suggestions based on quiz results*

### Career Roadmap
![Career Roadmap](screenshots/career-roadmap.png)
*Detailed career progression path with milestones*

## Architecture Diagram

```mermaid
graph TB
    A[User Browser] --> B[Express Server]
    B --> C[PostgreSQL Database]
    B --> D[JSearch API]
    B --> E[Static Files]

    subgraph "Frontend"
        F[index.html]
        G[auth.html]
        H[quiz.html]
        I[jobs.html]
        J[recommendation.html]
        K[roadmap.html]
    end

    subgraph "Backend"
        L[server.js]
        M[Authentication Routes]
        N[Job Search Routes]
        O[Quiz Processing]
    end

    subgraph "Database"
        P[users table]
        Q[session data]
    end

    B --> F
    B --> G
    B --> H
    B --> I
    B --> J
    B --> K
    L --> M
    L --> N
    L --> O
    C --> P
    C --> Q
```

## User Flow Diagram

```mermaid
flowchart TD
    A[User Visits Site] --> B[Landing Page]
    B --> C[Click 'Start Career Quiz']
    C --> D[Authentication Required]
    D --> E[Login/Signup]
    E --> F[Take Career Quiz]
    F --> G[Submit Quiz Answers]
    G --> H[View Career Recommendations]
    H --> I[Explore Career Roadmap]
    I --> J[Search Jobs]
    J --> K[Compare Careers]
    K --> L[Build Resume]

    M[Direct Access] --> N[Job Search]
    N --> O[Career Comparison]
    O --> P[Resume Builder]
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Troubleshooting

### Common Issues

1. **Database Connection Error:**
   - Ensure PostgreSQL is running
   - Check database credentials in `.env` file
   - Verify user permissions on database

2. **API Key Issues:**
   - Register for JSearch API at RapidAPI
   - Update `RAPIDAPI_KEY` in environment variables

3. **Port Already in Use:**
   - Change PORT in `.env` file
   - Kill process using the port: `npx kill-port 3000`

## License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## Contact

**Sachin Naik**
- GitHub: [@ssachinnaik](https://github.com/ssachinnaik)
- Repository: [https://github.com/ssachinnaik/quiz-career-guidance](https://github.com/ssachinnaik/quiz-career-guidance)

---

*Built with ❤️ for career guidance and professional development*
