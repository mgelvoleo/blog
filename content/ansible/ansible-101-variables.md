---
title: "Ansible 101: Understanding Variables - Strings, Booleans, Lists, and Dictionaries"
date: 2025-03-07
categories:
  - Ansible
tags:
  - automation
  - ansible
  - devops
---

Variables are one of the most powerful features in Ansible. They allow you to make your playbooks dynamic, reusable, and adaptable to different environments. In this lesson, we’ll explore the different types of variables in Ansible, including **strings**, **booleans**, **lists**, and **dictionaries**, and how to use them effectively in your playbooks.

## **I. String Variables**

### **What is a String Variable?**

A string variable is a sequence of characters, such as text or numbers, enclosed in quotes. Strings are the most common type of variable used in Ansible.

### **How to Define and Use String Variables**

You can define string variables in your playbooks, inventory files, or separate variable files. Here’s an example:
```
```
```
name: Example of a string variable
  hosts: localhost
  vars:
    app_name: "MyWebApp"
    app_version: "1.0.0"
  tasks:
    - name: Print the app name and version
      debug:
        msg: "The app {{ app_name }} is running version {{ app_version }}."
```
        
        
### **Use Cases for String Variables**

- Setting application names, versions, or configurations.
    
- Defining file paths or URLs dynamically.
    

---

## **II. Boolean Variables**

### **What is a Boolean Variable?**

A boolean variable represents a true or false value. In Ansible, booleans are often used to control the flow of playbooks using conditionals.

### **How to Define and Use Boolean Variables**

Boolean variables can be defined as `true` or `false` (without quotes). Here’s an example:
```

name: Example of a boolean variable
  hosts: localhost
  vars:
    enable_feature: true
  tasks:
    - name: Check if the feature is enabled
      debug:
        msg: "The feature is enabled."
      when: enable_feature
```


### **Use Cases for Boolean Variables**

- Enabling or disabling features in your playbooks.
    
- Controlling whether certain tasks should run.
    

---

## **III. List Variables**

### **What is a List Variable?**

A list variable is an ordered collection of items. Lists are useful when you need to store multiple values, such as a list of packages, users, or IP addresses.

### **How to Define and Use List Variables**

Lists are defined using square brackets `[]`. Here’s an example:

```

name: Example of a list variable
  hosts: localhost
  vars:
    packages:
      - nginx
      - mysql
      - php
  tasks:
    - name: Install packages
      apt:
        name: "{{ item }}"
        state: present
      loop: "{{ packages }}"
```



### **Use Cases for List Variables**

- Installing multiple packages or software.
    
- Managing a list of users or groups.
    
- Iterating over a collection of items in tasks.
    

---

## **IV. Dictionary Variables**

### **What is a Dictionary Variable?**

A dictionary variable is a collection of key-value pairs. Dictionaries are useful for storing structured data, such as configuration settings or user details.

### **How to Define and Use Dictionary Variables**

Dictionaries are defined using curly braces `{}` and key-value pairs. Here’s an example:

```
name: Example of a dictionary variable
  hosts: localhost
  vars:
    user_details:
      name: "john_doe"
      uid: 1001
      shell: "/bin/bash"
  tasks:
    - name: Create a user
      user:
        name: "{{ user_details.name }}"
        uid: "{{ user_details.uid }}"
        shell: "{{ user_details.shell }}"
```



### **Use Cases for Dictionary Variables**

- Storing and managing configuration settings.
    
- Defining user or system properties.
    
- Organizing complex data structures.
    

---

## **Practical Example: Combining All Variable Types**

Let’s combine all the variable types into a single playbook to demonstrate their power and flexibility:

```

name: Combined example of variables
  hosts: localhost
  vars:
    app_name: "MyApp"  # String
    enable_logging: true  # Boolean
    dependencies:  # List
      - nginx
      - mysql
      - php
    config:  # Dictionary
      port: 8080
      log_level: "debug"
  tasks:
    - name: Print app details
      debug:
        msg: |
          App Name: {{ app_name }}
          Logging Enabled: {{ enable_logging }}
          Dependencies: {{ dependencies }}
          Config: {{ config }}

    - name: Install dependencies
      apt:
        name: "{{ item }}"
        state: present
      loop: "{{ dependencies }}"
      when: enable_logging
```



---

## **Key Takeaways**

1. **String Variables**: Used for text or single values.
    
2. **Boolean Variables**: Used for true/false conditions.
    
3. **List Variables**: Used for collections of items.
    
4. **Dictionary Variables**: Used for structured key-value pairs.
    

By mastering these variable types, you’ll be able to write more dynamic, reusable, and efficient Ansible playbooks.


<iframe width="560" height="315" src="https://www.youtube.com/embed/xMb7EkA6fh0?si=dUIgUOvZ9m3b80yV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

