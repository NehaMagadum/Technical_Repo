# Python Virtual Environment (virtualenv)
A virtual environment is an isolated Python environment created for a specific project. It allows us to install packages separately for each project without affecting other projects or the system Python.
## Why do we use a Virtual Environment? 

Suppose:  

• Project A requires pandas 2.0.  
• Project B requires pandas 3.0.  

Installing both versions globally can create conflicts.  

A virtual environment allows each project to use its own package versions independently.  

Advantages: 

• Avoids package version conflicts.  
• Keeps project dependencies separate.  
• Makes projects easier to manage and share.  
• Protects the system Python environment.  

## Creating a Virtual Environment 
```
python3 -m venv .venv
```
• python3 → Python interpreter.  
• -m venv → runs Python's virtual environment module.  
• .venv → name of the environment folder.  

## Activating Virtual Environment
```
source .venv/bin/activate
```
After activation, you may see:
```
(.venv) user@MacBook project %
```
This indicates that the virtual environment is active.

## Installing Packages
```
pip install pandas
```
The package will be installed inside the activated virtual environment.
## Deactivating Virtual Environment
```
deactivate
```
This exits the virtual environment and returns to the normal shell environment.

## Virtual Environment Workflow 
```
# Create environment
python3 -m venv .venv

# Activate environment
source .venv/bin/activate

# Install package
pip install pandas

# Save dependencies
pip freeze > requirements.txt

# Exit environment
deactivate
```
## Important Difference
| venv | virtualenv |
|----|-----|
| Built-in Python module | Third-party package |
| No separate installation required | Install using pip |
| python3 -m venv .venv | virtualenv .venv |
