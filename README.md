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
   - **Định Nghĩa:** Dùng để định nghĩa, thay thế bằng 1 giá trị hoặc (chuỗi) khác
     - **Ví dụ 1:** : #define Pi 3.14 ( Sau quá trình tiền xử các thành phần có chứa Pi thì sẽ được chuyển thành giá trị 3.14 )
     - **Ví dụ 2:**
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
       

</details>

<details>
  <summary>📂 Bài 2: STDARG - ASSERT</summary>
</details>
  
