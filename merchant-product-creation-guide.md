# Merchant Product Creation Guide (The Wizard)

## 1. Product Discovery (Tanya dulu, jangan asumsi)

Daripada kasih dropdown teknis, kita tanya merchant dengan bahasa manusia.

**Q: "Halo! Produk apa yang ingin Anda jual hari ini?"**

> ### A. 🎫 Tiket Masuk (Entry Ticket)
> *   **Help:** "Untuk akses masuk ke tempat wisata tanpa pemandu."
> *   **Contoh:** Museum, Waterpark, Zoo, Observation Deck.
> *   **Key Feature:** Bebas datang jam berapa saja (seharian).

> ### B. 🏃 Aktivitas (Activity)
> *   **Help:** "Kegiatan partisipatif dengan instruktur dalam durasi pendek."
> *   **Contoh:** Rafting, Spa, Kursus Memasak, Photoshoot Adat.
> *   **Key Feature:** Durasi tertentu (1-4 jam) & ada instruktur.

> ### C. 🗺️ Tur & Perjalanan (Tour)
> *   **Help:** "Perjalanan wisata keliling dengan rute dan pemandu."
> *   **Contoh:** City Tour, Island Hopping, Hiking seharian.
> *   **Key Feature:** Pindah-pindah lokasi & ada itinerary.

---

## 2. Validation Check (Double Check biar gak salah kamar)

Setelah merchant pilih, system validasi satu kali lagi.

### Skenario A: Pilih "Tiket Masuk" 🎫
*System check:*
> "Apakah tamu perlu **reservasi jam kedatangan** secara spesifik?"
> - **Tidak** → Confirm **Attraction**.
> - **Ya** → Saran: *"Sebaiknya pilih **Activity**, karena produk Anda butuh slot waktu."*

### Skenario B: Pilih "Aktivitas" 🏃
*System check:*
> "Apakah aktivitas ini melibatkan **pindah-pindah lokasi** (sightseeing) seharian?"
> - **Tidak** → Confirm **Activity**.
> - **Ya** → Saran: *"Sebaiknya pilih **Tour**, karena produk Anda punya rute perjalanan."*

---

## 3. The Input Wizard (Isi yang perlu aja)

### Form Khusus: Attraction 🎫
*Fokus: Validitas & Cara Masuk*

1.  **Validity Type:**
    *   [ ] **Fixed Date** *(Hanya berlaku di tanggal terpilih. Contoh: Konser)*
    *   [ ] **Open Date** *(Bebas dipakai kapan saja dalam 30 hari. Contoh: Ancol)*
2.  **Redemption:**
    *   [ ] **Direct Entry** *(Scan QR di gerbang atau langsung tunjukin e-ticket)*
    *   [ ] **Exchange** *(Tukar voucher tiket fisik di loket)*

### Form Khusus: Activity 🏃
*Fokus: Jadwal & Kapasitas*

1.  **Duration:**
    *   *Help: "Berapa lama aktivitas berlangsung?" (Contoh: 2 Jam)*
2.  **Schedules / Slots:**
    *   *Help: "Jam berapa saja sesi dimulai?" (Contoh: 09:00, 14:00)*
3.  **Preparation:**
    *   *Help: "Apa yang wajib dibawa tamu?" (Contoh: Baju ganti, Handuk)*

### Form Khusus: Tour 🗺️
*Fokus: Rute & Logistik*

1.  **Itinerary Builder:**
    *   *Help: "Ceritakan perjalanan dari awal sampai akhir."*
    *   *Contoh:*
        *   08:00 - Jemput di Hotel
        *   10:00 - Tiba di Pura Lempuyang
        *   13:00 - Makan Siang
2.  **Pickup Options:**
    *   *Help: "Area mana saja yang gratis jemput?" (Contoh: Kuta, Seminyak)*

---

## 4. Selling Points (Bikin produk menarik)

Merchant pilih tag keunggulan produk (Layer 2 Signals).

> **"Kenapa produk ini spesial? (Pilih semua yang sesuai)"**
>
> *   ✅ **Instant Confirmation** (Langsung dapat voucher)
> *   ✅ **Kid Friendly** (Aman untuk anak-anak)
> *   ✅ **Halal Food** (Makanan halal tersedia)
> *   ✅ **Wheelchair Accessible** (Ramah kursi roda)
> *   ✅ **English Speaking Guide**

---

## 5. Preview & Publish

Merchant lihat tampilan akhir ("Kartu Produk") sebelum live.

> **"Begini tampilan produk Anda di aplikasi Voyago! Sudah oke?"**
>
> [ **Publish Product** ]
