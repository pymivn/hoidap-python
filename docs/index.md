# Hỏi đáp Python

Tổng hợp những câu hỏi kỹ thuật hay được hỏi và trả lời tại lớp học Python
https://pymi.vn

## Tại sao khi có một list A, sau đó gán `B = A`, rồi thay đổi A thì B thay đổi theo.

`A` và `B` là 2 cái tên cho cùng 1 object. Khi thay đổi list A tức là thay đổi object mà list B cũng đang "buộc" vào (bound).

```
In [1]: A = [1,2,3,4]

In [2]: B = A

In [3]: A[0] = 3

In [4]: print(B)
[3, 2, 3, 4]

In [5]: id(A) == id(B)
Out[5]: True

In [6]: A is B
Out[6]: True
```

## Trong Python3, print('abc') trả về (return) gì?

`None`.

```
In [8]: out = print("Hello PYMI.VN")
Hello PYMI.VN

In [9]: out is None
Out[9]: True
```

## Tại sao sau `if` không cần dấu `(` mà len thì cần? `len()`?

`len` là function (hàm), `if` là statement (câu lệnh) tương tự với for/while/with/try.
