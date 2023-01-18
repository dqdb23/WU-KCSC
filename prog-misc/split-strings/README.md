![image](https://user-images.githubusercontent.com/87138860/213165600-5e458e7e-2e74-4071-9218-247af708ead8.png)



tương tự bài gen-max-number


script: 




```py
from pwn import *
import wordninja
r = remote("159.89.197.210",10463)
a = r.recvuntil(b'\n')
print(a)
c = " ".join(wordninja.split(a[9:].decode()))
r.sendline(c.encode())
while(1):
    r.recvline()
    a = r.recvuntil(b'\n')
    c = " ".join(wordninja.split(a[9:].decode()))
    print(c.encode())
    r.sendline(c.encode())
    
r.interactive()

```

flag: KCSC{Looks like you know how to use that tool, nice hecker}
