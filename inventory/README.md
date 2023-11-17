# Ansible Inventory Handling

Ansible은 host나 node들을 Inventory라는 리스트항목으로 관리한다.

직접 명령어에 host나 node를 지정해서 사용할 수 있지만 대부분 inventory를 생성해서 관리한다.

[출처] https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html

#### Default inventory path
``` bash
/etc/ansible/hosts
```

#### select specific inventory
``` bash
ansible {명령어} -i <path>
```

# Inventory formats, host, group

기본적으로 인벤토리는 다음과 같은 형태로 이루어진다.

#### default inventory
``` bash
mail.example.com

[webservers]
foo.example.com
bar.example.com

[dbservers]
one.example.com
two.example.com
three.example.com
```

#### YAML format
``` yaml
ungrouped:
  hosts:
    mail.example.com:
webservers:
  hosts:
    foo.example.com:
    bar.example.com:
dbservers:
  hosts:
    one.example.com:
    two.example.com:
    three.example.com:
```

> 여기서 ungrouped나 webservers, dbservers는 group이고 주소값은 host를 나타낸다.

# Inventory 관리

## group 중복 가능

Inventory의 host값들은 여러개의 group에 할당 될 수 있다.

``` yaml
ungrouped:
  hosts:
    mail.example.com:
webservers:
  hosts:
    foo.example.com:
    bar.example.com:
dbservers:
  hosts:
    one.example.com:
    two.example.com:
    three.example.com:
east:
  hosts:
    foo.example.com:
    one.example.com:
    two.example.com:
west:
  hosts:
    bar.example.com:
    three.example.com:
prod:
  children:
    east:
test:
  children:
    west:
```

위 예시를 보면 하나의 호스트가 여러개의 그룹에 매핑되어 있는 모습을 볼 수 있다.

이러한 특징으로 호스트 및 node를 다양한 조건으로 그룹화 시켜 관리 할 수 있다.

#### 에시
- where(서버가 위치한 장소) : east, west
- what(서버의 용도) : webservers, dbservers
- when(서버가 사용되는 시기) : production, test 

## Examples
#### inventory_test 파일
``` bash
[dbservers]
db01.test.example.com
db02.test.example.com

[appservers]
app01.test.example.com
app02.test.example.com
app03.test.example.com
```

#### inventory_staging 파일
``` bash
[dbservers]
db01.staging.example.com
db02.staging.example.com

[appservers]
app01.staging.example.com
app02.staging.example.com
app03.staging.example.com
```

#### test파일의 appservers group에 실행
``` bash
ansible-playbook -i inventory_test -l appservers site.yml
```