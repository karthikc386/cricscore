# CricScore - Simple Web-Based Cricket Scorer

CricScore is a single-page web application designed for manually scoring cricket matches directly in your browser. It provides a clean interface for tracking runs, wickets, overs, and various types of extras ball-by-ball. It now includes session persistence via local storage and a proper undo function.

## Features

*   **Score Tracking:** Displays the current score (Runs/Wickets), overs bowled, and run rate.
*   **Ball-by-Ball Entry:** Record each delivery with dedicated buttons.
*   **Event Types:** Supports common cricket events:
    *   Dot Ball
    *   Runs (0-6, plus custom values)
    *   Wickets (with optional runs scored off the same delivery)
    *   Wides (with optional extra runs)
    *   Byes (with optional runs)
    *   Leg Byes (with optional runs)
    *   No-balls (with optional runs scored off the bat or as byes/leg byes)
    *   Penalty Runs
*   **Complex Events:** Handles combined events like Wicket+Wide, Wicket+No-ball, No-ball+Bye, etc.
*   **Over Management:** Automatically groups deliveries into overs and prompts for a new bowler at the start of each over.
*   **Bowler Tracking:**
    *   Requires assigning a bowler to each over via a modal.
    *   Allows adding new bowler names on the fly.
    *   Remembers previously entered bowler names for easy selection.
*   **Free Hit Indication:** Visually marks the next legitimate delivery after a No-ball as a Free Hit (using a border).
*   **History View:** Option to show all previous overs or hide them to focus on the current and last over.
*   **Undo Last Action:** Reverts the last recorded ball/event using a history stack.
*   **Reset Match:** Clears the current score and starts fresh (requires confirmation).
*   **Session Persistence:** Automatically saves the scoring progress using browser Local Storage, allowing you to close and reopen the browser without losing data (within the same browser).
*   **Responsive Design:** Uses Bootstrap 5 for a layout that adapts to different screen sizes.
*   **Offcanvas Menu:** Includes a basic side menu structure (links are currently placeholders).

## How to Use

1.  **Open the File:** Simply download the `index.html` file and open it in your preferred web browser (like Chrome, Firefox, Edge, Safari). No web server is required.
2.  **Resume Session (Optional):** If you previously used the scorer in the same browser, it will attempt to load your last session automatically.
3.  **Set Bowler:** At the start of the match (or a new over), click the "Set Bowler" button. Select an existing bowler from the dropdown or click "Add New Bowler" to enter a name, then click "Save". You must set a bowler before recording the first legitimate ball of an over.
4.  **Record Deliveries:**
    *   Click "Dot" for a dot ball.
    *   Click "Run", "Wicket", "Wide", "Bye", "Leg Bye", "No-ball", or "Penalty".
    *   A modal will pop up asking you to select the number of runs/extras associated with that event (e.g., how many runs for a "Run" event, how many wides for a "Wide" event).
    *   For Wickets and No-balls, the modal also provides options to record combined events (like Wicket+Wide).
    *   Select a preset value button or enter a custom value (if allowed for that event) and click "Add".
5.  **View Score:** The main score header (`Runs/Wickets (Overs.Balls, R.R RunRate)`) and the balls remaining display update automatically.
6.  **Over Completion:** After 6 legitimate deliveries (runs, wickets, byes, leg byes), the system automatically starts the next over and prompts you to set the bowler. Wides and No-balls do not count towards the 6 balls in the over.
7.  **History:** Click "Show History" to view all bowled overs. Click "Hide History" to collapse the view to only the last two overs.
8.  **Undo:** Click the "Undo" button to revert the *last* action (e.g., remove the last ball added). You can undo multiple actions sequentially.
9.  **Reset:** Click the "Reset" button to clear all scoring data and start a new match (you will be asked for confirmation).
10. **Persistence:** Your progress is automatically saved in your browser's local storage after each ball. Closing and reopening the tab/browser should restore the state.

## Technology Stack

*   **HTML5:** Structure of the web page.
*   **CSS3:** Styling (primarily via Bootstrap).
*   **Bootstrap 5:** Front-end framework for UI components (Navbar, Modals, Buttons, Grid Layout) and responsive design.
*   **JavaScript (Vanilla):** Handles all the application logic, state management, event handling, and DOM manipulation.
*   **Browser Local Storage API:** Used for saving and restoring the scoring session.

## Known Issues / Limitations

*   **Persistence Limitations:** Data is stored only in the browser's local storage. Clearing browser data, using a different browser, or using incognito/private browsing mode will lose the saved session.
*   **Limited Player Management:** Only tracks the bowler's name for each over. Does not track batsmen, fielding team, etc.
*   **No Match Setup:** Does not include features for setting up teams, innings, target scores, etc.
*   **Placeholder Menu:** The offcanvas menu links (Profile, Settings, etc.) are not functional.
*   **Undo Granularity:** Undo works on a per-ball basis. Setting a bowler is not currently undoable via the button (though loading the previous state effectively undoes it).

## Future Improvements (Potential)

*   Add tracking for batsmen (on strike/off strike) and their individual scores.
*   Implement full match setup options (teams, players, innings, target).
*   Add more detailed statistics (e.g., bowler figures, partnership scores).
*   Allow editing of previous balls/overs.
*   Implement session export/import functionality.
*   Refine the UI/UX.
