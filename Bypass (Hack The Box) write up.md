# Bypass
>author: Baikuya
>by: t4t3012
>The Client is in full control. Bypass the authentication and read the key to get the Flag.

Đầu tiên mình sẽ kiểm tra file thuộc loại nào
![image](https://hackmd.io/_uploads/ByMpYTzP0.png)
Nhìn ta có thể thấy file exe này được làm từ ngôn ngữ C#
nên ta sẽ debug nó bằng dnSpy
![image](https://hackmd.io/_uploads/HkAHcaGDR.png)
![image](https://hackmd.io/_uploads/ByyvqazwC.png)
Ta được 3 hàm chính là 0(), 1() và 2()
Để bypass qua username và password ta sẽ phải debug
![image](https://hackmd.io/_uploads/Sytyspzw0.png)
flag và flag 2 như là username với password
ta chỉ cần set bay thằng vô `global::0.2();`
![image](https://hackmd.io/_uploads/Hk4VspzvA.png)
Mình sẽ nhập đại key vậy
cứ như vậy mà cứ set vào `Console.Write(5.5 + global::0.2 + 5.6);`
khi ta tiếp tục chương trình sẽ hiện như sau:
![image](https://hackmd.io/_uploads/SkaispGwR.png)
`flag: HTB{SuP3rC00lFL4g}`