# Encryption Bot
>author: 0xrakesh
>by: t4t3012
>My friend send me a encrypted message by using encryption bot. This is a important message. Can you decrypt the message for me?

![image](https://hackmd.io/_uploads/BJ20zhzv0.png)

![image](https://hackmd.io/_uploads/HkTgX2Mv0.png)

![image](https://hackmd.io/_uploads/ByhZ73fPA.png)

![image](https://hackmd.io/_uploads/r1ozm3GwC.png)

![image](https://hackmd.io/_uploads/HyyEm2fwA.png)

![image](https://hackmd.io/_uploads/BkPNmhzDC.png)

![image](https://hackmd.io/_uploads/SkMSQnfv0.png)

## script:
```python
info = lambda x :print(f'[+] {x}')


def flag_enc_to_index():
    for i in range(36):
        for j,char in enumerate(string):
            if flag_enc[i] == string[j]:
                reverse_flag_int[i] = j

def index_to_binary(num, index):
    for i in reversed(range(6)):
        bits[i+index] = num % 2
        num= num // 2

def binary_to_str(index):
    sum = 0
    for j in reversed(range(8)):
        sum += bits[j+index] * REVERSE_FIVE53AB(j)
    flag_int[index//8] = sum        

def REVERSE_FIVE53AB(j):
    num = 129
    for i in range(j):
        num //=2

    return num 

if __name__ == '__main__':
    bits = [0 for i in range(216)]
    flag_enc = input()
    string = "RSTUVWXYZ0123456789ABCDEFGHIJKLMNOPQabcdefghijklmnopqrstuvwxyz"
    reverse_flag_int = [0 for i in range(36)]
    flag_int = [0 for i in range(27)]
    FLAG = ''

    flag_enc_to_index()

    for i in range(36):
        index_to_binary(reverse_flag_int[i], i*6)
    

    for i in range(27):
        binary_to_str(i*8)
    
    
    for i in range(27):
        FLAG += chr(flag_int[i])
    
    
    info(f'Flag is {FLAG}')
```
![image](https://hackmd.io/_uploads/ry_B43zw0.png)

`flag: HTB{3nCrypT10N_W1tH_B1Ts!!}`