# Pizza
## Script:
```python
text = "9,4,6,8.6.2,9.2,;.2,9.9,2,2,7.3,4,7.2,2,9.4,7.3,3.7,9.1,9,4.0,9.8."
ans =""
for i in range(0,len(text),2):
    if(text[i+1]=='.'):
        for j in range(0,127):
            if(chr(j//2)==text[i] and j%2==0):
                ans+=chr(j)
                break
    else:
        for j in range(0,127):
            if(chr(j//2)==text[i]and j%2!=0):
                ans+=chr(j)
                break
print(ans)
```
flag: `grodno{simplereverseengineeringforcsharp}`