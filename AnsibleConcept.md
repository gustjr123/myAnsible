# Ansible

Ansible은 IAC(Infrastructure as a Code)로 자동화하는 도구

말그대로, <mark>**IT 인프라를 코드 기반으로 자동 설치 및 구축/관리/프로비저닝 하는 프로세스**</mark>

Ansible은 이런 <mark>**IaC를 지향하는 오픈소스 기반의 자동화 관리 도구**</mark>

### 🔸 Agentless

Chef, Puppet은 원격 서버에 **에이전트**를 설치할 필요가 있었다. 
따라서 Controller가 Agent와 명령을 주고 받는 방식.

하지만 Ansible은 <mark>**SSH기반**으로 원격서버에 명령을 전달</mark>하는 방식으로 에이전트가 필요없다.

### 🔸 접근 용이성

자동화 도구는 여러 명령어를 **한번에 모아서 실행할 수 있어야 한다.**
이러한 측면에서 <mark>명령 모음집(Playbook)</mark>을 YAML파일로 관리함으로써 진입장벽이 낮다.

### 🔸 멱등성

<mark>**여러번 수행해도 항상 같은 결과를 도출하는 성질**</mark>을 지니고 있다.


# Ansible 용어

### 🔸 Controller 서버 (실제 Ansible용어는 아니지만 앞으로 명칭을 위해 설명)

**Ansible을 설치하는 서버** = Ansible 명령을 여러 원격 서버에 전달하는 주체

### 🔸 Inventory(인벤토리 = Ansible hosts라고도 한다)

<mark>**Controller 서버가 명령을 전달할 원격 서버들의 목록**</mark>

**/etc/ansible/hosts** 파일에 해당 목록들이 저장되어 있다.

### 🔸 Playbook(플레이북)

원격 서버에 전달할 명령들을 모아둔 **명령집**, 즉 스크립트 파일이다.

### 🔸 Ansible의 작업 수행 모습
![Ansible Configuration](./img/Ansible%20Configuration.png)

[출처] https://5equal0.tistory.com/entry/Ansible-%EC%95%A4%EC%84%9C%EB%B8%94Ansible-%EA%B0%9C%EB%85%90%EA%B3%BC-%EC%84%A4%EC%B9%98%EC%82%AC%EC%9A%A9%EB%B2%95-w-CentOS-76

