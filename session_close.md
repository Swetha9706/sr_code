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

4. Verify the GitHub Pages deployment (MANDATORY — do not skip):

   GitHub Pages legacy builds sometimes fail silently ("Page build failed") and the site serves a 404 even though the push succeeded. Every push to `main` MUST be followed by this verification loop:

   a. Wait ~30–60 seconds after the push, then check the latest Pages build status:
      ```sh
      TOKEN=$(git remote get-url origin | sed -E 's|https://([^@]+)@.*|\1|')
      curl -sS -H "Authorization: token $TOKEN" \
        "https://api.github.com/repos/Swetha9706/sr_code/pages/builds/latest"
      ```
      Confirm that `"commit"` matches the SHA just pushed (`git rev-parse HEAD`).

   b. If `"status"` is `queued` or `building`, wait 15 seconds and check again. Repeat until it reaches a final state.

   c. If `"status"` is `"errored"`, trigger a fresh build and go back to step (a):
      ```sh
      curl -sS -X POST -H "Authorization: token $TOKEN" \
        -H "Accept: application/vnd.github+json" \
        "https://api.github.com/repos/Swetha9706/sr_code/pages/builds"
      ```
      Repeat this retrigger-and-recheck loop until the build reports `"built"` (a manual retrigger has resolved every failure so far). If it still errors after 3 retriggers, inspect the repo for oversized files (>100 MB), symlinks, or invalid filenames before retrying.

   d. Once the build reports `"built"`, verify the live site actually serves the new content:
      ```sh
      curl -sS -o /dev/null -w "%{http_code}\n" "https://swetha9706.github.io/sr_code/"
      ```
      This must return `200` (not `404`). Spot-check at least one recently changed page the same way.

   - Do NOT consider the session closed while the latest Pages build is `errored` or the live site returns `404`.
   - Confirm that `session_log.md` and `activity.log` reflect the latest session.

5. Only after completing the above steps, run '/clear' to clear the conversation context.

Following this procedure ensures a persistent activity log and session history across sessions, even after clearing the context.