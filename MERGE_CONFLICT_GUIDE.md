# Resolving the GitHub Pages workflow merge conflict

When you attempt to merge the deployment branch into `main`, Git will pause because the same lines were modified in both branches. You can resolve the conflict without rewriting the workflow by following these steps:

1. **Confirm you are on the branch you want to merge _into_.**
   ```bash
   git status
   ```
   Make sure it says `On branch main` (or whatever branch you are updating).

2. **Start the merge and let Git mark the conflict.**
   ```bash
   git merge <name-of-deployment-branch>
   ```
   Git will stop and mark the conflicting files (shown in the screenshots you provided).

3. **Open `.github/workflows/deploy.yml` in your editor.**
   - You will see the conflict markers:
     ```yaml
     <<<<<<<
     with:
       enablement: enabled
     =======
     # incoming block
     >>>>>>>
     ```
   - Decide which version you want to keep:
     * Keep the `with: enablement: enabled` block if you want the workflow to automatically enable Pages during the first run.
     * Otherwise remove the entire block if you prefer to manage the setting manually.
   - Delete the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and any duplicate lines you do not want.

4. **Open `README.md` and resolve its conflict.**
   - Choose the text you prefer (either the original bullet point or the updated explanation about automatic enablement).
   - Remove the conflict markers just like in the workflow file.

5. **Mark the conflicts as resolved and finish the merge.**
   ```bash
   git add .github/workflows/deploy.yml README.md
   git merge --continue
   ```
   If `git merge --continue` reports that there is nothing to commit, run `git commit` instead.

6. **Push the merged result.**
   ```bash
   git push origin main
   ```

These steps keep your existing logic intact; you only choose which version of the conflicting lines to keep.
