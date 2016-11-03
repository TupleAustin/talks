<!-- $theme: default -->

# Introduction to Ansible

By [@colinfdrake](https://twitter.com/colinfdrake)

---

# What is it?

> App deployment, configuration management and orchestration - all from one system. Ansible is powerful IT automation that you can learn quickly.

---

# Basic Concepts

- Inventory
- Facts
- Tasks
- Playbooks
- Roles

---

# Inventory

- The servers to operate on, may be grouped
- Operated on via local login or SSH, no "Ansible server" needed
- Can also by dynamically discovered (built-in AWS discovery)

```ini
# Typical inventory file, predefined list

[local]
127.0.0.1

[remote]
buildserver1.ourcompany.com
buildserver2.ourcompany.com
```

---

# Facts

- Describe the state of the system
- Collected for each node in the inventory
- Ansible provides many built-ins
	- `ansible_os_family`, `ansible_env`, ...
- Define custom facts as the output of commands
- Used as variables in tasks, file templates, etc.

---

# Tasks

- Many built-in ways to run tasks:
	- `shell`, `apt`, `service`, `copy`, ...
- Declarative: usually describes the desired state of the system
	- Ex: `apt: package="vim" state="installed"`
- Should be idempotent
	- i.e. won't run `service start` if service is already running
	- Facts may be used to determine if a task needs to be run

---

# Playbooks

- Defines which tasks to run on which nodes in the inventory
- May configure static variables

```yaml
# Playbook example (YAML)

- hosts: all
  vars:
    text: "Hello World"
  tasks:
    - shell: echo "{{ text }}"
    - gem: name="rake" state="installed"

- hosts: local
  tasks:
    - shell: echo "This is only locally run"
```

---

# Roles

- Help abstract and modularize Playbooks
- Break up steps, variable definitions, etc. into a role that can be executed by name
- [Ansible Galaxy](https://galaxy.ansible.com/) is the repository of communited maintained roles

```yaml
# To execute roles in a Playbook...

roles:
  - TupleAustin.xcode
  - TupleAustin.xcode-cli
  - TupleAustin.homebrew-ruby
```

---

# Prepare for Failure: Quick Live Demo