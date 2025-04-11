---
title: "Ansible 101: Ansible Environment Variables Explained"
date: 2025-03-07
categories:
  - Ansible
tags:
  - automation
  - ansible
  - devops
---
### What Are Environment Variables in Ansible?

Environment variables in Ansible allow you to customize and control the behavior of Ansible execution, such as setting paths, credentials, debugging, and proxy configurations.


### Types of Environment Variables

1. **Ansible-Specific Variables:** Prefixed with `ANSIBLE_` (e.g., `ANSIBLE_CONFIG`, `ANSIBLE_STDOUT_CALLBACK`).
    
2. **User-Defined Variables:** Custom variables used in playbooks, roles, or inventory.
    
3. **System Environment Variables:** Used for proxy, locale, or path configuration

### Common Ansible Environment Variables

|   |   |
|---|---|
|Variable|Purpose|
|`ANSIBLE_CONFIG`|Define a custom Ansible config file location.|
|`ANSIBLE_INVENTORY`|Override the default inventory file.|
|`ANSIBLE_ROLES_PATH`|Set custom roles directory path.|
|`ANSIBLE_STDOUT_CALLBACK`|Change output format (e.g., json, yaml, minimal).|
|`ANSIBLE_NOCOLOR`|Disable colored output.|
|`ANSIBLE_HOST_KEY_CHECKING`|Disable SSH host key checking (`False` for automation)|

### Best Practices

- Keep sensitive data out of environment variables if they’re logged.
    
- Use `.env` files or configuration management tools for consistency.
    
- Leverage `ANSIBLE_CONFIG` to maintain multiple configurations for different projects.

### When to Use

- Switching between dev, staging, and production setups.
    
- Enabling debug or verbose output conditionally.
    
- Running automation with consistent environments (e.g., CI/CD).


### Summary

Environment variables in Ansible offer powerful ways to control and customize execution behavior. Use them to simplify your workflows, improve reusability, and streamline your automation process.



<iframe width="560" height="315" src="https://www.youtube.com/embed/yhSZX4t4edA?si=WAPu7PGT56kO1rDg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


