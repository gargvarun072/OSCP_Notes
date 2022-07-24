Encryption Cracking


```python3
import sys, Des
from base64 import b64decode

passwd = b64decode('<base64>')
c = des.DesKey(b'<Deskey>')
iv = b'<iv>'
print(c.decrypt(passwd, initial=iv, padding=True))
```