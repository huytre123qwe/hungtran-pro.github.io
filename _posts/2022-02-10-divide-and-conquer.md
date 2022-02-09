# Thuật toán chia để trị (Divide and Conquer).

![Ảnh mô tả chia để trị](/image/1-2.png)

## 1.Khái niệm:

- Như tên gọi của thuật toán, để giải quyết một bài toán ta thực hiện theo chiến lược như sau:

    - Chia nhỏ bài toán thành 2 hoặc nhiều bài toán con (Chia).

    - Giải quyết các bài toán con (Trị).

    - Kết hợp chúng để có được đầu ra mong muốn.

- Hai bài toán phổ biến nhất sử dụng thuật toán chia để trị là Tìm kiếm nhị phân và Quick-sort.

## 2.Ví dụ:

### 2.1 Tìm kiếm nhị phân.
Bài toán: Cho một mảng A gồm n phần tử A[1, 2, ...,n] đã được sắp xếp theo chiều tăng dần và một số nguyên x. Tìm vị trí của x trong mảng.

![Ảnh mô tả tìm kiếm nhị phân](/image/1_VwnVSmKLev2MMfcdBcWH1g.png)    

Với các bài toán tìm kiếm thông thường để tìm kiếm một phần tử trong danh sách đã được sắp xếp, chúng ta cần duyệt toàn bộ danh sách để tìm được vị trí tương ứng với độ phức tạp O(n).Tuy nhiên lợi dụng tính chất danh sách này đã được sắp xếp, ta có thể sử dụng Tìm kiếm nhị phân với Ο(log n) bằng cách sau:

- Bước 1(Chia): Danh sách ban đầu sẽ được chia thành 2 nửa.

- Bước 2 (Trị): Trong mỗi bước, so sánh phần tử cần tìm với phần tử nằm ở chính giữa danh sách. Nếu hai phần tử bằng nhau thì phép tìm kiếm thành công và thuật toán kết thúc. Nếu chúng không bằng nhau thì tùy vào phần tử nào lớn hơn, thuật toán lặp lại bước so sánh trên với nửa đầu hoặc nửa sau của danh sách.

- Bước 3: Bằng việc lặp lại cách giải quyết như bước 2 ta sẽ tìm được kết quả.

- Code:

```C++
 int binarySearch(int array[], int left, int right, int x)
{ 
    // nếu chỉ số left > right dừng lại và return -1 không có kết quả
    if (left > right) return -1;
    // tìm chỉ số ở giữa của mảng
    int mid = (left + right) / 2;
    
    // nếu số cần tìm bằng số ở giữa của mảng thì return
    if (x == array[mid]) 
        return mid;
    
    // nếu số cần tìm nhỏ hơn số ở giữa của mảng thì tìm sang nửa bên trái
    if (x < array[mid]) 
        return binarySearch(array, left , mid-1, x);

    // nếu số cần tìm lớn hơn số ở giữa của mảng thì tìm sang nửa bên phải
    if (x > a[mid]) 
        return binarySearch(a, mid+1 , right, x);
}
```
### 2.2 Nâng x lên lũy thừa n.

Bài toán: Tìm <img src="https://render.githubusercontent.com/render/math?math=x^{n}">
 
- Bước chia:
    
   -  <img src="https://render.githubusercontent.com/render/math?math=x^{n}=x^\frac{n}{2}.x^\frac{n}{2}"> nếu n chẵn.
        
   -  <img src="https://render.githubusercontent.com/render/math?math=x^{n}=x.x^\frac{n}{2}.x^\frac{n}{2}"> nếu n lẻ.
    
- Bước trị: Tính toán <img src="https://render.githubusercontent.com/render/math?math=x^\frac{n}{2}"> trong trường hợp x chẵn, <img src="https://render.githubusercontent.com/render/math?math=x.x^\frac{n}{2}"> trong trường hợp x lẻ.
 
- Bước tổng hợp. Kết quả chính là <img src="https://render.githubusercontent.com/render/math?math=x^\frac{n}{2}.x^\frac{n}{2}"> nếu n chẵn trong <img src="https://render.githubusercontent.com/render/math?math=x.x^\frac{n}{2}.x^\frac{n}{2}"> trường hợp x lẻ. 

- Code:

```C++
// Cách 1:
 int power(int x, unsigned int n)
 {
    if( n == 0)
        return 1;
    else if (n%2 == 0)
        return power(x, n/2)*power(x, n/2);
    else
        return x*power(x, n/2)*power(x, n/2); 
}

// Cách 2:
int power(int x, unsigned int n) 
{
    int temp;
    if( n == 0)
        return 1;
    temp = power(x, n/2);
    if (n%2 == 0)
        return temp*temp;
    else
        return x*temp*temp;
}
```

## 3. Một số lưu ý khi áp dụng giải thuật Chia để trị.

- Làm thế nào để chia tách bài toán một cách hợp lý thành các bài toán con, bởi vì nếu các bài toán con được giải quyết bằng các thuật toán khác nhau thì sẽ rất phức tạp.

- Việc kết hợp lời giải các bài toán con được thực hiện như thế nào.

## 4. Một số ứng dụng của thuật toán

- Tìm kiếm nhị phân.

- Giải thuật sắp xếp hợp nhất.

- Giải thuật sắp xếp nhanh.

- Phép nhân ma trận Strassen.

- Thuật toán Karatsuba.
