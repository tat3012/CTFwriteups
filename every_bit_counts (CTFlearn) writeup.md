# every_bit_counts
>author: kcbowhunter
>
Bài này ta bắt buộc phải dùng angr

![image](https://hackmd.io/_uploads/By1TU2ZwR.png)

![image](https://hackmd.io/_uploads/S1J2L2ZDR.png)

## script:
```python
import angr
import claripy

def main():

    binary_path = './every_bit_counts'

    project = angr.Project(binary_path, auto_load_libs=False)

 
    input_size = 52 
    input_symbolic = claripy.BVS('input_symbolic', input_size * 8)

   
    initial_state = project.factory.entry_state(args=[binary_path, input_symbolic])

    
    for byte in input_symbolic.chop(8):
        initial_state.solver.add(byte >= 0x20)  
        initial_state.solver.add(byte <= 0x7E)  
    
   
    simulation = project.factory.simulation_manager(initial_state)

    
    success_address = 0x004035D1  
    failure_address = 0x004035EF 

    
    simulation.explore(find=success_address, avoid=failure_address)

    
    if simulation.found:
        solution_state = simulation.found[0]
        solution = solution_state.solver.eval(input_symbolic, cast_to=bytes)
        print(f"Found solution: {solution}")
    else:
        print("No solution found")

if __name__ == '__main__':
    main()
```
![image](https://hackmd.io/_uploads/SyL48nZPA.png)

flag = `CTFlearn{w0w_you_f0und_My_fl@g_y0u_Ar3_so_much_n1c3}`