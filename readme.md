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

Open file `group.txt` and write your name on first line.
    ```
     git add 
     git commit -m "Add <yourname>'s name"
     git push origin main
     ```

     example:
    ```
     git add 
     git commit -m "Add Khoa's name"
     git push origin main
    ```

    *There should be error from the second try.*

    So how to fix this?

#### **Method 1: Pull Then Push**

1. **Identify the conflict**  
   When a member tries to push changes without pulling the latest updates, they will encounter an error:
   ```bash
   ! [rejected] main -> main (non-fast-forward)
   error: failed to push some refs to '<remote-repository-url>'
   ```

2. **Pull the latest changes from the remote repository**  
   Run the following command:
   ```bash
   git pull origin main
   ```
   - Git will attempt to merge the changes automatically.
   - If there is a conflict in `group.txt`, Git will notify you and mark the conflict in the file.

3. **Manually resolve the conflict**  
   Open the `group.txt` file, and you'll see something like this:
   ```plaintext
   <<<<<<< HEAD
   Khoa's name
   =======
   Another member's name
   >>>>>>> 123abc456def
   ```
   - **Edit the file** to resolve the conflict. For example:
     ```plaintext
     Khoa's name
     Another member's name
     ```

4. **Stage the resolved file and commit**  
   ```bash
   git add group.txt
   git commit -m "Resolve conflict in group.txt"
   ```

5. **Push the resolved changes to the remote repository**  
   ```bash
   git push origin main
   ```

---

#### **Method 2: Use Branching**

This method avoids conflicts by allowing each member to work in their own branch and merge changes into the `main` branch.

1. **Create a new branch for your changes**  
   ```bash
   git checkout -b <yourname>
   ```
   Replace `<yourname>` with your name.

2. **Make changes in your branch**  
   Open the `group.txt` file, add your name, and save it.

3. **Stage and commit your changes**  
   ```bash
   git add group.txt
   git commit -m "Add <yourname>'s name"
   ```

4. **Push your branch to the remote repository**  
   ```bash
   git push origin <yourname>
   ```

5. **Create a pull request on GitHub**  
   - Go to your GitHub repository in your browser.
   - Click on the **Pull requests** tab.
   - Click **New pull request** and choose your branch.
   - Review the changes and submit the PR.

6. **Merge the pull request**  
   - After a review, merge the pull request into the `main` branch.
   - If there is a conflict, GitHub will notify you, and you can resolve it through the web interface or locally.

7. **Pull the latest changes to your local `main` branch**  
   ```bash
   git checkout main
   git pull origin main
   ```