---
title: Handler
date: 2023-10-01
categories:
  - Ansible
tags:
  - automation
  - ansible
  - devops
---

Handlers are a unique feature in Ansible that allow you to trigger tasks only when notified by other tasks. This lesson will teach you how to use handlers to manage services, reload configurations, or perform other actions only when necessary.

**What You’ll Learn:**

- What handlers are and why they are useful in playbooks.
    
- How to define handlers in your playbooks.
    
- Using the `notify` directive to trigger handlers.
    
- Practical examples, such as restarting a service after a configuration change.
    

**Use Cases:**

- Restarting Apache or Nginx after updating a configuration file.
    
- Reloading a database service after a schema change

