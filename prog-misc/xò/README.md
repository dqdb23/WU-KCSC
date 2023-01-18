![image](https://user-images.githubusercontent.com/87138860/213167867-f97b0706-b6e5-49e0-aa9a-ba6abe6bd03b.png)


ý tưởng: xor 2 pic

script:



```py
from binascii import unhexlify

with open("1.jpg", mode='rb') as fl:
    lemur = fl.read()
    

with open("2.jpg", mode='rb') as ff:
    flag = ff.read()

d = b''
for b1, b2 in zip(lemur, flag):
    d += bytes([b1^b2])

with open("new.jpg", mode='wb') as fn:
    fn.write(d)
```
flag: KCSC{Da_bao_roi_cu_x%r_tung_byte_la_ra_ma_li}
