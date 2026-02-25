# Fixing Up a House Interactive Fiction Game

A browser based interactive fiction game with beat driven progression, choices, inventory, and clue logging. Everything runs from a single HTML file.

## Run

Option 1: Open the file directly
1. Double click `fixing_house_beat1_game.html` (or your renamed copy).
2. If you edited beat keys recently, click **Reset save** in the UI after the page loads.

Option 2: Run a local server (recommended for iteration)
1. Install Node.js.
2. In the folder with the HTML file, run:
   ```bash
   npx http-server . -p 5173
   ```
3. Open http://localhost:5173/fixing_house_beat1_game.html

## Controls

New run resets in memory state and starts at Beat 1.1.

Save writes the current state to localStorage.

Load restores the last saved state from localStorage.

Reset save clears the stored state in localStorage.

Actor notes toggles the display of notes[].

Typewriter toggles progressive text rendering.

## Beat Schema

Each beat is an entry in const beats = { ... } with this structure:

"X.Y": {
  title: "Beat Title",
  loc: "Location",
  time: "Time of day",
  text: [
    "Line 1. Keep each line 1 to 2 sentences.",
    "Line 2."
  ],
  notes: [
    "[AMANDA: Actor facing note. Optional.]"
  ],
  choices: [
    { t: "Choice text", next: "Next.Beat", fx: (s) => { s.trust += 1; } },
    { t: "Choice text", next: "Other.Beat", fx: (s) => { s.unease += 1; } }
  ],
  hint: "Optional hint text"
}

## Rules used in this project

Keep story text literal. Avoid meta labels such as door IDs.

Prefer 2 choices per beat unless a beat intentionally ends.

Every choices[].next must point to an existing beat key, or be null to end.

## Adding Beats Safely

Pick a key, for example 4.7.

Add the new beat object anywhere inside const beats = { ... }.

Update a previous beat choice to point to it via next: "4.7".

Verify syntax:

Every beat object ends with },

Every array entry ends with a comma when followed by another entry

Strings use matching quotes

Verify links:

Search for next: and confirm every referenced beat exists

Refresh and click through the path that reaches the new beat.

If the game jumps to an unexpected beat, click Reset save.

## Troubleshooting

If the page stays on "Loading…"

Open DevTools Console (F12).

Look for a red syntax error pointing to a line number.

Common causes:

Missing comma between beats

Unclosed quote in text[] or notes[]

A beat key referenced in next does not exist

If clicking a choice does nothing

Check the console for Cannot read properties of undefined or similar.

That usually means next points to a missing beat key.

If Save and Load behave oddly after edits

Click Reset save.

Refresh the page.

## Project Structure

fixing_house_beat1_game.html main game file with embedded CSS and JS.

README.md usage and development notes.

.github/copilot-instructions.md editing rules for assistants.

CHANGELOG.md optional version history.

## Development Notes

No build step is required.

Use DevTools Console for errors and state inspection.

Prefer a local server while editing for faster refresh and cleaner debugging.