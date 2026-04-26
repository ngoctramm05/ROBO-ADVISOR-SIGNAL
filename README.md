# ROBO-ADVISOR-SIGNAL
## 1. Thông tin dự án
- Tên dự án: Robo-Advisor Trading Bot
- Ngôn ngữ: Python
- Nền tảng: Bitget Spot API
- Mục đích: Phân tích dữ liệu thị trường và tạo tín hiệu giao dịch tự động
## 2. Mô tả hệ thống
Hệ thống là một bot phân tích thị trường tài chính theo thời gian thực, sử dụng dữ liệu giá và khối lượng từ Bitget API.
Bot thực hiện:
- Thu thập dữ liệu nến (candlestick)
- Tính toán các chỉ báo kỹ thuật
- Xác định tín hiệu giao dịch
- Hiển thị kết quả trên terminal
- Gửi thông báo qua Telegram
## 3. Dữ liệu sử dụng
- Nguồn: Bitget Public API
- Loại dữ liệu:
  - Giá đóng cửa (Close price)
  - Khối lượng giao dịch (Volume)
  - Timestamp
- Khung thời gian: 5 phút
## 4. Danh sách tài sản theo dõi
Hệ thống chỉ theo dõi các token thuộc nhóm Tokenized US Stocks trên Bitget:
AAPLon, ABNBon, ACNon, ADBEon, AMDon, APPon, AVGOon, AXPon, BAon, BIDUon, CMGon, COINon, COSTon, CRCLon, CRMon, DASHon, DISon, EQIXon, FIGon, FUTUon, GEon, GMEon, GOOGLon, GSon, HIMSon, HOODon, INTCon, INTUon, JDon, LINon, MAon, MARAon, METAon, MRVLon, MSFTon, MSTRon, MUon, NFLXon, NOWon, NVDAon, PANWon, PBRon, PLTRon, PYPLon, RDDTon, RIOTon, SBETon, SHOPon, SPGIon, SPOTon, TSLAon, TSMon, UNHon, WFCon
## 5. Phương pháp phân tích
### 5.1 EMA (Exponential Moving Average)
- EMA9: xu hướng ngắn hạn
- EMA21: xu hướng trung hạn
Tín hiệu:
- EMA9 cắt lên EMA21 → xu hướng tăng
- EMA9 cắt xuống EMA21 → xu hướng giảm
### 5.2 RSI (Relative Strength Index)
- RSI < 30: vùng quá bán
- RSI > 70: vùng quá mua
### 5.3 Volume
- So sánh volume hiện tại với trung bình 20 phiên
- Volume cao → xác nhận tín hiệu mạnh
## 6. Logic tạo tín hiệu
Hệ thống tạo tín hiệu theo điều kiện:
- BUY: EMA9 cắt lên EMA21 + RSI thấp
- SELL: EMA9 cắt xuống EMA21 + RSI cao
- WATCH BUY: xu hướng tăng + volume xác nhận
- WATCH SELL: xu hướng giảm + volume xác nhận
- HOLD: không có tín hiệu rõ ràng
## 7. Kết quả đầu ra
Khi chạy chương trình, hệ thống sẽ:
- Hiển thị giá và tín hiệu trên terminal
- In các chỉ số: RSI, EMA9, EMA21, Volume
- Cập nhật theo chu kỳ thời gian 30 giây
