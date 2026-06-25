# Session Close Procedure

Before running '/clear' (or ending the session), please perform the following steps:

1. Update the session log:
   - Open `session_log.md`.
   - Find the row for the current session (the latest row).
   - Set the **End Time** to the current UTC timestamp (run `date +"%Y-%m-%d %H:%M:%S"` in terminal).
   - Update the **Brief Summary** with a concise description of what was accomplished in this session.

2. Update the activity log:
   - Append a new line to `activity.log` in the format:
     `[YYYY-MM-DD HH:MM:SS] <brief description of changes>`
   - Use the same timestamp as the session end time.

3. Commit and push changes:
   - Stage all modified files (`git add -A`).
   - Commit with a clear message summarizing the session (e.g., `feat: update session log and activity log for session 1`).
   - Push **only** to the `main` branch: `git push origin main`.

4. Verify:
   - Ensure the push succeeded and the GitHub Pages site updates (if applicable).
   - Confirm that `session_log.md` and `activity.log` reflect the latest session.

5. Only after completing the above steps, run '/clear' to clear the conversation context.

Following this procedure ensures a persistent activity log and session history across sessions, even after clearing the context.