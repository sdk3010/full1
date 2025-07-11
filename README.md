# Weather Wise News Hub

Weather Wise News Hub is a full-stack application that provides real-time weather updates and a personalized news feed. Users can view weather for their current location, popular cities, and access news articles. The application also features user authentication with protected routes for a personalized experience.

## Features

- **Real-time Weather:** Get current weather conditions for your approximate location (requires geolocation enabled and running on `localhost` or HTTPS).
- **Popular Cities Weather:** Displays weather for pre-defined cities like New Delhi and Tokyo.
- **Location Search:** Search for weather in any city and navigate to the weather dashboard.
- **News Feed:** View the latest news articles from various sources.
- **User Authentication:**
  - **Sign Up:** Create a new user account.
  - **Login:** Authenticate to access personalized features.
  - **Logout:** Securely log out of your account.
- **Protected Routes:** Access to Weather Board, News Board, and Profile sections requires authentication.
- **User Preferences:** Customize temperature units, auto-refresh intervals, notifications, and language (preferences saving is a placeholder for now).

## Technologies Used

**Frontend:**
- React
- TypeScript
- Vite
- Tailwind CSS (with Shadcn UI components)
- React Router DOM
- React Query

**Backend:**
- Node.js
- Express.js
- MongoDB (with Mongoose)
- JSON Web Tokens (JWT) for authentication
- bcryptjs for password hashing
- dotenv for environment variable management

**APIs:**
- OpenWeatherMap API for weather data
- NewsData.io API for news articles

## Getting Started

Follow these instructions to set up and run the project locally.

### Prerequisites

- Node.js (v18 or higher) and npm (or Bun)
- MongoDB instance (local or cloud-based like MongoDB Atlas)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-repo/weather-wise-news-hub.git
    cd weather-wise-news-hub
    ```

2.  **Backend Setup:**
    Navigate to the `server` directory:
    ```bash
    cd server
    ```
    Install backend dependencies:
    ```bash
    npm install # or bun install
    ```
    Create a `.env` file in the `server` directory with the following content:
    ```
    MONGO_URI=your_mongodb_connection_string_here
    JWT_SECRET=your_super_secret_jwt_key_here
    PORT=5000 # or any other port
    ```
    - Replace `your_mongodb_connection_string_here` with your actual MongoDB connection string (e.g., from MongoDB Atlas).
    - Replace `your_super_secret_jwt_key_here` with a strong, random string. This is crucial for JWT token generation.

    Start the backend server:
    ```bash
    npm start # or bun run start (if you have a start script)
    ```
    (Note: You might need to add a `start` script to `server/package.json` like `"start": "node index.js"`)

3.  **Frontend Setup:**
    Navigate back to the project root directory:
    ```bash
    cd ..
    ```
    Install frontend dependencies:
    ```bash
    npm install # or bun install
    ```
    Ensure your API keys are correctly configured in `src/pages/Home.tsx` and `src/components/news/NewsSection.tsx`:
    - `OPENWEATHER_API_KEY`: Get this from [OpenWeatherMap](https://openweathermap.org/api).
    - `NEWS_API_KEY`: Use `pub_016a6fe6473f4a8b9cc5f7ef2a5a6ee2` (from NewsData.io) or obtain your own from [NewsData.io](https://newsdata.io/).

    Start the frontend development server:
    ```bash
    npm run dev # or bun dev
    ```

## Important Notes

- **Geolocation:** Browser geolocation API only works when the application is served over HTTPS or from `localhost`. Please run your frontend on `localhost` during development for this feature to work.
- **Backend API:** The backend server must be running for authentication and other server-dependent features to function correctly.
- **News API Limitations:** The NewsData.io free plan might have limitations on the number of requests or features (e.g., `content` field often returns "ONLY AVAILABLE IN PAID PLANS" as seen in your provided sample).

## Troubleshooting

- If you encounter a "500 Internal Server Error" during login/signup, ensure your `JWT_SECRET` and `MONGO_URI` are correctly set in the `server/.env` file and that your MongoDB instance is accessible.
- If the page is blank or components are not rendering, check your browser's console for JavaScript errors. Ensure all dependencies are installed and the `ThemeProvider` is correctly set up.
