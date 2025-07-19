# SOP: Python Virtual Environment 

---


| Authors           | Created on     | Version | Last updated by | Last edited on |
|-------------------|---------------|---------|-----------------|---------------|
| Kawalpreet Kour   | 16 July 2025  | v1      | -               | -             |

---

## Table of Contents
- [Purpose](#1-purpose)
- [Scope](#2-scope)
- [Prerequisites](#3-prerequisites)
- [Procedure](#4-procedure)
  - [4.1. Introduction](#41-introduction)
  - [4.2. Checking Python Version](#42-checking-python-version)
  - [4.3. Creating Virtual Environment](#43-creating-virtual-environment)
  - [4.4. Activating Virtual Environment](#44-activating-virtual-environment)
  - [4.5. Installing Packages](#45-installing-packages)
  - [4.6. Freezing Installed Packages](#46-freezing-installed-packages)
  - [4.7. Deactivating the Virtual Environment](#47-deactivating-the-virtual-environment)
  - [4.8. Deleting Virtual Environment](#48-deleting-virtual-environment)
  
- [Troubleshooting](#5-troubleshooting)
- [Conclusion](#6-conclusion)
- [References](#7-references)
- [Revision History](#8-revision-history)

## 1. Purpose
This SOP outlines the standard procedure for setting up, managing, and troubleshooting Python virtual environments using the built-in `venv` module on Ubuntu systems.

## 2. Scope
This document is intended for all developers and engineers who need to:
- Create isolated Python environments
- Avoid dependency conflicts
- Maintain reproducible project setups across machines

## 3. Prerequisites
- A Linux-based system (Ubuntu recommended)
- Python 3.3 or higher installed
- Basic familiarity with terminal commands

## 4. Procedure

### 4.1. Introduction
Python virtual environments allow you to create isolated environments with their own site-packages, interpreter, and binaries. This ensures no conflict between dependencies of different projects on the same machine.

### 4.2. Check if Python 3 is Installed 
```bash
python3 
```
<img width="711" height="138" alt="Screenshot from 2025-07-19 14-27-19" src="https://github.com/user-attachments/assets/093d083c-01e2-4012-920a-6623c2ef2535" />

- If the output shows the version, Python 3 is already installed. You can also see additional information about copyright, license, etc.

- If the command shows an error saying bash: python3: command not found, Python is not installed.

### Install it:
```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip
```
### Verify Installation
```bash
python3 --version
```
### 4.3. Creating Virtual Environment
Navigate to your project folder and run:
```bash
python3 -m venv <env_name>
```
<img width="742" height="140" alt="Screenshot from 2025-07-19 14-54-25" src="https://github.com/user-attachments/assets/8604d558-7b7f-4dfb-96df-3fca38505f44" />

- Replace `<env_name>` with your preferred environment name (e.g., `venv` , `.venv` , `project_env` or `myenv` ).
- This creates a directory containing a copy of the Python interpreter and a local `site-packages`.

### 4.4. Activating Virtual Environment
```bash
source <env_name>/bin/activate
```
<img width="784" height="80" alt="Screenshot from 2025-07-19 15-01-49" src="https://github.com/user-attachments/assets/57c8bdd7-2297-4585-92f7-7a954eb0feab" />

Your prompt will change to `(env_name)` indicating activation.

### 4.5. Installing Packages
```bash
pip install <package_name>
```
<img width="1185" height="271" alt="Screenshot from 2025-07-19 15-37-47" src="https://github.com/user-attachments/assets/86966f21-dcf5-4418-9673-6cf7e619a467" />
<img width="1304" height="119" alt="Screenshot from 2025-07-19 15-38-05" src="https://github.com/user-attachments/assets/b96c2baa-4c08-421a-981f-4a1ac53fecc0" />

- Installed Flask as a demo package, commonly used for building simple web apps.
- You can install any other package as per your project like Django, FastAPI, pandas, etc.

### Check install success:
```bash
pip list
```
<img width="715" height="378" alt="Screenshot from 2025-07-19 15-38-33" src="https://github.com/user-attachments/assets/02d2fdac-28b0-40a0-ac37-86bfea2488d4" />

### 4.6. Freezing Installed Packages
Export the installed package versions to a file:
```bash
pip freeze > requirements.txt
```
<img width="916" height="62" alt="Screenshot from 2025-07-19 16-15-33" src="https://github.com/user-attachments/assets/d8bcf037-4ed6-45e9-b493-e03cac28bf10" />

- This command saves all installed packages + versions into a file.

## To check its contents:
```bash
cat requirements.txt
```
<img width="808" height="288" alt="Screenshot from 2025-07-19 16-17-29" src="https://github.com/user-attachments/assets/5023498a-a630-4b7f-a92b-1a6719e7e6ce" />

### 4.7. Deactivating the Virtual Environment
```bash
deactivate
```
<img width="763" height="65" alt="Screenshot from 2025-07-19 16-22-33" src="https://github.com/user-attachments/assets/f8fdf347-8e37-4af6-b022-82b21bb32a1b" />

- This exits the virtual environment and restores the global Python environment.

### 4.8. Deleting Virtual Environment
To completely remove the environment:
```bash
rm -rf <env_name>
```
<img width="763" height="65" alt="Screenshot from 2025-07-19 16-23-16" src="https://github.com/user-attachments/assets/b409361e-4ed1-41a0-b4ef-c3af6f4532eb" />

- This completely removes the virtual environment folder (named myenv here).
- Replace <env_name> with your environment name (like .venv, myenv, etc.) if it's different.

### 4.9. Project Setup on Another Machine
To replicate the environment:
```bash
git clone <project-url>
cd project-folder
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Troubleshooting

| **Issue**                                  | **Possible Cause**                       | **Solution**                                                                 |
|----------------------------------------------|---------------------------------------------|----------------------------------------------------------------------------------|
| `source myenv/bin/activate`: No such file      | Wrong path or myenv/ not created             | Make sure you're in the correct folder where virtual environment exists. Use `ls` to confirm. |
| Permission denied while activating            | Script not executable                       | Run: `chmod +x venv/bin/activate` to make the file executable                   |
| `pip install` fails or shows "Permission denied" | Virtual env not activated               | Run `source myenv/bin/activate` before installing any package                     |
| `python3: command not found`                  | Python not installed                        | Install Python: `sudo apt install python3 python3-venv`                         |
| `pip freeze` shows empty                      | No packages installed yet                   | Install at least one package first using `pip install <package>`                |
| `bash: deactivate: command not found`         | Not inside virtual environment              | First activate the environment, then `deactivate` will work                     |

---

## Conclusion

Using `venv` helps isolate dependencies per project.  
It keeps your global Python clean, avoids version conflicts, and makes deployment or sharing easy with `requirements.txt`.  
Virtual environments are essential in real-world team projects, frameworks (like Flask, Django), or while managing multiple apps on same system.

---

## References

- [Python Packaging Guide (Official)](https://packaging.python.org/en/latest/) – Install & best practices  
- [W3Schools - Python venv](https://www.w3schools.com/python/python_virtualenv.asp) – Simple explanation  
- [StackOverflow – How to create venv](https://stackoverflow.com/questions/43069780/how-to-create-virtual-env-with-python-3)  
- [GeeksForGeeks – Python Packages](https://www.geeksforgeeks.org/python/python-packages/) – Learn about packages  


## Revision History

| Version | Date       | Author           | Changes         |
|---------|------------|------------------|------------------|
| 1.0     | 2025-07-19 | Kawalpreet Kour  | Initial Draft Created |
