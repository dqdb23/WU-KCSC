![image](https://user-images.githubusercontent.com/87138860/213168385-0980e304-ab6e-4cad-b69b-0143a550cfe9.png)

```
void __cdecl ENC(int a1, int a2, int a3, int a4)

push    ebp
mov     ebp, esp
mov     eax, [ebp+0Ch]
add     eax, [ebp+10h]
add     eax, [ebp+8]
mov     ecx, [ebp+14h]
add     ecx, 0Ah
xor     ecx, [ebp+8]
add     eax, ecx
xor     eax, [ebp+8]
push    eax             ; char
push    offset Format   ; "0x%x"
call    printf
add     esp, 8
pop     ebp
retn
```

Tính kết quả của hàm ENC(0xAB12DF34, 0x7B, 0x2D, 0x43):


Để hiểu assembly ta phải đọc từng dòng một. Ghi nhớ rằng mỗi giá trị trong assembly đều là  hexadecimal. 
Chúng ta sẽ lần lượt đẩy các giá trị trong hàm vào stack.

ebp           |.      esp
ebp+0x4  |.     Ret
ebp+0x8  |.    0xAB12DF34
ebp+0xc  |.     0x7B
ebp+0x10|.      0x2D
ebp+0x14|.      0x43


-mov eax, [ebp+0x0Ch] => eax= 0x7B
-add eax, [ebp+0x10h]
-add eax, [ebp+0x8] 
=> eax= eax+ 0xAB12DF34 + 0x2D = 0xAB12DFDC


-mov ecx, [ebp+0x43] => ecx = 0x43
-add ecx, 0Ah  => ecx = 0x43 + 0xA = 0x4D
-xor ecx, [ebp+0x8] => ecx = ecx xor 0xAB12DF34= 0xAB12DF79

-add eax,ecx => eax = eax+ecx = 0xAB12DFDC + 0xAB12DF79 = 0x5625BF55

-xor eax,[ebp+0x8] => eax = 0x5625BF55 xor 0xAB12DF34 = 0xFD376061
 
Tiếp đó ta đẩy eax(char) và format vào stack. Sau đó gọi hàm printf để in.
Việc thêm 8 vào esp là để giải phóng bộ nhớ trong stack.

flag: KCSC{0xfd376061}
