# Ansible ad hoc commands

설명을 보았을때 ad hoc command는 별도의 playbook을 생성하지 않고 특정 작업을 스케줄링하는 기능이다.

예를들어, 매년 크리스마스에 관리하는 서버를 재부팅 하려면 playbook을 만들 필요없이 한 줄의 명령어로 처리가 가능하다

#### atlanta group의 서버들을 재부팅하는 명령어
``` bash
$ ansible atlanta -a "/sbin/reboot"
```

#### 특정 유저를 추가
``` bash
$ ansible atlanta -a "/sbin/reboot" -u username
```

#### 서버를 10개씩 실행
``` bash
$ ansible atlanta -a "/sbin/reboot" -f 10 -u username
```

# Commandline tool
- ansible
- ansible-config
- ansible-console
- ansible-doc
- ansible-galaxy
- ansible-inventory
- ansible-playbook
- ansible-pull
- ansible-vault

> 필요하면 찾아서 사용하면 될 것 같다.

[참고] https://docs.ansible.com/ansible/latest/command_guide/command_line_tools.html

# Ansible CLI cheatsheet

많이 사용하는 Ansible-playbook만 cheatsheet가 존재해서 가져와 봤다.

``` bash
ansible-playbook -i /path/to/my_inventory_file -u my_connection_user -k -f 3 -T 30 -t my_tag -M /path/to/my_modules -b -K my_playbook.yml
```

- [**-i**] : inventory 파일의 path 값
- [**-u**] : ssh 연결할 사용자 명 지정
- [**-k**] : ssh 연결할 때 비밀번호 인증 여부
- [**-f**] : 한번에 3개씩 실행
- [**-T**] : sets a 30-second timeout.
- [**-t**] : runs only tasks marked with the tag my_tag.
- [**-M**] : "/path/to/my/modules" 경로의 모듈 실행
- [**-b**] : executes with elevated privileges (uses become).
- [**-K**] : prompts the user for the become password.

[출처] https://docs.ansible.com/ansible/latest/command_guide/index.html