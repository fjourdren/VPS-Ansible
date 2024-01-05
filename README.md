# Fast VPS Provisioning for Basic Nginx Server

This project streamlines the setup of a Virtual Private Server (VPS) with enhanced security features for hosting a basic Nginx web server.

Tested on :

- Debian 12

## Usage Instructions

1. **Configure Hosts File**: Begin by setting up the `hosts` file with the necessary details of your VPS.

2. **Edit Configuration File**: Modify the `provision.yml` file. Here, you can specify the default user credentials, including username, password, SSH key path, and a new SSH port. To create a hashed password for the user, follow this [guide](https://docs.ansible.com/ansible/latest/reference_appendices/faq.html#how-do-i-generate-encrypted-passwords-for-the-user-module) : `ansible all -i localhost, -m debug -a "msg={{ 'mypassword' | password_hash('sha512', 'mysecretsalt') }}"`

3. **Run the Playbook**: Execute the following commands to start the provisioning process:

   ```bash
   wsl --distribution Ubuntu
   ansible-playbook provision.yml -i hosts
   ```

## Features Included

- **User Configuration**: Sets up a user account with your specified credentials.

- **SSH Hardening**:
  Disables password authentication to enhance security.
  Allows you to change the SSH port for an added layer of security.

- **Firewall Setup**: Configures Uncomplicated Firewall (UFW) to protect the server.

- **Nginx Installation**: Installs Nginx with HTTP/2 support, optimizing performance and security.

- **Fail2Ban Integration**: Implements Fail2Ban for additional protection against unauthorized access attempts.
