```bash
options rotate
options timeout:1
options attempts:2

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
# nameserver 9.9.9.9
# nameserver 2620:fe::fe:9
# nameserver 2620:fe::9
```

`resolv.py`

```python
import socket

for _ in range(5):
  socket.getaddrinfo('redhat.com', 80)
```

`strace -e trace=connect python3 resolv.py`
