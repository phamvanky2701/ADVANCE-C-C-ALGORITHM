# ADVANCE C/C++ AND ALGORITHM

<details>
  <summary>📂 Bài 1: Compiler + Macro</summary>
  
  ## Compiler
  **Định Nghĩa:** Compiler là quá trình chuyển đổi từ ngôn ngữ bậc cao (C, C++, Java...) sang ngôn ngữ bậc thấp (mã máy - 00011101), giúp chương trình hiểu và thực thi được.
  
  **Quá Trình Compiler:**
    <img src="https://s3-sgn09.fptcloud.com/codelearnstorage/Media/Default/Users/Darksider/ssj/maxresdefault.jpg">

   
  Quá trình biên dịch gồm 4 giai đoạn:
  
  - **Preprocessing (Tiền xử lý):**
    - Xử lý các lệnh bắt đầu bằng dấu `#` (Ví dụ: `#include <stdio.h>`, `#define`, `#if`...)
    - Thay thế các macro đã được định nghĩa trước (Ví dụ: `#define Pi 3.14`)
    - Xóa bỏ comment (chú thích)
    - Xử lý các điều kiện của tiền chỉ thị (`#if`, `#ifelse`, `#ifdef`, `#undef`...)
    - **Cú pháp chạy:**
      ```sh
      gcc -E tenfile.c -o tenfile.i
      ```
  
  - **Compiler:**
    - Chuyển đổi từ `file.i` sang `file.s`
    - Phân tích cú pháp, kiểm tra lỗi
    - Tối ưu mã nguồn giúp chương trình hoạt động hiệu quả hơn
    - **Cú pháp chạy:**
      ```sh
      gcc -S tenfile.i -o tenfile.s
      ```
  
  - **Assembling:**
    - Chuyển từ `file.s` sang `file.o`
    - Trình dịch assembler chuyển assembly code thành mã máy (000110010)
    - **Cú pháp chạy:**
      ```sh
      gcc -c tenfile.s -o tenfile.o
      ```
  
  - **Linking:**
    - Chuyển từ `file.o` sang `file.exe`
    - Liên kết các file lại với nhau
    - **Cú pháp chạy:**
      ```sh
      gcc tenfile.o -o tenfile
      ```
  
  ## Macro
  **Định Nghĩa:** Macro là các từ khóa định nghĩa hoạt động trong giai đoạn tiền xử lý (Preprocessing). Có 3 nhóm chính:
  - `#include`
  - `#define`, `#undef`
  - `#if`, `#elif`, `#else`, `#ifdef`, `#ifndef`
  
  **#include:**
  - **Định Nghĩa:** Dùng để chèn nội dung của một file vào file khác.
  
  - **Ví dụ:**
    #### File1.c
    ```c
    void Tong(int a, int b){
        printf("Tong: a + b = %d", a + b);
    }
    ```
   
    #### File2.c
    ```c
    #include <stdio.h>
    #include "File1.c"
    
    int main(){
        Tong(2, 3);
        return 0;
    }
    ```
  
  - **Ưu điểm:**
    - Tái sử dụng mã nguồn, tránh lặp code không cần thiết
    - Quản lý file chương trình hiệu quả
  
  - **Lưu ý:**
    - `#include <stdio.h>`: Dùng để gọi thư viện chuẩn của C
    - `#include "file.c"`: Dùng để gọi file tự định nghĩa
    - Không được `#include` hai file giống nhau trong cùng một mã nguồn

   **#define:**
  - **Định Nghĩa:** Dùng để định nghĩa lại 1 khái niệm, bằng các giá trị, chuỗi đơn giản hơn.
   - 
   - **Ứng dụng:**
   - Dùng để định nghĩa, thay thế bằng 1 giá trị hoặc (chuỗi) khác đơn giản hơn 
   - Dùng để tạo nhiều hàm, có cấu trúc giống nhau, tối ưu chương trình hơn 
   - Kết hợp với toán tử ## dùng để nối chuỗi 
   - Sử dụng toán tử # để chuyển 1 định dạng bất kỳ thành chuỗi 

     - **Ví dụ 1:**  #define Pi 3.14 ( Sau quá trình tiền xử các thành phần có chứa Pi thì sẽ được chuyển thành giá trị 3.14 )
     - **Ví dụ 2:** Dùng để tạo nhiều hàm, có cấu trúc giống nhau
#### main.c
  ```c
    #include <stdio.h>  
    
    #define FULL_NAME(name,cmd)   \
    void name (){                    \
        printf(cmd);                  \
    }

    FULL_NAMEC(test1,"Nguyen Cong Phuong\n");
    FULL_NAME(test2,"Pham Van Ky\n");
```

#### main.i
  ```c
void test1 (){ printf("Nguyen Cong Phuong\n"); };
void test2 (){ printf("Pham Van Ky\n"); };
```
- **Ví dụ 3:** Kết hợp với toán tử ## dùng để nối chuỗi
#### main.c
  ```c
    #define FULL_NAME(name)   \
     int int_##name ;             \
     float float_##name

     FULL_NAME(Tong); // Dùng để tạo ra nhiều biến mới, có cùng kiểu dữ liệu 
```

#### main.i
  ```c
int int_Tong ;
float float_Tong;
```
- **Ví dụ 4:** Sử dụng toán tử # để chuyển 1 định dạng bất kỳ thành chuỗi
#### main.c
  ```c
    #define FULL_NAME2(name)   \
    printf(#name)

   FULL_NAME(LeHungAnh); 
```

#### main.i
  ```c
    printf("LeHungAnh");
```

**#unfine:** 
- **Định Nghĩa:** Dùng để hủy 1 macro đã được định nghĩa trước đó 
-**Ví dụ:** 
#### main.c
  ```c
#include <stdio.h>

// undef dùng để hủy 1 macro đã định nghĩa trước đó
#define HCN 50 

int main(){
    printf("Hinh Chu Nhat : %d\n", HCN);

#undef HCN 
#define HCN 30

   printf("Hinh Chu Nhat : %d\n", HCN);
}
```

#### main.c
  ```c
Hinh Chu Nhat : 50
Hinh Chu Nhat : 30
```

**#ifndef:** 
- **Định Nghĩa:** 
- Dùng để kiểm tra xem 1 macro đã được định nghĩa chưa, nếu chưa định nghĩa thì nó sẽ được định nghĩa lại ở phía dưới chương trình
- Dùng để tránh lặp mã nguồn của chương trình

- **Ví dụ:**
#### main.c
  ```c
#include <stdio.h>

#ifndef HCN // Dùng để kiểm tra HCN đã được định nghĩa chưa nếu chưa thì sẽ được định nghĩa lại và chương trình [#inndef - #endif], được thực thi !!!
#define HCN 5

int arr[HCN] ={1,2,3,4,9};

#endif // Kết thúc chỉ thị điều kiện

```

**#ifdef:** 
- **Định Nghĩa:** Dùng để kiểm tra xem 1 macro đã được định nghĩa chưa, nếu chưa định nghĩa thì chương trình phía dưới không thực thi

- **Ví dụ:**
#### main.c
  ```c
#include <stdio.h>

#define HCN 5
#ifdef HCN // Dùng để kiểm tra HCN đã được định nghĩa chưa nếu chưa định nghĩa thì chương trình [#inndef - #endif] sẽ không được thực thi !!!

int arr[HCN] ={1,2,3,4,9};

#endif // Kết thúc chỉ thị điều kiện

```

**#if, #elif, #else #endif:** 
- **Định Nghĩa:** 
  - #if sử dụng để bắt đầu một điều kiện tiền xử lý.
  - Nếu điều kiện trong #if là đúng, các dòng mã nguồn sau #if sẽ được biên dịch
  - Nếu sai, các dòng mã nguồn sẽ bị bỏ qua đến khi gặp #endif
  - #elif dùng để thêm một điều kiện mới khi điều kiện trước đó là #if hoặc #elif là sai
  - #else dùng khi không có điều kiện nào ở trên đúng





</details>

<details>
  <summary>📂 Bài 2: STDARG - ASSERT</summary>

## I. Thư Viện Stdarg
### a. Khái niệm
Thư viện `stdarg` được ứng dụng cho các trường hợp làm việc với các hàm có số lượng input đầu vào không cố định.

### b. Cấu trúc của thư viện stdarg

- `va_list`: Là một kiểu dữ liệu trong C, được định nghĩa trong thư viện `<stdarg.h>`, dùng để xử lý danh sách các đối số có số lượng không xác định (variadic arguments).

#### **Cú pháp:**
```c
va_list tenbien;
```
Ví dụ:
```c
void Tong (int sum, ...){ // … : 4,5,3.14, "hello"
    va_list args; // Tạo một biến args kiểu dữ liệu char*
}
```

- `va_start`: Khởi tạo danh sách đối số, loại bỏ các thành phần trước dấu `...` và giữ lại các thành phần sau `...`.

#### **Cú pháp:**
```c
va_start(tenbien, tenbienloaibo);
```
Ví dụ:
```c
void Tong (int sum, ...){
    va_list args;
    va_start(args, sum); // Loại bỏ các thành phần trước '...', giữ lại các đối số sau '...'
}
```

- `va_arg`: Lấy ra từng đối số (mỗi lần gọi sẽ lấy ra một đối số).

#### **Cú pháp:**
```c
va_arg(tenbien, kieudulieu);
```
Ví dụ:
```c
void Tong (int sum, ...){
    va_list args;
    va_start(args, sum);
    
    printf("[1] = %d\n", va_arg(args, int));
    printf("[2] = %d\n", va_arg(args, int));
    printf("[3] = %.2f\n", va_arg(args, double));
    printf("[4] = %s\n", va_arg(args, char*));
}
```

- `va_end`: Kết thúc chương trình

#### **Cú pháp:**
```c
va_end(tenbien);
```

### **Ứng dụng:**
- Giải quyết các bài toán không xác định được số lượng tham số đầu vào.

---

## **Ví dụ 1: Tính tổng với số lượng tham số không cố định, nhưng biết được số lượng tham số truyền vào cho 1 lần tính toán**

### **Ý tưởng:**
Làm sao để giải quyết bài toán, tính tổng khi biết số lượng truyền vào không cố định, khi thì truyền 3 tham số , khi thì truyền 4 tham số, nhưng để giải quyết bài toán này ? Thư viện Stdarg sẽ hỗ trợ và giải quyết bài toán này, để giải quyết bài toán Ví dụ 1 này ta cần biết số lượng tham số truyền vào trong 1 lần tính.

```c
#include <stdio.h>
#include <stdarg.h>

void sum(int count, ...){
    va_list args;
    va_start(args, count);
    
    int tong = 0;
    for (int i = 0; i < count; i++){
        tong += va_arg(args, int);
    }
    
    va_end(args);
    printf("Sum = %d", tong);
}

int main(){
    sum(4, 4, 5, 6, 7);
}
```

---

## **Ví dụ 2: Không cần biết trước số lượng tham số 1 lần truyền vào, cho 1 lần tính toán**
### **Ý tưởng:**
Thêm số `0` vào cuối tham số truyền vào để làm điều kiện dừng vòng lặp.

```c
#include <stdio.h>
#include <stdarg.h>

#define tong(...) sum(__VA_ARGS__, 0)

void sum(int count, ...){
    va_list args;
    va_start(args, count);
    
    int result = count;
    int value;
    while ((value = va_arg(args, int)) != 0){
        result += value;
    }
    
    printf("Sum = %d", result);
    va_end(args);
}

int main(){
    tong(1, 2, 3, 4);
}
```

---

## **Ví dụ 3: Xử lý khi input truyền vào chứa số 0, không phải ở cuối**
### **Ý tưởng:**
Sử dụng một ký hiệu đặc biệt thay vì số `0` để đánh dấu điểm kết thúc.

```c
#include <stdio.h>
#include <stdarg.h>

#define tong(...) sum(__VA_ARGS__, "a")

int sum(int count, ...){
    va_list args;
    va_list args1;
    
    va_start(args, count);
    va_copy(args1, args);
    
    int result = count;
    while ((va_arg(args1, char*)) != (char*)"a"){
        result += va_arg(args, int);
    }
    
    va_end(args);
    return result;
}

int main(){
    printf("Sum = %d", tong(1, 2, 3, 4));
}
```

---

## II. Thư Viện `assert`
### **Khái niệm:**
- `assert` là một macro có sẵn trong thư viện `<assert.h>`.
- Dùng để kiểm tra chương trình và báo lỗi nếu điều kiện không đúng.
- Nếu điều kiện kiểm tra đúng, chương trình tiếp tục thực thi bình thường, nếu sai, chương trình sẽ dừng lại và báo lỗi.
- Được sử dụng chủ yếu để debug chương trình.

### **Ví dụ:**
```c
#include <stdio.h>
#include <assert.h>

int tong(int a, int b){
    int sum = a + b;
    assert(sum == 5 && "Gia Tri Sum Phai Bang 5 !!!");
    printf("sum = %d", sum);
}

int main(){
    tong(7, 3);
}
```

---


</details>
  
