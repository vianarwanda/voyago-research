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

## 2. Validation Check (Jawab Pertanyaan Ini)

System akan mengajukan beberapa pertanyaan kunci untuk memastikan kategori sudah tepat.

### A. Jika pilih "Tiket Masuk" 🎫
**Q1: "Apakah tamu perlu reservasi jam kedatangan spesifik?"**
> *   **Tidak** → Lanjut.
> *   **Ya** → *Warning:* "Sebaiknya pindah ke **Activity** agar fitur slot waktu aktif."

**Q2: "Apakah tiket ini sudah termasuk pemandu (guide)?"**
> *   **Tidak** → Lanjut.
> *   **Ya** → *Warning:* "Jika dipandu, produk ini lebih cocok masuk **Tour** atau **Activity**."

**Q3: "Apakah ini hanya voucher makan (Dining)?"**
> *   **Ya** → *Warning:* "Untuk saat ini, Voucher Makan masuk ke kategori **Activity** (Dining)."

---

### B. Jika pilih "Aktivitas" 🏃
**Q1: "Apakah aktivitas ini pindah-pindah lokasi (sightseeing) seharian?"**
> *   **Tidak** → Lanjut.
> *   **Ya** → *Warning:* "Ini terdengar seperti **Tour**. Pindah kategori agar ada fitur Itinerary."

**Q2: "Apakah tamu hanya menyewa alat (Rental) tanpa instruktur?"**
> *   **Ya** → Lanjut (Pilih sub-kategori: *Rental* di langkah berikutnya).
> *   **Tidak** → Lanjut.

---

### C. Jika pilih "Tur" 🗺️
**Q1: "Apakah durasi tur lebih dari 24 jam (menginap)?"**
> *   **Tidak** → Lanjut (Day Tour).
> *   **Ya** → *Note:* "Produk akan ditandai sebagai **Multi-day Tour**."

**Q2: "Apakah ini Open Trip (digabung orang lain) atau Private?"**
> *   *Note:* Merchant akan diminta set varian harga untuk *Shared* atau *Private* di langkah selanjutnya.

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
