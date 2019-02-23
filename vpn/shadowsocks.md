## shadowsocks
!https://github.com/shadowsocksr-backup/shadowsocksr

- install
```
pip install shadowsocks
;start
sudo ssserver -p 443 -k password -m aes-256-cfb --user nobody -d start
;stop
sudo ssserver -d stop
;log
sudo less /var/log/shadowsocks.log
```

- free
!http://www.ishadowsocks.com/#free