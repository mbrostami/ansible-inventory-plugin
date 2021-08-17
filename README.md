# ansible-inventory-plugin

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
