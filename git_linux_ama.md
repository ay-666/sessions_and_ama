# Linux, Git AMA Questions - Answers

## How to know hidden files

```bash
ls -a
```

- `ls` → lists files and directories
- `-a` → shows hidden files also

Example:
```bash
ls -la
```

## Difference between clone and pull

### git clone
- Used to copy a remote repository to your local machine
- Done only the first time

```bash
git clone url
```

### git pull
- Used to fetch and update the latest changes from remote repository
- Used after repository already exists locally

```bash
git pull origin main
```

---

## Use of squash command

Squash combines multiple commits into a single commit.

Used to keep Git history clean.

### Example:
```bash
git rebase -i HEAD~3
```

Then change:
```text
pick
pick
pick
```

to:
```text
pick
squash
squash
```

---

## Difference between list and tuple

| List    | Tuple     |
| ------- | --------- |
| Mutable | Immutable |
| Slower  | Faster    |

### Example:
```python
my_list = [1, 2, 3]
my_tuple = (1, 2, 3)
```

---

## How to add repository on GitLab

### Create Repository on GitLab

1. Login to GitLab
2. Create **New Project**


### Connect Local Project

```bash
git init
git remote add origin <repository_url>
git add .
git commit -m "Initial commit"
git push -u origin main
```

## Difference between kill -15 vs kill -9

### kill -15
- Gracefully stops process
- Allows cleanup before stopping

```bash
kill -15 PID
```

### kill -9
- Forcefully stops process
- No cleanup happens

```bash
kill -9 PID
```

---

## Use of rebase

Rebase is used to move or combine commits from one branch to another.

Keeps Git history linear and clean.

### Example:
```bash
git checkout feature
git rebase main
```

---

## How to solve merge conflict

### Steps:
1. Pull latest changes
2. Open conflicted file
3. Remove conflict markers:
   ```text
   <<<<<<<
   =======
   >>>>>>>
   ```
4. Keep correct code
5. Add file
6. Commit changes

---

## How to know architecture of PC

### Linux Commands

```bash
uname -m
```

Example output:
- `x86_64` → 64-bit
- `i686` → 32-bit

---

## How can we create a branch and switch branch immediately

```bash
git switch -c branch-name
```

---

## How to add user in group

### Command:
```bash
sudo usermod -aG groupname username
```

### Example:
```bash
sudo usermod -aG sudo john
```

---

## How do you removed staged file form staging area

### Stage single file
```bash
git reset
```
---

## What are the main pillars of OOPS

### 1. Encapsulation
Binding data and methods together.

### 2. Inheritance
One class acquires properties of another class.

### 3. Polymorphism
Same function behaves differently.

### 4. Abstraction
Hiding implementation details.

---

## Rename current branch 
```bash
git branch -m new-branch-name
```

---

## How to delete a directory

### Delete empty directory
```bash
rmdir foldername
```

### Delete non-empty directory
```bash
rm -r foldername
```

---
