# 📌 Mục Lục

<details>
  <summary>📂 Bài 1: Compiler + Macro</summary>
  
  <details>
    <summary>📂 Compiler - Định Nghĩa</summary>
    Compiler là quá trình chuyển đổi từ ngôn ngữ bậc cao (C, C++, Java...) sang ngôn ngữ bậc thấp (mã máy - 00011101), giúp chương trình hiểu và thực thi được.
  </details>
  
  <details>
    <summary>📂 Quá Trình Compiler</summary>
    Quá trình biên dịch gồm 4 giai đoạn:
    
    <details>
      <summary>📂 Preprocessing (Tiền xử lý)</summary>
      - Xử lý các lệnh bắt đầu bằng dấu `#` (Ví dụ: `#include <stdio.h>`, `#define`, `#if`...)
      - Thay thế các macro đã được định nghĩa trước (Ví dụ: `#define Pi 3.14`)
      - Xóa bỏ comment (chú thích)
      - Xử lý các điều kiện của tiền chỉ thị (`#if`, `#ifelse`, `#ifdef`, `#undef`...)
      - **Cú pháp chạy:**
        ```sh
        gcc -E tenfile.c -o tenfile.i
        ```
    </details>
    
    <details>
      <summary>📂 Compiler</summary>
      - Chuyển đổi từ `file.i` sang `file.s`
      - Phân tích cú pháp, kiểm tra lỗi
      - Tối ưu mã nguồn giúp chương trình hoạt động hiệu quả hơn
      - **Cú pháp chạy:**
        ```sh
        gcc -S tenfile.i -o tenfile.s
        ```
    </details>
    
    <details>
      <summary>📂 Assembling</summary>
      - Chuyển từ `file.s` sang `file.o`
      - Trình dịch assembler chuyển assembly code thành mã máy (000110010)
      - **Cú pháp chạy:**
        ```sh
        gcc -c tenfile.s -o tenfile.o
        ```
    </details>
    
    <details>
      <summary>📂 Linking</summary>
      - Chuyển từ `file.o` sang `file.exe`
      - Liên kết các file lại với nhau
      - **Cú pháp chạy:**
        ```sh
        gcc tenfile.o -o tenfile
        ```
    </details>
  </details>

  <details>
    <summary>📂 Macro - Định Nghĩa</summary>
    Macro là các từ khóa định nghĩa hoạt động trong giai đoạn tiền xử lý (Preprocessing). Các nhóm chính:
    - `#include`
    - `#define`, `#undef`
    - `#if`, `#elif`, `#else`, `#ifdef`, `#ifndef`
  </details>
  
  <details>
    <summary>📂 #include</summary>
    <details>
      <summary>📂 Định Nghĩa</summary>
      Dùng để chèn nội dung của một file vào file khác.
    </details>
    
    <details>
      <summary>📂 Ví dụ</summary>
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
    </details>
    
    <details>
      <summary>📂 Ưu điểm</summary>
      - Tái sử dụng mã nguồn, tránh lặp code không cần thiết
      - Quản lý file chương trình hiệu quả
    </details>
    
    <details>
      <summary>📂 Lưu ý</summary>
      - `#include <stdio.h>`: Dùng để gọi thư viện chuẩn của C
      - `#include "file.c"`: Dùng để gọi file tự định nghĩa
      - Không được `#include` hai file giống nhau trong cùng một mã nguồn
    </details>
  </details>
</details>
