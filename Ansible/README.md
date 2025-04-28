# Ansible

Commands

```bash

ansible-config list  # List all configurations

ansible-config view  # Show the current config file

ansible-config dump  # Show the current settings


```

---

YAML files

```YAML
# Normal
Fruit: Apple
Vegetable: Carrot

# Array/List
Fruits:
-   Orange
-   Apple

# Dic/Map
Banana:
    Calories: 105
    Fat: 0.4 g


```

---

### Inventory

Agentless

Inventory file in -> /etc/ansible/hosts

Sample Inventory file

```INI

web ansible_host=server1.company.com ansible_connection=ssh ansible_user=root
db ansible_host=server2.company.com ansible_connection=winrm ansible_user=admin
mail ansible_host=server3.company.com ansible_connection=ssh ansible_ssh_pass=P%12dwa
web2 ansible_host=server4.company.com ansible_connection=winrm ansible_user=root


# For locahost

localhost ansible_connection=localhost
```

Inventory files can be

- INI (previous exampel)
- YAML

### Variables

- Stores informatoin that change in each host

Same, can be INI of YAML

Ex

```INI
Web http_port=8081
```

```YAML
http_port: 8081
```

Use ->

```YAML
-firewalld:
    port: '{{ http_port }}'/tcp
    premanent: true
```
