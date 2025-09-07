# How to create library for Arduino IDE

#### Author: Nguyen Thu Hang

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

Chọn New Tab và đặt tên file mới. Mình đặt tên là **"matcal.h"**.

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

Chọn New Tab và đặt tên file mới. Mình đặt tên là **"matcal.cpp"**. Đặt tên giống với file **.h**. Và phải thêm **#include "matcal.h"**.

Code của file **matcal.cpp** sẽ **giải thích rõ** các chức năng của các hàm trong file **matcal.h** là gì.


Code như sau:

```cpp
#include "matcal.h"

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

Thêm thư viện sau #include "matcal.h", và đoạn code như sau:

```cpp
#include "matcal.h"

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





