# ansible-inventory-plugin

## yamltags 
Ansible inventory plugin to support tag in yaml files

### Example
```
all: # keys must be unique, i.e. only one 'hosts' per group
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
Output:  
```
@all:
  |--@TagA:
  |  |--test1
  |  |--test2
  |--@TagB:
  |  |--test2
  |--@ungrouped:
```
