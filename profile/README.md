# 🚀 TOR Monitor - Tactical Opname Restock Monitor

> Optimalkan modal UMKM Anda dengan strategi restock yang cerdas dan berbasis AI.

---

## 📌 Tentang Aplikasi

**TOR Monitor** adalah solusi manajemen stok barang yang dirancang khusus untuk membantu pelaku usaha, terutama UMKM, dalam memonitor dan mengelola inventori dengan lebih efisien. 

Kami memahami tantangan utama yang dihadapi UMKM: **keterbatasan modal**. Dari permasalahan tersebut, kami menciptakan fitur unggulan **"Tactical Opname Restock (TOR)"** untuk membantu Anda mengoptimalkan penggunaan modal dalam pengisian kembali stok barang.

### 🎯 Visi
Memberdayakan UMKM agar penggunaan modal lebih **bijak**, **tepat**, dan **efisien**.

---

## ⚡ Fitur Utama

### 1. 📊 Forecasting Restock Otomatis
- Prediksi kebutuhan restock produk berbasis data historis penjualan
- Menggunakan **XGBoost ML** untuk akurasi tinggi
- Identifikasi produk dengan stok rendah secara real-time
- Rekomendasi jumlah restock yang optimal

### 2. 📦 Manajemen Stok Barang via Web
- Dashboard interaktif untuk monitoring stok real-time
- Input/update stok barang dengan mudah
- Tracking kategori produk dan harga
- Laporan penjualan dan profitabilitas

### 3. 💬 AI Chat Interaktif
- Asisten virtual berbasis AI untuk menjawab pertanyaan bisnis
- Analisis tren penjualan dan rekomendasi strategi
- Natural Language Processing untuk komunikasi natural

---

## 💡 Keunggulan TOR Monitor

| Keunggulan | Deskripsi |
|-----------|-----------|
| 🤖 **AI-Powered Forecasting** | Prediksi akurat menggunakan machine learning dengan parameter yang sudah dituning, bukan sekadar rumus statistik |
| 💰 **Optimasi Modal** | Restock cerdas berarti tidak ada modal terbuang untuk stok berlebihan |
| ⏱️ **Real-time Dashboard** | Pantau stok kapan saja, di mana saja via web |
| 📈 **Data-Driven Decision** | Setiap keputusan restock didukung oleh data dan prediksi AI |
| 🎯 **User-Friendly** | Interface intuitif yang mudah digunakan tanpa training khusus |
| 🚀 **Scalable** | Infrastruktur yang dapat menangani pertumbuhan bisnis Anda |

---

## 🛠️ Tech Stack

### **Frontend**
- ⚛️ **TanStack** - Framework React modern untuk UI responsif

### **Backend**
- 🐍 **FastAPI** - API framework Python yang cepat dan scalable
- 🧠 **Langchain** - Framework untuk orchestration AI agents

### **AI & Machine Learning**
- 🤖 **Groq AI** - LLM untuk chat interaktif dan natural language processing
- 🌳 **XGBoost** - Gradient boosting untuk forecasting akurat

### **Database & Infrastructure**
- 🗄️ **PostgreSQL** (via Supabase) - Database relasional yang reliable
- 🔐 **Supabase Auth** - Authentication dan authorization
- 🔄 **Alembic** - Migration management untuk database schema

### **ORM & Utilities**
- 📝 **SQLModel** - Kombinasi SQLAlchemy + Pydantic untuk type-safe queries

---

## 🔍 Mengapa XGBoost untuk Forecasting?

### Dibanding Statistical Methods (Moving Average, Exponential Smoothing, dll):

#### **1. Akurasi Lebih Tinggi**
```
Moving Average:      Hanya mengambah rata-rata nilai terakhir → kurang fleksibel
XGBoost:             Belajar dari pola kompleks data → prediksi lebih akurat
```
Referensi: [Comparing statistical and machine learning methods for time series forecasting in data-driven logistics](https://arxiv.org/html/2303.07139v2#S5), [XgBoost Hyper-Parameter Tuning Using Particle Swarm
Optimization for Stock Price Forecasting
](https://eprints.uad.ac.id/61736/1/24-XgBoost%20Hyper-Parameter%20Tuning%20Using%20Particle%20Swarm%20Optimization%20for%20Stock%20Price%20Forecasting.pdf)

#### **2. Handling Non-Linear Patterns**
- **Statistical Methods**: Asumsi hubungan linear antara waktu & penjualan
- **XGBoost**: Capture pola kompleks (seasonality, trend break, anomali)
- Contoh: Penjualan yang naik drastis saat hari raya atau promo spesial

#### **3. Feature Engineering**
- **Statistical Methods**: Hanya menggunakan nilai historis
- **XGBoost**: Bisa memanfaatkan multiple features (kategori, harga, musim, dll), lalu memperkaya data dengan teknik sliding window
- Hasil: Prediksi lebih kontekstual & relevan dengan bisnis

#### **4. Adaptability terhadap Perubahan**
- **Statistical Methods**: Perlu re-tuning manual saat pola berubah
- **XGBoost**: Self-learning, adaptif terhadap trend baru dengan retrain berkala, cepat, ringan namun tetep presisi

#### **5. Real-World Performance**
- **Statistical Methods**: RMSE/MAE yang lebih tinggi (~15-25% error)
- **XGBoost**: Error rate lebih rendah (~5-10%) dengan proper tuning

### 📊 Ringkas Perbandingan

| Aspek | Moving Average | Exponential Smoothing | XGBoost |
|-------|---------------|-----------------------|---------|
| Akurasi | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Non-linear Pattern | ❌ | ⚠️ | ✅ |
| Multi-feature Support | ❌ | ❌ | ✅ |
| Maintenance | Manual | Semi-auto | Auto-learning |
| Use Case | Simple trend | Seasonal data | Complex business |

---

## 🎬 Cara Kerja Sistem

```
┌─────────────────────────────────────────────────────────┐
│  User Interface (Next.js)                               │
│  ├── Dashboard Stok                                      │
│  ├── Input Penjualan & Restock                           │
│  └── Chat AI                                             │
└────────────────┬────────────────────────────────────────┘
                 │ HTTP/REST
┌────────────────▼────────────────────────────────────────┐
│  API Backend (FastAPI)                                  │
│  ├── Auth Router (Supabase)                              │
│  ├── Goods & Sales Management                            │
│  ├── Forecast Router                                     │
│  └── Chat Router (Langchain Agent)                       │
└────────────────┬────────────────────────────────────────┘
                 │
    ┌────────────┼────────────┐
    │            │            │
    ▼            ▼            ▼
┌────────┐  ┌──────────┐  ┌──────────┐
│Database│  │ XGBoost  │  │ Groq AI  │
│(Postgres)│  │ Forecaster│  │ (Chat)  │
└────────┘  └──────────┘  └──────────┘
```

---

## Mari bersama-sama memberdayakan UMKM Indonesia!

