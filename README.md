![tampilan desktop](https://github.com/user-attachments/assets/a3f42260-4af1-4e00-a4b6-46525553abd4)
# Sistem-Monitoring-Suhu-dan-Kelembaban
berdasarkan codingan diatas buatakan seperti ini 
## Instalasi

### 1. Clone Repository
```bash
[git clone https://github.com/karinamaharani81/Sistem-Monitoring-Suhu-dan-Kelembaban
cd proyek-monitoring-sensor
```

### 2. Install Python Dependencies
```bash
pip install tokio-modbus tokio-serial matplotlib requests chrono influxdb-client tkinter serde reqwest
```

### 3. Siapkan InfluxDB
- Jalankan atau instal InfluxDB v2 di localhost.
- Buat Organization, Bucket, dan Token

### 4. Konfigurasi Sensor Modbus RTU
Pastikan sensor terhubung melalui USB dan dapat membaca data dari register input 1 dan 2 (untuk suhu dan kelembaban)

### 5. Jalankan Server TCP
```bash
cargo run --bin tcp_server  # atau: cargo build && ./target/debug/tcp_server
```

### 5. Jalankan Client Pembaca Sensor
```bash
cargo run --bin modbus_client
```

## Usage

### 1. Monitoring Real-time dengan GUI
Jalankan antarmuka GUI berbasis Tkinter
```bash
python gui.py
```
#### Fitur GUI:
- Menampilkan data suhu dan kelembaban secara real-time dari InfluxDB.
- Menampilkan grafik historis berdasarkan waktu tertentu (format waktu RFC3339, contoh: 2025-05-30T08:00:00Z).

## Project Structure
```
proyek-monitoring-sensor/
├── tcp_server.rs         # Server TCP (menggunakan Tokio dan Reqwest)
├── modbus_client.rs      # Client pembaca sensor (Modbus RTU)
├── gui.py                # GUI Python (Tkinter + Matplotlib)
├── Cargo.toml            # Konfigurasi proyek Rust
└── README.md             # Dokumentasi proyek
```

## Perbaikan & Pengembangan Selanjutnya
- Tambahkan fitur logging untuk menyimpan semua data lokal.
- Tambahkan validasi waktu input di GUI.
- Tambahkan autentikasi dasar di TCP server.
- Tambahkan fitur export CSV dari data historis.
