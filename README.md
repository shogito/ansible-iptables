# Ansible Role: ansible-iptables

### 要求
iptablesが動作していること

### Role Variables
iptablesでのパケットフィルタの有効化(True/False)
```
ANSIBLE_IPTABLES_FILTER: True
```

全ホストへのICMPのECHOを許可(True/False)
```
ANSIBLE_IPTABLES_ALLOW_ICMP: True
```

DDoS等の攻撃対策(True/False)
```
ANSIBLE_IPTABLES_SELF_DEFENCE: True
```

全ホストからの通信許可
```
ANSIBLE_IPTABLES_ALLOW:
  - { port: 80, protocol: tcp }
  - { port: 443, protocol: tcp }
  - { port: 22, protocol: tcp }
```

Docker用内部通信許可(サービス再起動などのタイミングではうまく動かない可能性大)
```
ANSIBLE_IPTABLES_DOCKER_NETWORK: True
```

信頼するホスト(配列)
```
ANSIBLE_IPTABLES_ALLOW_HOSTS: 
  - hoo
  - bar
```

拒否するホスト(配列)
```
ANSIBLE_IPTABLES_DENY_HOSTS: 
  - hoge
  - huga
```

### Example Playbook
```
- hosts: all
  vars:
    ANSIBLE_IPTABLES_ALLOW_ICMP: True
    ANSIBLE_IPTABLES_SELF_DEFENCE: True
    ANSIBLE_IPTABLES_ALLOW:
      - { port: 80, protocol: tcp }
      - { port: 443, protocol: tcp }
      - { port: 22, protocol: tcp }
    ANSIBLE_IPTABLES_DOCKER_NETWORK: True
    ANSIBLE_IPTABLES_ALLOW_HOSTS: []
    ANSIBLE_IPTABLES_DENY_HOSTS: []
  roles:
    - { role: shogito.iptables }
```

### License
MIT / BSD

### Author Information


