# How to create library for Arduino IDE

#### Author: Nguyen Thu Hang

# A. Thêm thư viện trực tiếp trong folder
## 1. File .ino ban đầu không dùng thư viện

Mình đặt tên file là **tester.ino** được đặt trong folder **tester** (tên folder trùng tên file). Ban đầu, ta có đoạn code sau:

```cpp
long long add(int a, int b);

long long sub(int a, int b);

long long mul(int a, int b);

float division(int a, int b);

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  int cong = add(6, 8);
  int tru = sub(8, 6);
  int nhan = mul(2, 34);
  float chia = division(172, 2);
  Serial.println(cong);
  Serial.println(tru);
  Serial.println(nhan);
  Serial.println(chia);
}

void loop() {
  // put your main code here, to run repeatedly:
}

long long add(int a, int b){
  return a + b;
}

long long sub(int a, int b){
  return a - b;
}

long long mul(int a, int b){
  return a * b;
}

float division(int a, int b){
  return (float)a / b;
}
```

Vậy làm sao để thu gọn đoạn code lại? Phần tiếp theo chúng ta sẽ tạo thư viện **.h**.

## 2. Tạo thư viện .h

Trong giao diện của Arduino IDE, **góc bên phải phía trên** có dấu ba chấm. 

Chọn New Tab và đặt tên file mới. Mình đặt tên là **<matcal.h>**.

Khung ban đầu của thư viện **matcal.h** như sau:

```cpp
#ifndef MATHCAL_H
#define MATHCAL_H

#include <Arduino.h>


#endif
```

Ta nên thêm thư viện <Arduino.h> vì đây là thư viện của chúng ta tự tạo, nên không có sẵn như file thông thường.

Vì mình dùng thêm các hàm **add, sub, mul, division** nên ở thư viện **.h** mình cần khai báo thêm như sau:

```cpp
#ifndef MATHCAL_H
#define MATHCAL_H

#include <Arduino.h>

// them doan sau ===========
long long add(int a, int b);
long long sub(int a, int b);
long long mul(int a, int b);
float division(int a, int b);
// =========================

#endif
```

Phần tiếp theo, chúng ta cần tạo file .cpp

## 3. Tạo thư viện .cpp

Chọn New Tab và đặt tên file mới. Mình đặt tên là **"matcal.cpp"**. Đặt tên giống với file **.h**. Và phải thêm **#include <matcal.h>**.

Code của file **matcal.cpp** sẽ **giải thích rõ** các chức năng của các hàm trong file **matcal.h** là gì.


Code như sau:

```cpp
#include <matcal.h>

long long add(int a, int b){
  return a + b;
}

long long sub(int a, int b){
  return a - b;
}

long long mul(int a, int b){
  return a * b;
}

float division(int a, int b){
  return (float)a / b;
}
```

## 4. File tester.ino dùng thư viện

Sau khi đã tạo xong 2 file **matcal.cpp** và **matcal.h** thì việc tiếp theo là mình cần thêm thư viện và xóa phần đầu đi.

Thêm thư viện sau #include <matcal.h>, và đoạn code như sau:

```cpp
#include <matcal.h>

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  int cong = add(6, 8);
  int tru = sub(8, 6);
  int nhan = mul(2, 34);
  float chia = division(172, 2);
  Serial.println(cong);
  Serial.println(tru);
  Serial.println(nhan);
  Serial.println(chia);
}

void loop() {
  // put your main code here, to run repeatedly:

}
```
Và kết quả là code đã **gọn gàng** hơn rất nhiều, chúng ta chỉ cần gọi tên hàm **add, sub, mul** hay **division** là tính toán được.

# B. Thêm thư viện vào thư viện của Arduino

## 1. Cách folder thư viện của Arduino

Tải một thư viện bất kỳ trong **LIBRARY MANAGER** (hình chồng sách bên trái) trong giao diện của Arduino IDE.

Ví dụ tải thư viện "**tft_eSPI**". Sau tải xong nhấn tổ hợp phím "Window + S" rồi search **tft_eSPI** nhấn **Open file location**.

Vậy là đã tìm thấy chỗ để có thể thêm thư viện tự tạo.

## 2. Thêm thư viện vào

Đầu tiên, tạo folder tên **matcal**. Rồi "Ctrl + X" 2 file **matcal.h** và **matcal.cpp** vào trong folder matcal.

Rồi tắt phần mềm Arduino IDE và bật lại file **tester.ino** lúc này không còn 2 file cũ là **matcal.h** và **matcal.cpp**.

Nhấn **Verify** (dấu tích) ở bên trái phía trên. Chương trình được biên dịch không có lỗi.

Như vậy, chúng ta đã tạo thư viện thành công.

# C. Một số lỗi có thể gặp

1. Gọi nhầm tên thư viện

2. Tên của hàm bị trùng với tên đã được thiết lập sẵn (trước mình đặt biến tên **div** và bị lỗi nên mình đã đổi tên biến thành **division**)





