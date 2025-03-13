![image](https://github.com/user-attachments/assets/6e743ff6-3830-4012-b333-55c71be1aff5)

![image](https://github.com/user-attachments/assets/ccc03544-85ba-4050-bfd9-f0e321706b53)

![image](https://github.com/user-attachments/assets/ef7daf6c-96a8-4138-b3af-aa2d7836136a)
![image](https://github.com/user-attachments/assets/a53b72eb-4694-425d-8fa7-e2b3aae25242)
![image](https://github.com/user-attachments/assets/2a9e97df-1acd-4243-89b7-a421e09a331a)
![image](https://github.com/user-attachments/assets/90479933-0655-48e2-a5d2-09e05f8bb3f6)


#Git Graded Assignment - Hero Vired

Introduction
This project is all about getting hands-on experience with Git and GitHub while working on a Python-based project. You'll learn how to:
- Use Git to manage your code
- Work with branches for new features and bug fixes
- Handle large files efficiently using Git LFS
- Collaborate effectively on GitHub

Files in This Project
1. CalculatorPlus: A Python program for basic math calculations.
2. Geometry Calculator: A tool to calculate areas of circles and rectangles.
3. Git LFS Integration: Helps in managing large files in Git.

---

#Task 1: Improving the Calculator

Goal:
Make a better calculator by adding a square root function and fixing a division bug.

Steps:
1. Set Up GitHub
   - Create a private GitHub repository called `git_assignment_HeroVired`.
   - Clone it to your local computer:
     ```bash
     git clone https://github.com/your-username/git_assignment_HeroVired.git
     cd git_assignment_HeroVired
     ```

2. Create a Branch for Development
   - Make a `dev` branch for ongoing work:
     ```bash
     git checkout -b dev
     ```
   - Add the initial calculator code to `calculator_plus.py`.

3. Merge Work and Release Version 1
   - Merge `dev` into `main`:
     ```bash
     git checkout main
     git merge dev
     ```
   - Tag the first release:
     ```bash
     git tag v1.0
     git push origin main --tags
     ```

4. Add Square Root Feature
   - Create a new branch:
     ```bash
     git checkout -b feature/sqrt
     ```
   - Implement square root calculation:
     ```python
     import math
     
     def square_root(x):
         return math.sqrt(x)
     ```
   - Commit and push the changes:
     ```bash
     git add calculator_plus.py
     git commit -m "Added square root feature"
     git push origin feature/sqrt
     ```

5. Fix the Division Bug
   - Switch back to `dev`:
     ```bash
     git checkout dev
     ```
   - Update the `divide` function to prevent division by zero:
     ```python
     def divide(a, b):
         if b == 0:
             raise ValueError("Cannot divide by zero.")
         return a / b
     ```
   - Commit and push the fix:
     ```bash
     git add calculator_plus.py
     git commit -m "Fixed division by zero bug"
     git push origin dev
     ```

6. Merge Changes and Release Version 2
   - Merge `feature/sqrt` into `dev`, then `dev` into `main`:
     ```bash
     git checkout dev
     git merge feature/sqrt
     git checkout main
     git merge dev
     ```
   - Tag version 2.0:
     ```bash
     git tag v2.0
     git push origin main --tags
     ```

---

Task 2: Managing Large Files with Git LFS

Goal:
Learn how to use Git LFS to store large files efficiently.

Steps:
1. Install Git LFS
   ```bash
   sudo apt update
   sudo apt install git-lfs
   ```

2. Enable Git LFS in Your Repo
   ```bash
   git lfs install
   ```

3. Create a Branch for Git LFS
   ```bash
   git checkout -b lfs
   ```

4. Tell Git to Track Large Files
   ```bash
   git lfs track ".bin"
   ```

5. Commit and Push a Large File
   ```bash
   dd if=/dev/urandom of=testfile.bin bs=1M count=300
   git add testfile.bin
   git commit -m "Added a large test binary file"
   git push origin lfs
   ```

6. Check if Git LFS is Working
   ```bash
   git lfs ls-files
   git show HEAD:testfile.bin
   ```

---

Task 3: Geometry Calculator

Goal:
Create a geometry calculator while using Git stash to manage unfinished work.

Steps:
1. Create a Branch for Geometry Calculator
   ```bash
   git checkout -b geometry-calculator
   ```

2. Implement Circle Area Calculation
   - Create a sub-branch:
     ```bash
     git checkout -b feature/circle-area
     ```
   - Add this function:
     ```python
     import math

     def calculate_circle_area(radius):
         return math.pi  radius  2
     ```
   - Stash unfinished work:
     ```bash
     git stash
     ```
   - Push the branch:
     ```bash
     git push origin feature/circle-area
     ```

3. Implement Rectangle Area Calculation
   - Create a sub-branch:
     ```bash
     git checkout -b feature/rectangle-area
     ```
   - Add this function:
     ```python
     def calculate_rectangle_area(length, width):
         return length  width
     ```
   - Stash unfinished work:
     ```bash
     git stash
     ```
   - Push the branch:
     ```bash
     git push origin feature/rectangle-area
     ```

4. Complete and Merge Work
   - Restore stashed work and commit changes:
     ```bash
     git checkout feature/circle-area
     git stash pop
     git add geometry_calculator.py
     git commit -m "Implemented circle area feature"
     git push origin feature/circle-area
     ```
   - Do the same for `feature/rectangle-area`.

5. Merge Everything into Main
   ```bash
   git checkout geometry-calculator
   git merge feature/circle-area
   git merge feature/rectangle-area
   git push origin geometry-calculator
   git checkout dev
   git merge geometry-calculator
   git checkout main
   git merge dev
   ```

