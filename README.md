# 📍 Geo-Notes Flutter - Ứng dụng ghi chú theo vị trí GPS

Ứng dụng **Flutter** cho phép bạn tạo ghi chú gắn với vị trí GPS, xem trên bản đồ và dẫn đường bằng Google Maps.  
Dữ liệu được lưu trữ **local trên thiết bị**.

## ✨ Tính năng

- ✅ Check-in và tạo ghi chú tại vị trí hiện tại
- ✅ Hiển thị các ghi chú trên bản đồ (Google Maps)
- ✅ Danh sách ghi chú hiển thị kèm khoảng cách từ vị trí của bạn
- ✅ Lọc ghi chú theo bán kính (1km → 50km hoặc tất cả)
- ✅ Dẫn đường đến vị trí ghi chú bằng Google Maps
- ✅ Xóa ghi chú
- ✅ Lưu dữ liệu local bằng **Shared Preferences / Hive**
- ✅ Reverse geocoding để hiển thị địa chỉ từ tọa độ GPS

## 🚀 Cài đặt môi trường

### 1. Yêu cầu
- Flutter SDK (stable)  
- Android Studio hoặc Xcode
- Thiết bị thật hoặc simulator/emulator

Kiểm tra Flutter:
```bash
flutter doctor
```

### 2. Clone dự án
```bash
git clone <repo-url>
cd geo_notes_flutter
```

### 3. Cài đặt dependencies
```bash
flutter pub get
```

### 4. Chạy ứng dụng
```bash
flutter run
```

## 📦 Dependencies chính

| Package | Chức năng |
|-------|-----------|
| `geolocator` | Lấy vị trí GPS hiện tại |
| `google_maps_flutter` | Hiển thị bản đồ và marker |
| `geocoding` | Reverse geocoding địa chỉ |
| `shared_preferences` hoặc `hive` | Lưu trữ dữ liệu local |
| `url_launcher` | Mở Google Maps để dẫn đường |

Cài đặt gói (nếu cần):
```bash
flutter pub add geolocator google_maps_flutter geocoding shared_preferences url_launcher
```

## 🔧 Cấu hình Google Maps API Key

### Android
Mở file:
```
android/app/src/main/AndroidManifest.xml
```
Thêm:
```xml
<meta-data
  android:name="com.google.android.geo.API_KEY"
  android:value="YOUR_API_KEY"/>
```

### iOS
Mở file:
```
ios/Runner/AppDelegate.swift
```
Thêm:
```swift
GMSServices.provideAPIKey("YOUR_API_KEY")
```

## 📱 Cấu trúc Project

```
lib/
├── screens/
│   ├── map_screen.dart          # Màn hình bản đồ với marker
│   ├── notes_screen.dart        # Danh sách ghi chú
│   └── add_note_screen.dart     # Tạo ghi chú mới
│
├── widgets/
│   ├── note_card.dart           # Widget hiển thị thông tin ghi chú
│   └── radius_filter.dart       # Dropdown chọn bán kính lọc
│
├── services/
│   ├── location_service.dart    # Lấy GPS + reverse geocoding
│   ├── navigation_service.dart  # Mở Google Maps dẫn đường
│   └── storage_service.dart     # Lưu/đọc dữ liệu local
│
├── models/
│   └── note.dart                # Model ghi chú
│
└── utils/
    └── distance.dart            # Tính khoảng cách giữa 2 tọa độ
```

## 🎯 Cách sử dụng

| Hành động | Thực hiện |
|--------|-----------|
| **Thêm ghi chú** | Nhấn nút `+` → nhập tiêu đề + mô tả |
| **Xem bản đồ** | Các ghi chú sẽ hiển thị bằng marker |
| **Lọc theo khoảng cách** | Chọn bán kính trong dropdown |
| **Dẫn đường** | Nhấn nút "Chỉ đường" trên card ghi chú |
| **Xóa ghi chú** | Bấm biểu tượng 🗑 trong danh sách ghi chú |

## 🔐 Quyền truy cập cần thiết

### Android
- ACCESS_FINE_LOCATION
- ACCESS_COARSE_LOCATION

### iOS
- NSLocationWhenInUseUsageDescription (thêm trong `Info.plist`)

## 🐛 Troubleshooting

| Lỗi | Cách khắc phục |
|----|----------------|
| Không lấy được GPS | Kiểm tra quyền location + bật GPS |
| Bản đồ không hiển thị | Kiểm tra API Key trong AndroidManifest / AppDelegate |
| Khoảng cách hiển thị sai | Kiểm tra hàm tính distance trong `utils/distance.dart` |

## 📄 License
MIT License — Tự do sử dụng cho dự án cá nhân và thương mại.
