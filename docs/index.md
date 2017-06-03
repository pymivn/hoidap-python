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

## Tại sao `0.1 + 0.1 + 0.1 != 0.3`?

Kiểu dữ liệu float (0.1, 0.3) là một dạng biểu diễn gần đúng của giá trị
số phức (có giá trị nó biểu diễn chính xác được, có giá trị thì không).
Khi ba số 0.1 (biểu diễn gần đúng) cộng lại với nhau,
giá trị nó tạo ra sẽ khác với 0.3 (biểu diễn chính xác).
Xem chi tiết ở [đây](http://pymi.vn/blog/why-not-float/)

## Tại sao `1e2 == 10**2` mà `1e69 != 10**69`?

Float là kiểu dữ liệu [biểu diễn gần đúng](http://pymi.vn/blog/why-not-float/):

```
In [6]: 1e69 == 10**69
Out[6]: False

In [7]: int(1e69)
Out[7]: 1000000000000000072531436381529235126158374409646521955518210155479040
```

## Các argument được pass dùng tham chiếu hay tham trị?

Python dùng [call-by-object-reference](http://pymi.vn/blog/call-by/)

## Hãy mô tả function overloading trong Python
Python không phải là C++! Python không cần và không có khái niệm
overloading.
Python là dynamic typing, theo style
[duck-typing](https://docs.python.org/3/glossary.html#term-duck-typing),
khi cần gọi function với các argument khác nhau/số lượng tuỳ ý, sử dụng
[`*args, **kwargs`](https://docs.python.org/3/tutorial/controlflow.html#arbitrary-argument-lists)

## Mô tả interface và abstract trong Python
Python không phải là Java! Python không có khái niệm interface, hay abstract
class như Java.
