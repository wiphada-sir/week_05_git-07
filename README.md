# DevTeam Hub

A team portfolio site for JSD Cohort 12. Built to practice Git collaboration.

---

## Before you start

Follow the [Setup Guide](SETUP.md) first. Come back here once your repo is cloned and your team has assigned member numbers.

---

## Exercise 1 — Feature branches (no conflicts)

**Goal:** Everyone practises the full branch → commit → push → PR workflow without merge conflicts.

Each team member edits their own clearly marked section in `index.html`, so your changes will not clash with anyone else's.

---

### What you will do

Each member adds their profile card directly into `index.html`.

---

### Steps

**1. Make sure your local `main` is up to date.**

```bash
git checkout main
git pull upstream main
```

**2. Create your feature branch.**

Replace `1` with your member number.

```bash
git checkout -b feature/add-member-1-card
```

**3. Edit your section in `index.html`.**

Open `index.html` and find the comment for your member number:

```html
<!-- MEMBER 1: Replace this placeholder with your card -->
```

Delete the entire grey placeholder `<div>` below that comment and replace it with your own card using this structure:

```html
<div
  class="bg-gray-800 rounded-xl p-6 text-center border border-gray-700 team-card"
>
  <img
    src="YOUR_IMAGE_URL"
    alt="YOUR_NAME"
    class="w-16 h-16 rounded-full mx-auto mb-4 object-cover bg-gray-600"
    onerror="this.src='https://api.dicebear.com/7.x/pixel-art/svg?seed=fallback'"
  />
  <p class="font-semibold text-white text-lg">YOUR_NAME</p>
  <p class="text-indigo-400 text-sm mb-3">YOUR_ROLE</p>
  <p class="text-gray-400 text-sm mb-4 italic">"YOUR_FUN_FACT"</p>
  <a
    href="YOUR_GITHUB_URL"
    target="_blank"
    class="text-xs text-indigo-400 hover:underline"
    >GitHub Profile &rarr;</a
  >
</div>
```

Fill in your details:

- `Your Name Here` → your real name
- `Student Developer` → your role or something fun (e.g. "CSS Wizard", "Bug Hunter")
- The fun fact string → something true about you
- The GitHub URL → your real GitHub profile URL
- The image `src` → a photo URL, or keep the default pixel art avatar

**4. Test it locally.**

Open `index.html` in your browser. You should see your card in the team grid.

**5. Commit your changes.**

```bash
git add index.html
git commit -m "add profile card for Your Name"
```

**6. Push your branch to your fork.**

```bash
git push origin feature/add-member-1-card
```

**7. Open a Pull Request.**

1. Go to your fork on GitHub.
2. Click **Compare & pull request**.
3. Set the base repo to the **Team Lead's repo**, base branch `main`.
4. Write a short description of what you changed.
5. Submit the PR.

**8. Team Lead: review and merge each PR.**

Team Lead reviews each PR and merges them one by one into `main`.

---

### What to notice

- Because each member only edits their own numbered section, **no two PRs touch the same lines**. GitHub merges them cleanly with no conflicts.
- This is the ideal workflow for a team: divide work so changes don't overlap.

---

## Exercise 2 — Feature branches (with conflicts)

**Goal:** Everyone experiences a real merge conflict and learns to resolve it.

This time you will all edit the **same file at the same location**. Conflicts are guaranteed.

---

### Important: Do NOT pull `main` before you start

This feels wrong — but it is intentional. On a real team, two people often start working at the same time without knowing the other person is editing the same file. We are recreating that situation on purpose.

---

### What you will do

Each member adds their personal project to the project board in `data/projects.js`.

---

### Steps

**1. Create a new feature branch from your current `main`.**

```bash
git checkout main
git checkout -b feature/add-project-member-1
```

(Use your member number.)

**2. Open `data/projects.js` and add your project entry.**

Add a new object at the **very top of the array**, right after the `[` and the comment block. Copy the existing entry as a template:

```javascript
const projects = [
  // ADD YOUR ENTRY HERE
  {
    member: "Your Name",
    project: "Your Project Name",
    description: "One sentence about what you are building.",
    status: "in-progress",
    github: "https://github.com/yourusername/your-repo"
  },

  // existing entries below...
```

**3. Save, test, commit, and push.**

```bash
# Open index.html in a browser and check the project board shows your entry
git add data/projects.js
git commit -m "add project entry for Your Name"
git push origin feature/add-project-member-1
```

**4. Open a Pull Request** to the Team Lead's `main` (same as Exercise 1).

**5. Team Lead: merge the first PR.**

Merge one person's PR. Leave the rest open.

---

### Resolving the conflict

Everyone whose PR was NOT merged first will now have a conflict. Here is how to fix it.

**Step A — Pull the updated `main` into your branch.**

```bash
git checkout main
git pull upstream main
git checkout feature/add-project-member-1
git merge main
```

Git will tell you there is a conflict in `data/projects.js`.

**Step B — Open the file and look for conflict markers.**

```
<<<<<<< HEAD
  {
    member: "Your Name",
    ...
  },
=======
  {
    member: "Other Person",
    ...
  },
>>>>>>> main
```

**Step C — Resolve the conflict.**

Keep **both** entries. Delete the `<<<<<<<`, `=======`, and `>>>>>>>` lines. The result should be two (or more) objects in the array, comma-separated.

**Step D — Stage and commit the resolution.**

```bash
git add data/projects.js
git commit -m "resolve merge conflict in projects.js"
```

**Step E — Push and update your PR.**

```bash
git push origin feature/add-project-member-1
```

Your PR on GitHub will update automatically. Team Lead can now merge it.

---

### What to notice

- Merge conflicts look scary but they are just Git asking: "Both of you changed this spot — which version is correct?"
- The answer is often "both" — you keep everyone's changes and remove the markers.
- After resolving, always open the file in a browser to confirm everything still works before pushing.
