






![image](https://user-images.githubusercontent.com/87138860/213165406-8dca4c0f-09f9-461e-9a86-def228089884.png)







script:


```py
from pwn import *


def sapxep:
          num_list = [int(x) for x in str(num)]
          num_list = sorted(num_list,reverse=True)
          largest_num = int("".join(map(str,num_list)))
          return largest_num


def pre(sta):
          return int((sta.decode())[7:])

s=remote(“146.190.115.228”,10464)

a=s.recvuntil(b’n’)
print(a)
sta=pre(a)
x=str(sapxep(sta)).encode()
print(x)
s.sendline(x)

while (1):
           s.recvline()
            Như trên
s.interactive()
```
flag: KCSC{You will maximize yourself when participating in KCSC, G00d_j0b}
