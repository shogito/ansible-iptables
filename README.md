# Ansible Role: ansible-iptables

### 要求
iptablesが動作していること

### Role Variables
ICMPのECHOを許可(True/False)
```
allowIcmp: True
```

DDoS等の攻撃対策(True/False)
```
selfDefence: True

全ホストからの通信許可
```
allow:
  - { port: 80, protocol: tcp }
  - { port: 443, protocol: tcp }
  - { port: 22, protocol: tcp }
```

Docker用内部通信許可(サービス再起動などのタイミングではうまく動かない可能性大)
```
enableDockerNetwork: True
```

信頼するホスト(配列)
```
allowhosts: 
  - hoo
  - bar
```

拒否するホスト(配列)
```
denyhosts: 
  - hoge
  - huga
```

### Example Playbook
```
- hosts: all
  vars:
  roles:
    - { role: shogito.iptables }
```

### License
MIT / BSD

### Author Information


