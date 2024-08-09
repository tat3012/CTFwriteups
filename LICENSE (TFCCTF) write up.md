# LICENSE
![image](https://hackmd.io/_uploads/H1kM1ToK0.png)
ta thấy rằng để có flag thì phải qua được 2 hàm `sub_1209` và `sub_1345` , src phải có 17 ký tự

![image](https://hackmd.io/_uploads/BJCOyaoFR.png)
Tại `sub_1209`

![image](https://hackmd.io/_uploads/Hk3KyasYC.png)
hàm `sub_1209` dùng để kiểm tra 8 ký tự đầu
## Script1:
```python=
def inputt(target):
    decimal_values = []
    for i in range(8):
        v1 = i % 3
        transformed_char = ord(target[i]) ^ 0x33
        if v1 == 2:
            input_char = transformed_char + 37
        elif v1 == 1:
            input_char = transformed_char - 16
        else:  # v1 == 0
            input_char = transformed_char ^ 0x5A
        decimal_values.append(input_char)
    return decimal_values


target = "Xsl3BDxP"
decimal_values = inputt(target)

print(decimal_values)

```
![image](https://hackmd.io/_uploads/HkeFw-aoYR.png)

Tại `sub_1345`
![image](https://hackmd.io/_uploads/ByaXWpsKA.png)
## Script2:
```python=
s = ""
n = "mzXaPLzR"
for i in range(8):
    a = ""
    for j in range(32, 127):
        if chr(j).islower():
            a = chr((j - 92) % 26 + 97)
        elif chr(j).isupper():
            a = chr((j - 48) % 26 + 65)
        if a == n[i]:
            s += chr(j)
            break
print(s)
```
![image](https://hackmd.io/_uploads/rk7s-TjFC.png)

ký tự giữa sẽ là '-'

![image](https://hackmd.io/_uploads/SyZAZaoKR.png)

vì 8 ký tự đầu khi nhập tay sẽ bị lỗi format nên phải dùng pwntools
## Script:
```python=
from pwn import *

p = remote("challs.tfcctf.com", 30257)
part1 = [49, 48, 132, 90, 97, 156, 17, 83]
s1 = b''.join(bytes([x]) for x in part1)
s2 = b"huGvYUuA"
mid = b'-'
print(len(s1+mid+s2))
p.sendline(s1 + mid + s2)
p.interactive() 
```
![image](https://hackmd.io/_uploads/S10LGpiFR.png)

flag: `TFCCTF{ac1da9096a8ad2fcb839565621bf09e892a470a6a7a0498b6259e09525096b9d}`
