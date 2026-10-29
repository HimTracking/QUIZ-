# QuizArena — Windows setup and run guide

QuizArena is a real-time classroom quiz app with a styled landing page, admin dashboard, PIN rooms, timed multiple-choice questions, scoring, answer review, and leaderboard.

## Requirements
- Node.js 22 or newer (including Node.js 26)
- Internet connection for the first dependency install
- Windows: use `start.bat`, or the commands below in Command Prompt

## Start on Windows
1. Extract the ZIP fully (do not run from inside the ZIP preview).
2. Open the extracted `QuizArena` folder in VS Code. The folder should contain `package.json` and `server.js`.
3. Open **Terminal → New Terminal**. Command Prompt is recommended if PowerShell blocks `npm.ps1`.
4. Run `npm install`. This project uses Node's built-in `node:sqlite`, so no native SQLite addon needs compiling.
5. Run `npm start`.
6. Open `http://localhost:3000` for the student homepage and `http://localhost:3000/admin` for the host dashboard.

Alternatively, double-click `start.bat`. Keep its terminal window open while using the website.

## Demo admin credentials
- Email: `admin@quizarena.local`
- Password: `ChangeMe123!`

Change these values in `.env` before any public deployment.

## Fix if you previously ran npm install and it failed
Close the running server. In Command Prompt, change directory to this project folder, then run:

```bat
rmdir /s /q node_modules
del package-lock.json
npm install
npm start
```

If `node:sqlite` prints an experimental warning on your Node version, it is a warning; the app can still start.

## Notes
- Database file: `quizarena.db` in the project folder.
- The server-authoritative timer continues after a browser refresh.
- A player nickname can only submit one attempt per room.
- Before public deployment, use HTTPS, strong credentials and session secret, rate limiting, and persistent storage.
- This is a classroom/demo starter; not every optional feature in the original brief (question bank randomization, shuffled options, full analytics dashboard) is implemented yet.
