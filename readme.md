## Git/GitHub Remoting Practice

### Step 1: Create a New GitHub Repository and Add Members

*Note: Only one person in the group needs to do this step.* 
1. **Create a new repository on GitHub**
   - Go to [GitHub](https://github.com/).
   - Click on the **New** button to create a new repository.
   - Name your repository (e.g., `gdsc-git-practice`).
   - Set it to **Private** or **Public**, as preferred.
   - Do not initialize it with a `README.md`.

2. **Add your group members as collaborators**  
   - Go to **Settings** > **Collaborators and teams** > **Add people**.
   - Invite your group members by their GitHub usernames or email addresses.

---

### Step 2: Change the Remote URL and Push Again

1. **Check the current remote URL**  
   ```bash
   git remote -v
   ```

2. **Change the remote URL to your new repository**  
   Replace `<https://github.com/dkhoa2906/TP2024.git>` with your new GitHub repository HTTPS link
   ```bash
   git remote set-url origin <https://github.com/dkhoa2906/TP2024.git>
   ```

3. **Push your changes to the new repository**  
   ```bash
   git push -u origin main
   ```
   > Your changes should successfully be pushed to your new repository.

---

### Step 3: Simulate a Conflict Scenario

1. 

2. **Steps for Person A**:  
   - Modify the file (e.g., add a line saying "Hello from A").
   - Stage, commit, and push the changes:
     ```bash
     git add README.md
     git commit -m "Person A changes README.md"
     git push
     ```

3. **Steps for Person B**:  
   - Pull the latest changes to ensure their local branch is up-to-date:
     ```bash
     git pull origin main
     ```
     - Make changes to the same file (e.g., add "Hello from B").
     - Stage and commit:
       ```bash
       git add README.md
       git commit -m "Person B changes README.md"
       ```
     - Try to push:
       ```bash
       git push
       ```
     > **Expected conflict error**:
     > ```bash
     > ! [rejected] main -> main (non-fast-forward)
     > error: failed to push some refs to '<remote-repository-url>'
     > ```

4. **Resolve the conflict**:  
   - Person B should pull the latest changes:
     ```bash
     git pull origin main
     ```
   - Git will notify you of the conflict. Open the conflicted file to resolve it manually.
   - After resolving, stage the file and commit:
     ```bash
     git add README.md
     git commit -m "Resolve conflict in README.md"
     ```
   - Push the changes:
     ```bash
     git push
     ```

---

### Tips for Team Collaboration
- **Communicate**: Always communicate changes with your team to minimize conflicts.
- **Branching**: Use separate branches for feature development, and merge into the main branch after review.
- **Pull Regularly**: Frequently pull the latest changes to stay updated.

Would you like additional details on any step?