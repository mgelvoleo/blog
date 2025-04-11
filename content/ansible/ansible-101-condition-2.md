---
title: "Ansible 101: Ansible Conditions Made Easy | When, Failed, Changed, and More! - Part 2"
date: 2025-03-07
categories:
  - Ansible
tags:
  - automation
  - ansible
  - devops
---

Welcome back to Part 2 of our **Ansible Conditions Made Easy** series! In Part 1, we explored the basics like `when`, `failed_when`, and `changed_when`. Now, let’s **level up** by combining these conditionals with **loops**, **handlers**, and **more advanced use cases** to build even more powerful and flexible playbooks.

---

#### 🔁 1. Using Conditions with Loops

Ansible loops are great for repetitive tasks—but what if you want to selectively skip some iterations?

```
- name: Install selected packages
  apt:
    name: "{{ item }}"
    state: present
  loop:
    - nginx
    - apache2
    - invalid_pkg
  when: item != 'invalid_pkg'

```
Here, the `when` clause filters out `invalid_pkg` dynamically during the loop.

---

#### 🔀 2. Combining Multiple Conditions

You can chain multiple conditions using Jinja2 expressions:

```
- name: Restart nginx if on Ubuntu and config was updated
  service:
    name: nginx
    state: restarted
  when: ansible_os_family == 'Debian' and nginx_config_updated

```

This ensures the task only runs when **both** conditions are true.

---

#### 🚨 3. Custom Failure with `failed_when`

You can handle non-zero exit codes **gracefully**:

```

- name: Run health check
  command: ./check_health.sh
  register: result
  failed_when: "'ERROR' in result.stdout"


```

Even if the command exits with `0`, we fail the task if it contains “ERROR” in the output.

---

#### 🛎 4. Conditional Handlers

Handlers are normally triggered via `notify`, but you can use conditions before notifying too:

```
- name: Change configuration
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
  notify: Restart nginx
  when: update_config | bool

```

This avoids unnecessary restarts if nothing changed.

---

#### 🧠 5. Real-World Use Case: Conditional User Creation

Only create a user if it doesn’t exist **and** meets a specific condition:

```

- name: Add app user
  user:
    name: appuser
    state: present
  when: "'appuser' not in ansible_facts['passwd'] and deploy_env == 'production'"

```

---

### ✅ Wrapping Up

Using conditions in Ansible lets you write smarter, more **efficient playbooks** that respond dynamically to your environment. In this part, we explored how conditions enhance loops, handlers, and custom logic to create production-ready automation workflows.

<iframe width="560" height="315" src="https://www.youtube.com/embed/L7wFmEbJbss?si=D85fNCOA3Oh5O7Fo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>