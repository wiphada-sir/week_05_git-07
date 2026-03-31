# Setup Guide

Follow these steps **in order** before starting any exercises.

---

## Step 1 — Team Lead: Clone and reset the git history

One person on the team is the **Team Lead**. Everyone else skips to Step 2.

```bash
# Clone the instructor's starter repo
git clone <INSTRUCTOR_REPO_URL> devteam-hub
cd devteam-hub

# Delete the original git history
rm -rf .git

# Start a fresh git history
git init
git add .
git commit -m "initial commit"
```

Then create a new repo on your GitHub account (name it `devteam-hub`), and push:

```bash
git remote add origin https://github.com/<YOUR_USERNAME>/devteam-hub.git
git branch -M main
git push -u origin main
```

Share your GitHub repo URL with your team.

---

## Step 2 — All other members: Fork the Team Lead's repo

1. Open the Team Lead's repo URL in your browser.
2. Click the **Fork** button (top right on GitHub).
3. Fork it to your own GitHub account.
4. Clone **your fork** to your machine:

```bash
git clone https://github.com/<YOUR_USERNAME>/devteam-hub.git
cd devteam-hub
```

5. Add the Team Lead's repo as an upstream remote so you can pull their updates later:

```bash
git remote add upstream https://github.com/<TEAM_LEAD_USERNAME>/devteam-hub.git
```

6. Confirm your remotes are set up correctly:

```bash
git remote -v
# You should see two remotes:
# origin    https://github.com/<YOUR_USERNAME>/devteam-hub.git
# upstream  https://github.com/<TEAM_LEAD_USERNAME>/devteam-hub.git
```

---

## Step 3 — Everyone: Assign member numbers

Before starting the exercises, decide as a team who is Member 1 through Member 6.
Write it down somewhere your whole team can see it.

| Member # | Name   |
| -------- | ------ |
| Member 1 | **\_** |
| Member 2 | **\_** |
| Member 3 | **\_** |
| Member 4 | **\_** |
| Member 5 | **\_** |
| Member 6 | **\_** |

Your member number tells you which section is yours in `index.html`.

---

You're ready. Move on to [Exercise 1](README.md#exercise-1--feature-branches-no-conflicts).
