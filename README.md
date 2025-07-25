# SOP: Python Virtual Environment 


> This SOP is a simple guide for setting up and using Python virtual environments on Ubuntu.



![Python Logo](https://www.python.org/static/community_logos/python-logo.png)

---
## Author Information
| Last Updated On | Version | Author           | Level           | Reviewer               |
|-----------------|---------|------------------|-----------------|------------------------|
| 18-07-2025      | V1.0    | Kawalpreet Kour  | Internal Review | Pritam                 |
| 25-07-2025      | V1.0    | Kawalpreet Kour  | L0              | Shreya/Sharvani        |
|                 |         | Kawalpreet Kour  | L1              | Abhishek V             |
|                 |         | Kawalpreet Kour  | L2              | Abhishek Dubey/Rishabh sharma |

---
### Introduction
Python virtual environments allow you to create isolated environments with their own site-packages, interpreter, and binaries. This ensures no conflict between dependencies of different projects on the same machine.

---
## Table of Contents
- [Purpose](#purpose)
- [Pre-requisites](#pre-requisites)
- [Procedure](#procedure)
  - [Check if Python 3 is Installed](#check-if-python-3-is-installed)
  - [Creating Virtual Environment](#creating-virtual-environment)
  - [Activating Virtual Environment](#activating-virtual-environment)
  - [Installing Packages](#installing-packages)
  - [Freezing Installed Packages](#freezing-installed-packages)
  - [Deactivating the Virtual Environment](#deactivating-the-virtual-environment)
  - [Deleting Virtual Environment](#deleting-virtual-environment)
- [Troubleshooting](#troubleshooting)
- [Best Practices](#best-practices)
- [Conclusion](#conclusion)
- [Contact Information](#contact-information)
- [References](#references)

---


## Purpose
To give a simple guide on how to create, use, and manage Python virtual environments on Ubuntu.

---
## Pre-requisites

| Component             | Description                                           |
|-----------------------|-------------------------------------------------------|
| Linux System          | A Linux-based OS is required (Ubuntu is recommended) |
| Python Version        | Python 3.3 or higher must be installed                |
| Terminal Knowledge    | Basic familiarity with command-line operations        |

---
## Procedure



### Check if Python 3 is Installed 
```bash
python3 
```
<img width="711" height="138" alt="Screenshot from 2025-07-19 14-27-19" src="https://github.com/user-attachments/assets/093d083c-01e2-4012-920a-6623c2ef2535" />

- If the output shows the version, Python 3 is already installed. You can also see additional information about copyright, license, etc.

- If the command shows an error saying bash: python3: command not found, Python is not installed.

#### Install it:
_Updates the package list to get the latest versions._  
_Installs Python 3, venv module (for virtual environments), and pip (Python package installer)._

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip
``` 
#### Verify Installation
_Checks installed Python 3 version._

```bash
python3 --version
```
###  Creating Virtual Environment

_Creates a new virtual environment._

```bash
python3 -m venv <env_name>
```
<img width="742" height="140" alt="Screenshot from 2025-07-19 14-54-25" src="https://github.com/user-attachments/assets/8604d558-7b7f-4dfb-96df-3fca38505f44" />

- Replace `<env_name>` with your preferred environment name (e.g., `venv` , `.venv` , `project_env` or `myenv` ).
- This creates a directory containing a copy of the Python interpreter and a local `site-packages`.

### Activating Virtual Environment
_Activates the virtual environment (you’ll see (myenv) in your shell)._
```bash
source <env_name>/bin/activate
```
<img width="784" height="80" alt="Screenshot from 2025-07-19 15-01-49" src="https://github.com/user-attachments/assets/57c8bdd7-2297-4585-92f7-7a954eb0feab" />

Your prompt will change to `(env_name)` indicating activation.

### Installing Packages
_Installs a package inside the virtual environment._

```bash
pip install <package_name>
```
<img width="1185" height="271" alt="Screenshot from 2025-07-19 15-37-47" src="https://github.com/user-attachments/assets/86966f21-dcf5-4418-9673-6cf7e619a467" />
<img width="1304" height="119" alt="Screenshot from 2025-07-19 15-38-05" src="https://github.com/user-attachments/assets/b96c2baa-4c08-421a-981f-4a1ac53fecc0" />

- Installed Flask as a demo package, commonly used for building simple web apps.
- You can install any other package as per your project like Django, FastAPI, pandas, etc.

#### Check install success:
_Shows all installed packages in the environment._

```bash
pip list
```
<img width="715" height="378" alt="Screenshot from 2025-07-19 15-38-33" src="https://github.com/user-attachments/assets/02d2fdac-28b0-40a0-ac37-86bfea2488d4" />

### Freezing Installed Packages
_Exports the list of installed packages and versions to a file._

```bash
pip freeze > requirements.txt
```
<img width="916" height="62" alt="Screenshot from 2025-07-19 16-15-33" src="https://github.com/user-attachments/assets/d8bcf037-4ed6-45e9-b493-e03cac28bf10" />

- This command saves all installed packages + versions into a file.

#### To check its contents:
_Displays contents of requirements.txt._

```bash
cat requirements.txt
```
<img width="808" height="288" alt="Screenshot from 2025-07-19 16-17-29" src="https://github.com/user-attachments/assets/5023498a-a630-4b7f-a92b-1a6719e7e6ce" />

### Deactivating the Virtual Environment
_Deactivates the virtual environment._

```bash
deactivate
```
<img width="763" height="65" alt="Screenshot from 2025-07-19 16-22-33" src="https://github.com/user-attachments/assets/f8fdf347-8e37-4af6-b022-82b21bb32a1b" />

- This exits the virtual environment and restores the global Python environment.

### Deleting Virtual Environment
To completely remove the environment:


```bash
rm -rf <env_name>
```
<img width="763" height="65" alt="Screenshot from 2025-07-19 16-23-16" src="https://github.com/user-attachments/assets/b409361e-4ed1-41a0-b4ef-c3af6f4532eb" />

- This completely removes the virtual environment folder (named myenv here).
- Replace <env_name> with your environment name (like .venv, myenv, etc.) if it's different.

---

## Troubleshooting

| **Issue**                                          | **Possible Cause**            | **Solution**                                                                 |
|----------------------------------------------------|------------------------------|------------------------------------------------------------------------------|
| `source myenv/bin/activate`: No such file          | Wrong path or myenv/ missing | Make sure you're in the correct folder where the virtual environment exists. Use `ls` to confirm. |
| Permission denied while activating                 | Script not executable        | Run: `chmod +x venv/bin/activate` to make the file executable                |
| `python3: command not found`                       | Python not installed         | Install Python: `sudo apt install python3 python3-venv`                      |
| `pip freeze` shows empty                           | No packages installed yet    | Install at least one package first using `pip install <package>`             |
| `bash: deactivate: command not found`              | Not inside virtual env       | First activate the environment, then `deactivate` will work                  |

---

## Best Practices

| Heading                        | Description                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------|
| Use Virtual Environments       | Always create a virtual environment for each project to avoid dependency conflicts.             |
| Name and Ignore venv Folders   | Use consistent names like `venv`, `.venv`, `project_env`, and add them to `.gitignore`.         |
| Update Requirements File       | After installing or upgrading packages, update `requirements.txt` using `pip freeze > requirements.txt`. |
| Avoid Global Installs          | Don't install packages globally unless absolutely necessary.                                     |
| Document Environment Variables | Clearly mention any environment variables your project needs in a README or `.env.example` file. |

---
## Conclusion

Using `(env_name)` helps isolate dependencies per project.  
It keeps your global Python clean, avoids version conflicts, and makes deployment or sharing easy with `requirements.txt`.  
Virtual environments are essential in real-world team projects, frameworks (like Flask, Django), or while managing multiple apps on same system.

---
## Contact Information

| Name             | Email                                         |
|------------------|-----------------------------------------------|
| Kawalpreet Kour  | Kawalpreet.kour.snaatak@mygurukulam.co        |

---

## References

| Links                                                                                     | Descriptions                           |
|-------------------------------------------------------------------------------------------|----------------------------------------|
| [Python Packaging Guide (Official)](https://packaging.python.org/en/latest/) | Install & best practices      |
| [W3Schools - Python venv](https://www.w3schools.com/python/python_virtualenv.asp) | Simple explanation   |
| [StackOverflow](https://stackoverflow.com/questions/43069780/how-to-create-virtual-env-with-python-3) |How to create venv |
| [GeeksForGeeks – Python Packages](https://www.geeksforgeeks.org/python/python-packages/)  | Learn about packages          |

---


