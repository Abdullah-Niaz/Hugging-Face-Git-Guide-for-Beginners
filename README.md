# Hugging Face Git Guide for Beginners

Hugging Face lets you store **Models, Datasets, and Spaces** on the cloud. You can interact with these using **Git** for version control. Since passwords are no longer allowed, you must use a **Personal Access Token (PAT)** or **SSH keys**.

---

## 1. Prerequisites

1. Install [Git](https://git-scm.com/downloads) on your computer.
2. Create a Hugging Face account.
3. Generate a **Personal Access Token (PAT)**:

   * Go to **Settings → Access Tokens → New Token**
   * Select **Write** permission (for push/pull)
   * Copy and save your token securely.

---

## 2. Types of Hugging Face Repositories

* **Model Repo:** `https://huggingface.co/<username>/<model-name>`
* **Dataset Repo:** `https://huggingface.co/datasets/<username>/<dataset-name>`
* **Space Repo:** `https://huggingface.co/spaces/<username>/<space-name>`

> Spaces are used for live apps (Streamlit, Gradio, etc.)

---

## 3. Cloning a Repo (Pulling Down)

To get a copy of a remote Hugging Face repo:

**HTTPS method with token:**

```bash
git clone https://<username>:<token>@huggingface.co/spaces/<username>/<repo-name>
```

Example:

```bash
git clone https://abdullahniaz:yourtokenhere@huggingface.co/spaces/abdullahniaz/my-space
```

This downloads the repo to your local machine.

---

## 4. Adding Your Local Project to Hugging Face

If you have a folder locally that you want to push:

1. Navigate to the folder:

```bash
cd /path/to/your/project
```

2. Initialize Git (if not done):

```bash
git init
```

3. Add your remote repository:

```bash
git remote add origin https://<username>:<token>@huggingface.co/spaces/<username>/<repo-name>
```

4. Stage and commit your files:

```bash
git add .
git commit -m "Initial commit"
```

---

## 5. Pushing Changes to Hugging Face

Push your local changes to the remote repo:

```bash
git push origin main
```

> Replace `main` with your branch name if different.

* On first push, Git may ask for credentials:

  * **Username:** your Hugging Face username
  * **Password:** your personal access token

---

## 6. Pulling Updates from Hugging Face

If someone else updated the repo, or you want to sync your local copy:

```bash
git pull origin main
```

This fetches the latest changes from Hugging Face.

---

## 7. Updating Remote URLs

If your token changes, or you switch to SSH:

**HTTPS with new token:**

```bash
git remote set-url origin https://<username>:<new-token>@huggingface.co/spaces/<username>/<repo-name>
```

**SSH (recommended for frequent use):**

```bash
git remote set-url origin git@hf.co:spaces/<username>/<repo-name>
```

* SSH doesn’t require a token every push.

---

## 8. Tips for Beginners

* Always commit with clear messages:

  ```bash
  git commit -m "Update model weights"
  ```
* Use `.gitignore` to exclude large files you don’t want to track.
* Use `git status` to check changes before pushing.
* Spaces automatically deploy apps when you push changes.

---

## Quick Command Reference

| Action            | Command                                                      |
| ----------------- | ------------------------------------------------------------ |
| Clone repo        | `git clone https://<username>:<token>@huggingface.co/<repo>` |
| Add remote        | `git remote add origin <url>`                                |
| Stage files       | `git add .`                                                  |
| Commit changes    | `git commit -m "message"`                                    |
| Push changes      | `git push origin main`                                       |
| Pull changes      | `git pull origin main`                                       |
| Change remote URL | `git remote set-url origin <url>`                            |

---

This gives beginners a clear workflow for **pulling, pushing, and updating** repositories on Hugging Face using Git with HTTPS tokens or SSH.
