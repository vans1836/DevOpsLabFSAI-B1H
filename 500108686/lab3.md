lab 3:

# **Git Basics**

## **Using SSH and HTTP for Git**

### **SSH Key Setup**

Using SSH ensures secure access to Git repositories by utilizing both public and private keys.

---

### **1. Generating an SSH Key**
Generate an SSH key by running the following command:
```sh
ssh-keygen -t ed25519 -C "vanshika1836@gmail.com"
```

Verify the key is generated at the default location:
```sh
ls ~/.ssh
```

---

### **2. Viewing the SSH Key**
To read the SSH key, use the following command:
```sh
cat ~/.ssh/id_ed25519.pub
```

---

### **3. Adding the SSH Key to the SSH-Agent**
```sh
ssh-add ~/.ssh/id_ed25519
```

---

### **4. Adding the Key to GitHub**
- Navigate to **GitHub Settings → SSH and GPG keys → Add a new key**.
- Copy and paste the contents of `id_ed25519.pub`.

---

### **Cloning a Repository Using SSH**
```sh
git clone git@github.com:vans1836/DemoMain.git
```

---

### **Cloning a Repository Using HTTP**
```sh
git clone https://github.com/vans1836/DemoMain.git
```

When using HTTP, Git will prompt for your credentials if authentication is required.

---

## **Git Workflow**

### **1. Initialize and Clone a Repository**
```sh
git init
git clone <repository-url>
```

---

### **2. Working on a Repository**
1. Navigate to the repository directory.
2. Make necessary changes.
3. Add changes to the staging area:
```sh
git add .
```
4. Commit changes with a descriptive message:
```sh
git commit -m "Your commit message"
```

---

### **3. Resolving Merge Conflicts**
To avoid merge conflicts, always pull the latest changes before pushing:
```sh
git pull origin main
git merge
```

Push the changes to the repository:
```sh
git push origin main
```

---

## **VIM Commands (for Git commit messages)**

```sh
1. i → Insert mode
2. q → Quit
3. esc → Changing modes
4. shift + v → Visual mode
   - y → Copy / shift + insert
   - p → Paste
5. ‘H’, ‘J’, ‘K’, ‘L’ → Move left, up, down, right
6. dd → Delete the line
7. u → Undo
8. /something → Search something
9. esc + :wq → Save and quit
```

---
