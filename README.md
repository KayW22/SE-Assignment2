# SE-Assignment2
#!/usr/bin/env python3
"""
SE Assignment 2 - README Enhancement & GitHub Issues Workflow
Creates comprehensive README, manages issues, and closes them
"""

import os
import subprocess
import sys
import getpass
from pathlib import Path
from datetime import datetime

def run_command(command, cwd=None):
    """Run a shell command and return True if successful"""
    try:
        result = subprocess.run(command, shell=True, cwd=cwd, 
                              capture_output=True, text=True, check=True)
        print(f"✓ {command}")
        if result.stdout.strip():
            print(result.stdout.strip())
        return True
    except subprocess.CalledProcessError as e:
        print(f"✗ {command} failed:")
        print(f"Error: {e.stderr or e.stdout}")
        return False

def get_user_info():
    """Get user information for README and issues"""
    username = input("Enter your GitHub username: ").strip()
    classmate = input("Enter classmate's GitHub username (or 'teammate'): ").strip()
    if not classmate:
        classmate = "teammate"
    
    return username, classmate

def create_readme_content(username):
    """Generate comprehensive README content"""
    return f'''# SE Assignment 2 - Hello World with Git Workflow 🚀

## 📋 Project Description
This repository demonstrates a complete Software Engineering git workflow including:
- Initial commit with Hello World program
- Feature branch development (personalized greetings)
- Comprehensive README documentation
- GitHub Issues management and resolution

**Current Features:**
- ✅ Basic "Hello, World!" greeting
- ✅ Personalized "Hi! {username}" greeting (Feature 1)
- ✅ Professional documentation and issue tracking

## 🛠️ Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/{username}/SE-assignment2.git
   cd SE-assignment2
