# PIP (Python Package Manager)
pip is a package manager in python used to install, manage, and share Python libraries and packages.  
For example, we can install pandas, numpy, and matplotlib using pip.
### What does pip do?
• Installs Python packages.  
• Updates packages.  
• Uninstalls packages.  
• Manages project dependencies.  

Example:
```
pip install pandas
```
This install pandas library. 

### Always use pip inside Virtual Environment
A virtual environment is an isolated environment for a Python project.  

Why use it?  

• Keeps project packages separate.
• Avoids conflicts between projects.
• Does not unnecessarily modify global Python packages.  

Activate virtual environment:
```
source .venv/bin/active
```
After activation, install packages:
```
pip install pandas
```

### pip freeze command
```
pip freeze
```
Display all installed packages and their versions.  

Example output:
```
matplotlib==3.10.0
numpy==2.2.0
pandas==2.2.3
```
Save packages into requirements.txt
```
pip freeze > requirements.txt
```
Meaning:  

• pip freeze → lists installed packages with versions.  
• > redirects output into a file.  
•  requirements.txt → stores package names and versions.  

This file helps other developers install the same dependencies.

### pip install -r requirements.txt
```
pip install -r requirements.txt
```
Meaning:

- -r means read requirements from a file.
- pip reads package names from requirements.txt.  
- Installs all listed packages automatically.
  
Example requirements.txt:
```
pandas==2.2.3
numpy==2.2.0
matplotlib==3.10.0
```
### Practical Workflow
Step-by-step project setup
```
# 1. Create virtual environment
python3 -m venv .venv

# 2. Activate virtual environment
source .venv/bin/activate

# 3. Install packages
pip install pandas matplotlib

# 4. Save dependencies
pip freeze > requirements.txt

# 5. Install dependencies in another environment
pip install -r requirements.txt
```


