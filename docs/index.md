# Hỏi đáp Python

Tổng hợp những câu hỏi kỹ thuật hay được hỏi và trả lời tại lớp [học Python PyMIvn](https://pymi.vn),
cùng các câu hỏi phỏng vấn Python thường gặp 😏

## Tại sao khi có một list A, sau đó gán `Z = A`, rồi thay đổi A thì Z thay đổi theo.

`A` và `Z` là 2 cái tên cho cùng 1 object. Khi thay đổi list A tức là thay đổi object mà list Z cũng đang "buộc" vào (bound).

```
In [1]: A = [1,2,3,4]

In [2]: Z = A

In [3]: A[0] = 3

In [4]: print(Z)
[3, 2, 3, 4]

In [5]: id(A) == id(Z)
Out[5]: True

In [6]: A is Z
Out[6]: True
```

Xem chi tiết [cách name và binding hoạt động ở đây](https://pymi.vn/blog/call-by/#binding).

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
số thực (có giá trị nó biểu diễn chính xác được, có giá trị thì không).
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

## Tại sao trong một lần chạy id(-5) không đổi còn id(-6) thì lại thay đổi?
[CPython](https://pymi.vn/tutorial/python-la-gi/) lưu sẵn [(cache) giá trị các
số từ -5 đến 256](https://docs.python.org/3/c-api/long.html#c.PyLong_FromLong).
Vì vậy Python sẽ không tạo
ra một object mới mỗi lần dùng số trong khoảng này. Đây là tính chất có được
do cách tạo ra bản CPython,
không phải một tính năng của Python (không đúng với Jython, PyPy...).
Khi so sánh các số, hãy dùng `==` chứ đừng dùng `is`.

```python
n [3]: id(-5)
Out[3]: 4546887872

In [4]: id(-5)
Out[4]: 4546887872

In [5]: id(-6)
Out[5]: 4569471920

In [6]: id(-6)
Out[6]: 4569469616
```

## Các key trong dict có thứ tự thế nào?
Với Python2.7 -> Python3.5. Nếu ta viết code sau thì kết quả là gì

```python
for k in {1: 1, 2: 2, 1000: 1000, 8:8}:
     print(k)
```

Các key của dictionary không có thứ tự cụ thể. Nhưng không phải là ngẫu nhiên (tức đoạn code trên, nếu trên 1 máy tính, chạy 100 lần đều ra kết quả như nhau - nhưng trên máy khác có thể khác).

Bonus: Python3.6 sẽ ghi nhớ các key theo thứ tự chúng được add vào dictionary.

## Một tuple chứa 2 phần tử là 2 list có thể là key của dict không?
Tuple vốn là "immutable", đã tạo ra thì không thay đổi được, nhưng phần tử của nó là list, có thể thay đổi được -> tuple này trở thành mutable theo ý nghĩa: ta thay đổi được tuple đó chưa gì (mặc dù ở một câu sâu hơn, không phải thay đổi trực tiếp). Điều này khiến giá trị của tuple không cố định -> không lấy được "hash" -> không làm key của dict được.

## Tạo tuple chứa 1 phần tử là string 'Python'

Không phải là `('Python')`, mà phải có dấu phẩy sau nó để Python hiểu đây là tuple `('Python',)`

## Các argument được pass vào function dùng tham chiếu hay tham trị?

Python dùng [call-by-object-reference](http://pymi.vn/blog/call-by/)

## Mô tả function overloading trong Python
Python không phải là C++! Python không cần và không có khái niệm
overloading.
Python là dynamic typing, theo style
[duck-typing](https://docs.python.org/3/glossary.html#term-duck-typing),
khi cần gọi function với các argument khác nhau/số lượng tuỳ ý, sử dụng
[`*args, **kwargs`](https://docs.python.org/3/tutorial/controlflow.html#arbitrary-argument-lists)

## Mô tả interface và abstract trong Python
Python không phải là Java! Python không có khái niệm interface, hay abstract
class như Java. Nếu muốn, lập trình viên có thể sử dụng các thư viện cung cấp
các tính năng này như [ABC](https://www.python.org/dev/peps/pep-3119/).
