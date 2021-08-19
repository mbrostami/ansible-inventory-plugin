# ansible-inventory-plugin

## Installation
Copy plugin py and yaml file into a directory (e.g. `~/.ansible/plugins/inventory/`)  
Edit the ansible.cfg file located in `~/.ansible.cfg`   

```
[defaults]
inventory_plugins  = ~/.ansible/plugins/inventory

[inventory]
enable_plugins = yamltags, host_list, script, auto, yaml, ini, toml 
```


## yamltags 
Ansible inventory plugin to support tag in yaml files

### Example
```
all: 
    hosts:
        test1:
            tags:
              - TagA
        test2:
            host_var: value
            tags:
              - TagA
              - TagB
```
Output: `ansible-inventory -i example.yaml  --graph`
```
@all:
  |--@TagA:
  |  |--test1
  |  |--test2
  |--@TagB:
  |  |--test2
  |--@ungrouped:
```
