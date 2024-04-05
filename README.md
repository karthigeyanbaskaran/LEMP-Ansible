# Ansible LEMP Stack Deployment

This Ansible playbook automates the deployment of a LEMP (Linux, Nginx, MySQL, PHP, Phpmyadmin) stack on a remote server. It includes the installation and configuration of Nginx, PHP-FPM, MySQL, and phpMyAdmin.

## Prerequisites

- Ansible installed on your local machine.
- Access to a remote server with SSH key authentication.

## Inventory Configuration (inventory.yml)

```yaml
all:
  hosts:
    web01:
      ansible_host: your-host
      ansible_user: your-host-username
      ansible_ssh_private_key_file: pem-file
      ansible_ssh_common_args: '-o StrictHostKeyChecking=no'
```

## Nginx Configuration (nginx.conf.j2)

The playbook includes a customized Nginx configuration template (`nginx.conf.j2`) for your application. Ensure to adjust it according to your specific requirements.

## Playbook (web.yml)

This playbook installs and configures the LEMP stack on the specified server.

### Variables

- `php_version`: PHP version to be installed (default is "8.2").
- `php_packages`: List of PHP packages to be installed.

### Tasks

1. Install and configure Nginx.
2. Add Ondřej Surý PPA repository for PHP.
3. Install and configure PHP-FPM.
4. Install MySQL and its dependencies.
5. Configure MySQL, create a user, and a database.
6. Enable remote login to MySQL.
7. Download and install phpMyAdmin.

### Handlers

- `Restart mysql`: Restart MySQL service after configuration changes.
- `Restart nginx`: Restart Nginx after Nginx configuration changes.
- `Update package cache`: Update package cache after adding repositories.

## Running the Playbook

```bash
ansible-playbook -i inventory.yml web.yml
```

This playbook automates the entire process of setting up a LEMP stack, ensuring a smooth deployment of your web application.

**Note:** Make sure to review and customize the playbook according to your specific project requirements. In the Lemp.yaml file set your DB username and password for your convenience
