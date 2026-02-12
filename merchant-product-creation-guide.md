# Merchant Product Creation Guide (The Wizard)

Dokumen ini sengaja dibuat dalam bentuk “cerita” supaya tim **FE + Design** enak bikin wireframe wizard-nya, tanpa ngebebanin merchant dengan banyak input di awal.

## Prinsip UX (biar wizard-nya kerasa ringan)

- **Tanya dulu, jangan asumsi**: mulai dari pertanyaan manusia, bukan dropdown teknis.
- **Progressive disclosure**: tampilkan input sedikit-sedikit sesuai konteks.
- **Guardrail, bukan blocker**: kalau merchant “salah pilih”, kita kasih rekomendasi + alasan, tapi tetap ada opsi.
- **Draft-friendly**: autosave, bisa keluar, lanjut lagi kapan pun.

---

## Struktur Wizard (untuk wireframe)

1. **Product Discovery** (pilih tipe produk)
2. **Quick Checks** (pertanyaan validasi, tampilkan warning kalau perlu)
3. **Info Dasar** (yang wajib supaya produk bisa tampil rapi)
4. **Detail Sesuai Tipe** (tiket / aktivitas / tur)
5. **Harga & Ketersediaan** (dibikin simpel, step-by-step)
6. **Selling Points** (tag keunggulan)
7. **Preview & Publish** (lihat “kartu produk”)

> Catatan layout: pakai **progress bar** + tombol **Back / Next**. Setiap step idealnya 1 layar (atau 2 sub-layar max).

---

## 1) Product Discovery (Tanya dulu, jangan asumsi)

**Layar goal:** merchant cepat “mengerti dirinya jualan apa”.

**Copy utama:**
**Q: "Halo! Produk apa yang ingin Anda jual hari ini?"**

**UI yang kebayang:**
- 3 kartu pilihan (card select) + icon + contoh
- optional: link kecil “Belum yakin? Bantu saya pilih”

### A. 🎫 Tiket Masuk (Entry Ticket)
- **Help:** "Untuk akses masuk ke tempat wisata tanpa pemandu."
- **Contoh:** Museum, Waterpark, Zoo, Observation Deck.
- **Key Feature:** Bebas datang jam berapa saja (seharian).

### B. 🏃 Aktivitas (Activity)
- **Help:** "Kegiatan partisipatif dengan instruktur dalam durasi pendek."
- **Contoh:** Rafting, Spa, Kursus Memasak, Photoshoot Adat.
- **Key Feature:** Ada durasi & biasanya ada instruktur/sesi.

### C. 🗺️ Tur & Perjalanan (Tour)
- **Help:** "Perjalanan wisata keliling dengan rute dan pemandu."
- **Contoh:** City Tour, Island Hopping, Hiking seharian.
- **Key Feature:** Pindah-pindah lokasi & ada itinerary.

---

## 2) Quick Checks (Jawab pertanyaan ini)

**Layar goal:** memastikan kategori “tidak salah pilih”, tanpa bikin merchant bingung.

**UI yang kebayang:**
- pertanyaan ya/tidak (segmented control)
- kalau “kena warning” munculkan panel kuning dengan:
  - 1 kalimat alasan
  - CTA: **"Pindah ke …"** dan **"Lanjutkan saja"**

### A. Jika pilih "Tiket Masuk" 🎫
**Q1: "Apakah tamu perlu reservasi jam kedatangan spesifik?"**
- **Tidak** → Lanjut.
- **Ya** → *Warning:* "Kalau ada jam kedatangan, ini lebih nyaman dibuat sebagai **Aktivitas** (biar bisa atur sesi)."

**Q2: "Apakah tiket ini sudah termasuk pemandu (guide)?"**
- **Tidak** → Lanjut.
- **Ya** → *Warning:* "Kalau ada pemandu, biasanya lebih cocok jadi **Tur** atau **Aktivitas**."

**Q3: "Apakah ini voucher makan (Dining)?"**
- **Ya** → *Warning:* "Untuk saat ini, voucher makan kita masukkan ke **Aktivitas**."

### B. Jika pilih "Aktivitas" 🏃
**Q1: "Apakah aktivitas ini pindah-pindah lokasi (sightseeing) seharian?"**
- **Tidak** → Lanjut.
- **Ya** → *Warning:* "Kalau keliling banyak spot, ini lebih cocok sebagai **Tur** (biar bisa bikin itinerary)."

**Q2: "Apakah tamu hanya menyewa alat (Rental) tanpa instruktur?"**
- **Ya** → *Note:* "Nanti di step detail, kita tampilkan pilihan: **Rental**."
- **Tidak** → Lanjut.

### C. Jika pilih "Tur" 🗺️
**Q1: "Apakah durasi tur lebih dari 24 jam (menginap)?"**
- **Tidak** → Lanjut (Day Tour).
- **Ya** → *Note:* "Ini akan ditandai sebagai **Multi-day** (biar step berikutnya menyesuaikan)."

**Q2: "Tur ini Open Trip (gabung peserta lain) atau Private?"**
- *Note:* "Ini mempengaruhi tampilan harga (Shared/Private) di step harga."

---

## 3) Info Dasar (yang wajib supaya produk kebaca)

**Layar goal:** bikin “kartu produk” langsung bisa kebayang walau detailnya belum lengkap.

**UI yang kebayang:**
- input text + textarea pendek
- upload foto dengan placeholder
- chips untuk “include/exclude” (opsional)

**Field minimal yang disarankan:**
1. **Nama produk**
   - *Placeholder:* "Contoh: Tiket Masuk Bali Safari"
2. **Lokasi (tempat produknya ada di mana?)**
   - *Copy:* "Contoh: nama tempat wisata, alamat venue, atau area umum."
3. **Apakah produk ini butuh titik temu / pickup?** *(opsional, tergantung tipe)*
   - [ ] Tidak
   - [ ] Ya → tampilkan input tambahan:
     - **Titik temu** *(contoh: Lobby Hotel, Pintu Masuk Utama, Parkiran A)*
     - **Catatan singkat** *(contoh: “harap datang 15 menit lebih awal”)*
4. **Foto produk**
   - *Guidance:* "Minimal 3 foto (boleh tambah nanti)."
5. **Ringkasan singkat (1 kalimat)**
   - *Placeholder:* "Highlight utama untuk menarik pembeli."

**Optional (kalau mau nambah kualitas tanpa bikin berat):**
- **Yang termasuk** / **yang tidak termasuk**
- **Catatan penting** (mis. “bawa baju ganti”, “datang 15 menit lebih awal”)

---

## 4) Detail Sesuai Tipe (Isi yang perlu aja)

### A. Tiket Masuk 🎫 (Fokus: validitas & cara masuk)

**Layar goal:** pembeli ngerti “tiket ini berlaku kapan” dan “cara pakainya”.

1. **Jenis berlaku**
   - [ ] **Tanggal tertentu** *(contoh: konser / event)*
   - [ ] **Bebas tanggal** *(contoh: bebas dipakai kapan saja dalam 30 hari)*
2. **Cara masuk (redeem)**
   - [ ] **Langsung masuk** *(scan QR / tunjukin e-ticket)*
   - [ ] **Tukar di loket** *(voucher ditukar tiket fisik)*

### B. Aktivitas 🏃 (Fokus: durasi, sesi, persiapan)

**Layar goal:** pembeli ngerti “berapa lama” dan “mulainya jam berapa”.

1. **Durasi**
   - *Help:* "Berapa lama aktivitas berlangsung? (contoh: 2 jam)"
2. **Jam sesi mulai**
   - *Help:* "Sesi dimulai jam berapa saja? (contoh: 09:00, 14:00)"
3. **Persiapan / yang perlu dibawa**
   - *Help:* "Apa yang wajib dibawa tamu? (contoh: baju ganti, handuk)"
4. **Jenis aktivitas (opsional, kalau Q2 Rental = Ya)**
   - [ ] **Rental (sewa alat)** / [ ] **Dengan instruktur**

### C. Tur 🗺️ (Fokus: rute & logistik)

**Layar goal:** pembeli kebayang alur tur + opsi jemput.

1. **Itinerary singkat**
   - *Help:* "Ceritakan perjalanan dari awal sampai akhir."
   - *Contoh:*
     - 08:00 - Jemput di hotel
     - 10:00 - Tiba di Pura Lempuyang
     - 13:00 - Makan siang
2. **Opsi pickup**
   - *Help:* "Area mana saja yang bisa jemput? (contoh: Kuta, Seminyak)"

---

## 5) Harga & Ketersediaan (dibikin simpel)

**Goal:** merchant bisa publish “versi pertama” tanpa kebanyakan mikir.

**UI yang kebayang:**
- pilihan “Mulai dari harga berapa?” (simple)
- list varian (chip / card)
- kalender ketersediaan sederhana (atau “pilih hari operasional”)

**Pertanyaan inti:**
1. **Mulai dari harga berapa?**
   - *Help:* "Bisa diubah dan ditambah varian nanti."
2. **Harga ini untuk siapa?** (pilih salah satu yang paling relevan)
   - [ ] Per orang
   - [ ] Per grup
3. **Kapan produk bisa dipakai?**
   - Untuk **Tiket Masuk**: pilih “tanggal tertentu” atau “bebas tanggal”, lalu set aturan simpelnya
   - Untuk **Aktivitas**: pilih hari operasional + jam sesi (lanjut dari step sebelumnya)
   - Untuk **Tur**: pilih hari operasional + info pickup (kalau ada)

> Catatan: detail lanjutan (multi harga, seasonal, dsb) bisa jadi “Advanced settings” belakangan, biar wizard versi awal tetap ringan.

---

## 6) Selling Points (Bikin produk menarik)

**Layar goal:** bikin listing terlihat “percaya diri” tanpa nulis panjang.

Merchant pilih tag keunggulan produk.

**Copy:**
> **"Kenapa produk ini spesial? (Pilih semua yang sesuai)"**

Contoh tag:
- ✅ **Instant Confirmation** (Langsung dapat voucher)
- ✅ **Kid Friendly** (Aman untuk anak-anak)
- ✅ **Halal Food** (Makanan halal tersedia)
- ✅ **Wheelchair Accessible** (Ramah kursi roda)
- ✅ **English Speaking Guide**

---

## 7) Preview & Publish

**Layar goal:** merchant yakin sebelum live.

**Yang ditampilkan di preview:**
- “Kartu produk” (foto utama, nama, harga mulai, tipe)
- ringkasan + lokasi / pickup *(jika ada)*
- highlight (selling points)

**Copy:**
> **"Begini tampilan produk Anda di aplikasi Voyago! Sudah oke?"**

CTA:
- [ **Publish Product** ]
- optional: [ **Simpan sebagai Draft** ]
