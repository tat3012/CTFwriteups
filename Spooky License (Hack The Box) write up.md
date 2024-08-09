# Spooky License
>author: xct
>After cleaning up we found this old program and wanted to see what it does, but we can't find the licence we had for it anywhere. Can you help?

![image](https://hackmd.io/_uploads/ryxzZ1a-D0.png)

![image](https://hackmd.io/_uploads/S1-f16WwA.png)
## script:
```python
from z3 import *

def solve_license():
    license_key = [BitVec(f"byte{i}", 8) for i in range(32)]

    solver = Solver()

    solver.add(license_key[29] == license_key[5] - license_key[3] + 70)
    solver.add(license_key[22] + license_key[2] == license_key[13] + 123)
    solver.add(license_key[4] + license_key[12] == license_key[5] + 28)
    solver.add(license_key[23] * license_key[25] == license_key[17] + license_key[0] + 23)
    solver.add(license_key[1] * license_key[27] == license_key[22] + license_key[5] - 21)
    solver.add(license_key[13] * license_key[9] == license_key[3] * license_key[28] - 9)
    solver.add(license_key[9] == 112)
    solver.add(license_key[21] + license_key[19] == license_key[6] + 0x80)
    solver.add(license_key[16] == license_key[15] - license_key[11] + 48)
    solver.add(license_key[27] * license_key[7] == license_key[13] * license_key[1] + 45)
    solver.add(license_key[13] == license_key[13] + license_key[18] - 101)
    solver.add(license_key[20] - license_key[8] == license_key[9] + 124)
    solver.add(license_key[31] == license_key[8] - license_key[31] - 121)
    solver.add(license_key[31] * license_key[20] == license_key[20] + 4)
    solver.add(license_key[24] - license_key[17] == license_key[8] + license_key[21] - 23)
    solver.add(license_key[5] + license_key[7] == license_key[29] + license_key[5] + 44)
    solver.add(license_key[10] * license_key[12] == license_key[1] - license_key[11] - 36)
    solver.add(license_key[0] * license_key[31] == license_key[26] - 27)
    solver.add(license_key[20] + license_key[1] == license_key[10] - 125)
    solver.add(license_key[18] == license_key[14] + license_key[27] + 2)
    solver.add(license_key[11] * license_key[30] == license_key[21] + 68)
    solver.add(license_key[19] * license_key[5] == license_key[1] - 44)
    solver.add(license_key[13] - license_key[26] == license_key[21] - 127)
    solver.add(license_key[23] == license_key[29] - license_key[0] + 88)
    solver.add(license_key[19] == license_key[13] * license_key[8] - 23)
    solver.add(license_key[22] + license_key[6] == license_key[3] + 83)
    solver.add(license_key[12] == license_key[7] + license_key[26] - 114)
    solver.add(license_key[16] == license_key[18] - license_key[5] + 51)
    solver.add(license_key[30] - license_key[8] == license_key[29] - 77)
    solver.add(license_key[20] - license_key[11] == license_key[3] - 76)
    solver.add(license_key[16] - license_key[7] == license_key[17] + 102)
    solver.add(license_key[21] + license_key[1] == license_key[18] + license_key[11] + 43)
    
    if solver.check() == sat:
        model = solver.model()
        solution = bytes([model[license_key[i]].as_long() for i in range(32)])
        print(f"Flag: {solution}")
    else:
        print("No Found Flag")

if __name__ == '__main__':
    solve_license()
```
![image](https://hackmd.io/_uploads/BywK1aZD0.png)

`flag: HTB{The_sp0000000key_liC3nC3K3Y}`