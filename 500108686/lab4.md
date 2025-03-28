lab 4:


# **GIT Branching / Merge / Rebase**

## 1. **Creating Directories and Files:**

- **`mkdir project`**: Creates a `project` directory.
- **`cd project`**: Navigates into the `project` directory.
- **`mkdir src`**: Creates a `src` directory inside the `project` directory.
- **`touch README.md`**: Creates a `README.md` file.
- **`touch z.txt`**: Creates a `z.txt` file in `featureA` branch.
- **`touch x.txt`**: Creates a `x.txt` file in `featureA` branch.
- **`touch s.txt`**: Creates a `s.txt` file in `main` branch.

## 2. **Working with Files:**

- **`echo "Hello World" >> README.md`**: Adds "Hello World" to `README.md`.
- **`echo "content" >> README.md && cat README.md`**: Appends content to `README.md` and displays it:
  
  ```
  Hello World 1
  content
  ```
  
- **`echo -e "hello \n me"`**: Correctly prints the string with a newline:
  
  ```
  hello
  me
  ```
  
- **`echo "Hello World 1" > README.md`**: Rewrites `README.md` with "Hello World 1".

## 3. **Git Commands:**

- **`git init`**: Initializes a new Git repository.
- **`git remote -v`**: Displays remote repositories (none added here).
- **`git status`**: Shows the status of files in the repository.
- **`git add .`**: Stages all changes in the directory.
- **`git commit -m "message"`**: Commits staged changes with a message.
- **`git log`**: Displays commit history.

## 4. **Branching and Switching:**

- **`git branch`**: Lists branches in the repository.
- **`git branch -M main`**: Renames the current branch to `main`.
- **`git checkout featureA`**: Switches to the `featureA` branch.
- **`git branch featureA`**: Creates a `featureA` branch.
- **`git checkout -b featureB`**: Creates and switches to `featureB`.
- **`git checkout main`**: Switches to the `main` branch.

## 5. **Git Operations:**

- **`git reset --soft <commit>`**: Resets to a previous commit without changing the working directory.
- **`git rebase main`**: Rebases the `featureA` branch onto the `main` branch.
- **`git merge featureB`**: Merges the `featureB` branch into the `main` branch.
- **`git reset --hard <commit>`**: Resets the working directory and commit history to a specific commit.
- **`git merge --squash featureB`**: Squashes all the commits from `featureB` into a single commit without updating the HEAD.

## 6. **Final Content of Files:**

- **`README.md`**:
  ```
  Hello World 1
  content
  ```
  
- **`z.txt`** (created in `featureA` branch): Empty initially but added and committed.
- **`x.txt`** (created in `featureA` branch): Empty initially but added and committed.
- **`b.txt`**: Added in the main branch with commit message "Added b.txt".
- **`s.txt`**: Added in the `main` branch with commit message "s file added in main".
