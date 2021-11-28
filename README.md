```bash
options rotate
options timeout:1
options attempts:2

# Seems Local
nameserver 10.10.100.100
nameserver 10.10.200.200

# Google
nameserver 8.8.8.8
nameserver 8.8.4.4
# nameserver 2001:4860:4860::8844
# nameserver 2001:4860:4860::8888

# Cloudflare
nameserver 1.1.1.1
nameserver 1.0.0.1
# nameserver 2606:4700:4700::1111
# nameserver 2606:4700:4700::1001

# Quad9
nameserver 9.9.9.9
# nameserver 2620:fe::fe:9
# nameserver 2620:fe::9
```

```python
cat > resolv.py << "EndOfMessage"
import socket

for _ in range(5):
  socket.getaddrinfo('google.com', 80)
EndOfMessage
```

```bash
strace -e trace=connect python3 resolv.py 2>&1 | grep -i "htons(53)"
```
