* **Vị trí lỗi:** `const xeVaoSac = hangDoiXeCho.pop();`
* **Nguyên nhân kỹ thuật:** Phương thức `.pop()` xóa và trả về phần tử **ở cuối mảng** (xe mới tới sau cùng). Điều này vi phạm nguyên tắc điều phối **FIFO** (First In, First Out) của trạm sạc: Xe tới sớm nhất phải nằm ở chỉ số `0` và được phục vụ trước.
* **Giải pháp:** Đổi sang phương thức `.shift()` để rút đúng xe ở vị trí đầu tiên (chỉ số `0`).

* **Vị trí lỗi:** `for (let i = 0; i <= hangDoiXeCho.length; i++)`
* **Nguyên nhân kỹ thuật:** 
  * Ban đầu mảng có 3 phần tử. Sau khi rút 1 xe (`.shift()`) và thêm 1 xe mới (`.push('43D-88888')`), mảng vẫn có độ dài `length = 3` (gồm các index hợp lệ: `0, 1, 2`).
  * Việc dùng điều kiện `i <= length` khiến vòng lặp chạy đến `i = 3`. 
  * Tại `hangDoiXeCho[3]`, giá trị trả về là `undefined`, dẫn đến dòng chữ `STT 4: undefined` bị in ra bảng LED.
* **Giải pháp:** Sửa điều kiện dừng vòng lặp thành `i < hangDoiXeCho.length`.

