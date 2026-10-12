# Online Student Helpdesk System — DevOps Case Study

## 1. Project Overview

The Online Student Helpdesk System is a web application designed to help students submit and view campus-related issues. This project demonstrates basic DevOps concepts and server configuration management using Ansible.

## 2. Objectives

- Understand the DevOps lifecycle and workflow.
- Develop a simple student helpdesk web application.
- Configure and verify an Ubuntu server using Ansible.
- Automate server checks and configuration tasks.
- Demonstrate successful execution using terminal outputs and screenshots.

## 3. Technologies Used

- **Python and Flask:** Web application development.
- **Ubuntu Server:** Application hosting environment.
- **Ansible:** Configuration management and automation.
- **SSH:** Remote server connectivity.
- **Windows 11 and WSL Ubuntu:** Ansible control environment.
- **GitHub:** Project version control and code hosting.

## 4. Project Architecture

Ansible runs from the WSL Ubuntu control node and connects to the Ubuntu Server virtual machine through SSH. The Flask application runs on the server and provides the student helpdesk interface.

**Workflow:**

1. The student accesses the Helpdesk website through a browser.
2. The Flask application displays the ticket submission form.
3. Ansible connects to the Ubuntu Server through SSH.
4. The playbook checks the server hostname, Python version, and SSH service.
5. Ansible creates a deployment verification marker file.

## 5. Project Files

- `inventory.ini` — Defines the managed server and SSH connection settings.
- `final-helpdesk.yml` — Ansible playbook for server verification and marker-file creation.
- `ansible.cfg` — Ansible configuration settings.
- `README.md` — Project documentation.

## 6. Setup Requirements

- Windows 11 with WSL Ubuntu.
- An Ubuntu Server virtual machine.
- Ansible installed in WSL Ubuntu.
- SSH service running on the managed server.
- Python 3 installed on the server.
- Flask and the project virtual environment configured on the server.

## 7. Execution Commands

Run these commands in the **WSL Ubuntu terminal**, from the Ansible project directory.

### Step 1: Navigate to the project directory

```bash
cd ~/ansible-project
```

### Step 2: Test Ansible connectivity

```bash
ansible helpdesk -i inventory.ini -m ping --ask-pass
```

Expected result: `pong`

### Step 3: Execute the final playbook

```bash
ansible-playbook -i inventory.ini final-helpdesk.yml --ask-pass
```

Expected result: The playbook completes successfully, ideally with `failed=0` and `unreachable=0`.

### Step 4: Verify the marker file

```bash
ansible helpdesk -i inventory.ini -m command -a "cat /home/sakshi/helpdesk-deployment.txt"
```

Expected output:

```text
Online Student Helpdesk verified by Ansible.
```

## 8. Results

- The Helpdesk website was opened and tested in a browser.
- Ansible successfully connected to the managed server.
- Server information and SSH service status were verified.
- A deployment verification marker file was created and checked.
- Execution evidence was captured for the project demonstration.

## 9. Limitations

- Ticket information is stored in memory and may disappear when the Flask application restarts.
- The current Ansible playbook verifies the server but does not automatically deploy the Flask application.
- The project does not yet include a persistent database or automated CI/CD pipeline.

## 10. Future Enhancements

- Store tickets in a MySQL database.
- Add student authentication and ticket status updates.
- Automate Flask deployment using Ansible.
- Add automated testing and a CI/CD pipeline.
- Implement monitoring and logging.

## 11. Conclusion

This project demonstrates a basic DevOps workflow through a Flask-based student helpdesk application and Ansible configuration management. It provides practical experience with Linux servers, SSH connectivity, automation, configuration files, and execution verification.
