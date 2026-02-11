# Research: Taxonomy Models — Marketplace vs Travel Platform vs Folksonomy

Dokumen ini membahas perbedaan model kategorisasi produk antara **e-commerce marketplace** (Blibli, Tokopedia), **travel platform** (Viator, Klook), dan **user-generated tags / folksonomy** (social media style), serta rekomendasi hybrid untuk Voyago.

---

## 1. Marketplace (Blibli/Tokopedia/Shopee)

### Struktur: Strict Tree Hierarchy

Marketplace e-commerce pakai **strict tree** yang biasanya **3-4 level deep**:

```
Level 0: Department
└── Level 1: Category
    └── Level 2: Subcategory
        └── Level 3: Sub-subcategory (opsional)
```

Contoh:

```
📱 Handphone & Tablet              ← Department
├── Handphone                       ← Category
│   ├── Android                     ← Subcategory
│   │   ├── Samsung                 ← Sub-sub / Brand
│   │   ├── Xiaomi
│   │   └── OPPO
│   └── iPhone
├── Tablet
└── Aksesoris HP
    ├── Case & Cover
    ├── Screen Protector
    └── Charger & Kabel
```

### Karakteristik

- **1 produk = 1 leaf category** (strict single-parent)
- Kategori ditentukan dari **atribut fisik produk** (apa barangnya)
- Ada **SKU (Stock Keeping Unit)** — setiap variant punya kode unik
- Filtering berbasis **spesifikasi produk**: RAM, storage, warna, ukuran, brand
- **Attributes/specs** sangat penting: "RAM: 8GB, Storage: 256GB, Warna: Hitam"

---

## 2. Travel Platform (Viator/Klook)

### Struktur: Mesh Tags / Flexible Categories

Travel platform pakai **multi-parent tags (mesh)** atau **tree categories dengan labels tambahan**.

Satu produk bisa masuk ke banyak kategori sekaligus:

```
🚢 Dinner Cruise di Paris
├── 🍽️ Food & Drink → Dining Experiences
├── 🚢 Tours, Sightseeing & Cruises → Cruises & Sailing
├── 🌙 Evening Entertainment
├── 🎄 Christmas (seasonal)
└── ⭐ Unique Experiences
```

### Kenapa Multi-Category?

Produk travel itu **multi-dimensional** — satu pengalaman bisa relevan di banyak konteks. Charger HP ya charger HP. Tapi Dinner Cruise itu sekaligus dining, cruise, evening activity, dan bisa seasonal.

---

## 3. Perbandingan: Marketplace vs Travel Platform

| Aspek            | Marketplace (Blibli)            | Travel Platform (Viator/Klook)           |
| ---------------- | ------------------------------- | ---------------------------------------- |
| **Yang dijual**  | Barang fisik (tangible)         | Pengalaman/jasa (intangible)             |
| **Inventory**    | Stok fisik, bisa habis permanen | Availability per tanggal & slot waktu    |
| **Delivery**     | Dikirim ke alamat               | Datang ke lokasi / e-voucher             |
| **Variant**      | Warna, Ukuran, Model            | Tanggal, Waktu, Tipe tiket, Jumlah orang |
| **Kategorisasi** | 1 produk = 1 category (tree)    | 1 produk = banyak tags (mesh)            |
| **Pricing**      | Harga tetap + diskon            | Dynamic per tanggal & pax type           |
| **Fulfillment**  | Warehouse → Kurir → Customer    | Booking → Confirmation → Voucher         |
| **Return**       | Retur barang fisik              | Free cancellation / no refund policy     |
| **Filter**       | Brand, Specs, Price, Rating     | Category, Duration, Price, Features      |

### Contoh Atribut Produk

**Marketplace:**
```
Samsung Galaxy S25
├── Category: Handphone > Android > Samsung (single path)
├── SKU: BLI-SAM-S25-256-BLK
├── Attributes: RAM 12GB, Storage 256GB, Warna Hitam
├── Price: Rp 14.999.000 (fixed)
├── Stock: 47 units
└── Variants: [Black, Green, Silver] × [128GB, 256GB]
```

**Travel Platform:**
```
Bali Sunrise Trekking Mt. Batur
├── Tags: [Hiking, Outdoor, Sunrise, Adventure, Private Available]
├── Attributes: Duration 8h, Max 15 pax, Moderate difficulty
├── Price: Dynamic → Adult Rp 450k, Child Rp 300k
├── Availability: Per tanggal & slot (bisa sold out per hari)
└── Options: [Shared, Private] × [With/Without Lunch]
```

---

## 4. Model Tagging: Taxonomy vs Folksonomy vs Hybrid

### 3 Model

| Model          | Siapa yang buat tag? | Contoh                                             |
| -------------- | -------------------- | -------------------------------------------------- |
| **Taxonomy**   | Platform/admin       | Viator tags, Klook categories, Blibli categories   |
| **Folksonomy** | User/customer        | Instagram hashtags, Stack Overflow tags, Pinterest |
| **Hybrid**     | Kombinasi keduanya   | YouTube, Airbnb, TripAdvisor                       |

### Folksonomy (User-Generated Tags) — Kelebihan ✅

1. **Organik & natural language** — user mendeskripsikan dengan bahasa mereka: `#instagrammable`, `#budgettrip`, `#honeymoonideas`. Tag seperti ini nggak akan muncul dari taxonomy resmi.
2. **Self-evolving** — trend baru otomatis muncul tanpa admin. Saat "glamping" populer, user langsung tag `#glamping`.
3. **Discovery & virality** — klik `#hiddengemjogja` → ketemu produk yang nggak ditemukan lewat filter biasa.
4. **Community-driven curation** — produk yang sering di-tag `#worthit` jadi social proof natural.
5. **Long-tail keyword** — tag sangat spesifik yang platform nggak bisa prediksi: `#datenight`, `#anakbalita`, `#rainyseason`.

### Folksonomy — Kekurangan ❌

1. **Noisy & inconsistent** — `#bali`, `#Bali`, `#BALI`, `#balitrip`, `#bali_trip` semua harusnya 1 entitas tapi jadi banyak tag. Normalization nightmare.
2. **Spam & abuse** — seller nakal tag `#murah #promo #diskon #viral #trending #fyp` padahal produk biasa.
3. **No hierarchy** — flat structure, nggak bisa bikin navigasi terstruktur (breadcrumb, drill-down).
4. **Ambiguity** — `#spring` = musim semi? mata air? Spring break?
5. **Cold start** — produk baru = 0 tags, nggak bisa ditemukan sampai ada user yang tag.
6. **Tidak reliable untuk business logic** — nggak bisa dipakai untuk filtering, pricing rules, atau compliance karena terlalu chaotic.

### Perbandingan Head-to-Head

| Aspek               | Taxonomy                          | Folksonomy                   |
| ------------------- | --------------------------------- | ---------------------------- |
| **Consistency**     | ✅ Guaranteed                      | ❌ Chaotic                    |
| **Discoverability** | ⚠️ Terbatas pada kategori official | ✅ Long-tail, organik         |
| **Hierarchy**       | ✅ Parent-child, navigable         | ❌ Flat                       |
| **Maintenance**     | ❌ Perlu tim kurator               | ✅ Self-maintaining           |
| **Business logic**  | ✅ Bisa untuk filtering, pricing   | ❌ Terlalu noisy              |
| **Multi-language**  | ✅ Controlled per locale           | ❌ Campur-campur              |
| **New trends**      | ❌ Lambat, perlu manual update     | ✅ Instan                     |
| **Spam risk**       | ✅ Minimal                         | ❌ Tinggi                     |
| **UX navigation**   | ✅ Breadcrumb, drill-down          | ❌ Hanya search-based         |
| **Personalization** | ⚠️ Terbatas                        | ✅ Bisa lihat preference user |

---

## 5. Rekomendasi: Hybrid Layered Model untuk Voyago

Model paling ideal untuk platform travel adalah **hybrid 4-layer**:

```
┌──────────────────────────────────────────────────────┐
│  Layer 1: SYSTEM TAXONOMY (admin-defined)            │
│  ├── Category: Tours & Experiences                   │
│  ├── Subcategory: Day Trips                          │
│  └── Attributes: Duration, Group Size, Language      │
│  → Dipakai untuk: navigasi, filter, business logic   │
├──────────────────────────────────────────────────────┤
│  Layer 2: CURATED TAGS (admin + supplier)            │
│  ├── kid-friendly, skip-the-line, halal              │
│  ├── seasonal: christmas, ramadan, cny               │
│  └── quality: top-rated, best-value                  │
│  → Dipakai untuk: enriched filtering, campaigns      │
├──────────────────────────────────────────────────────┤
│  Layer 3: USER TAGS (customer-generated)             │
│  ├── #honeymoon #instagrammable #worthit             │
│  └── #budgetfriendly #hiddengemjogja                 │
│  → Dipakai untuk: discovery, social proof             │
├──────────────────────────────────────────────────────┤
│  Layer 4: AI-INFERRED TAGS (from reviews/photos)     │
│  ├── sentiment: positive, mixed                      │
│  └── auto-detected: scenic, crowded, accessible      │
│  → Dipakai untuk: recommendation engine               │
└──────────────────────────────────────────────────────┘
```

### Contoh Real-World Hybrid

- **Airbnb** — system categories (Beachfront, Countryside, Mansions) + extracted review tags ("Great for families", "Sparkling clean")
- **TripAdvisor** — official categories + user-generated "traveler type" tags (Couples, Families, Solo)
- **YouTube** — system category (Music, Gaming) + creator tags + AI-detected topics

### Mapping ke Sumber Data Voyago

| Layer                    | Viator Source                     | Klook Source                         |
| ------------------------ | --------------------------------- | ------------------------------------ |
| Layer 1: System Taxonomy | Main parent tags (no parentTagId) | Top-level categories                 |
| Layer 2: Curated Tags    | Filtering & categorization tags   | Marketing labels + filter attributes |
| Layer 3: User Tags       | ❌ Tidak ada                       | ❌ Tidak ada                          |
| Layer 4: AI Tags         | ❌ Tidak ada                       | ❌ Tidak ada                          |

> Layer 3 & 4 adalah **peluang diferensiasi** Voyago — kedua platform utama (Viator & Klook) belum menyediakan user-generated tagging di level API.

---

## 6. Voyago Taxonomy: Categories + Signals (Adopted)

Berdasarkan analisis di atas, Voyago mengadopsi **Hybrid 2-Layer** sebagai starting point yang pragmatis.

### Kenapa 2-Layer, Bukan Full 4-Layer?

| Layer               | Status           | Alasan                                                |
| ------------------- | ---------------- | ----------------------------------------------------- |
| Layer 1: Categories | ✅ Adopt sekarang | Wajib ada dari awal untuk navigasi & filter           |
| Layer 2: Signals    | ✅ Adopt sekarang | Enrichment fleksibel, bisa di-map dari Viator + Klook |
| Layer 3: User Tags  | 🔜 Nanti          | Butuh volume user yang besar dulu biar berguna        |
| Layer 4: AI Tags    | 🔜 Nanti          | Butuh data review yang cukup untuk di-extract         |

### Naming Convention

Voyago menggunakan istilah branded untuk membedakan dari platform lain:

| Istilah Voyago | Padanan Umum          | Fungsi                                               |
| -------------- | --------------------- | ---------------------------------------------------- |
| **Category**   | Category / Tag (tree) | Navigasi utama, strict tree hierarchy                |
| **Signal**     | Tag / Label (flat)    | Enrichment fleksibel, multi-attach ke produk manapun |

> **Kenapa "Signal"?**
> - Terdengar modern & tech-forward
> - Travel metaphor: "memberi sinyal ke traveler tentang apa yang worth it"
> - Bisa diperluas natural: "Quality Signals", "Vibe Signals", "Campaign Signals"
> - Tidak bentrok dengan istilah "tag" dari Viator atau "category" dari Klook

### Layer 1: Categories (Strict Tree)

Menjawab pertanyaan: **"Apa produk ini?"**

Dipakai untuk navigasi utama, breadcrumb, dan filter sidebar. Setiap produk punya **tepat 1 leaf category**.

```
VOYAGO CATEGORIES
│
├── 🎢 Attraction
│   ├── Theme Park
│   ├── Water Park
│   ├── Museum
│   ├── Zoo & Aquarium
│   ├── Observation Deck
│   ├── Historical Site
│   ├── Park & Garden
│   └── Attraction Pass
│
├── 🎭 Experience
│   ├── Cooking Class
│   ├── Workshop & Craft
│   ├── Water Activity
│   ├── Outdoor & Sports
│   ├── Wellness & Spa
│   └── Cultural Activity
│
└── 🗺️ Tour
    ├── Day Trip
    ├── City Tour
    ├── Food Tour
    ├── Boat & Cruise
    └── Multi-day Tour
```

### Layer 2: Signals (Flexible, Multi-Attach)

Menjawab pertanyaan: **"Kenapa produk ini spesial?"**

Satu produk bisa punya banyak signals. Signals tidak terikat pada 1 category — bisa lintas kategori.

```
VOYAGO SIGNALS
│
├── 🎯 Feature Signals
│   ├── kid-friendly
│   ├── halal-friendly
│   ├── skip-the-line
│   ├── private-available
│   ├── free-cancellation
│   ├── instant-confirmation
│   ├── hotel-pickup
│   └── english-guided
│
├── 🎭 Vibe Signals
│   ├── romantic
│   ├── adventurous
│   ├── chill
│   ├── instagrammable
│   └── hidden-gem
│
├── 🏷️ Campaign Signals
│   ├── christmas
│   ├── ramadhan
│   ├── summer-sale
│   ├── new-year
│   └── chinese-new-year
│
└── ⭐ Quality Signals
    ├── top-rated
    ├── best-value
    ├── trending
    └── voyago-pick
```

### Contoh Penerapan

```
Bali Sunrise Trekking at Mt. Batur
─────────────────────────────────────
Category:  Tour > Day Trip
Signals:   ⭐ top-rated  🎭 adventurous  🎯 hotel-pickup  🎯 english-guided
```

```
Skip-the-Line Louvre Museum Ticket
─────────────────────────────────────
Category:  Attraction > Museum
Signals:   🎯 skip-the-line  ⭐ best-value  🏷️ christmas
```

```
Bangkok Pad Thai Cooking Class
─────────────────────────────────────
Category:  Experience > Cooking Class
Signals:   🎯 halal-friendly  🎭 instagrammable  ⭐ voyago-pick  🎯 free-cancellation
```

### Mapping dari Sumber Data

| Voyago               | Viator Source                                                  | Klook Source                                                |
| -------------------- | -------------------------------------------------------------- | ----------------------------------------------------------- |
| **Category**         | Main parent + child tags → di-map ke Voyago tree               | Top-level categories → di-map ke Voyago tree                |
| **Feature Signals**  | Filtering tags (skip-the-line, kid-friendly)                   | Filter attributes (instant-confirmation, free-cancellation) |
| **Vibe Signals**     | Sebagian dari tags (Unique Experiences, Once in a Lifetime)    | ❌ Perlu enrichment manual                                   |
| **Campaign Signals** | Seasonal tags (Christmas, Halloween, dsb)                      | ❌ Perlu enrichment manual                                   |
| **Quality Signals**  | Merchandising tags di back-end (Top Product, Low Cancellation) | Marketing labels (Klook's Choice, Best Price)               |

### Growth Path: 2-Layer → 4-Layer

```
Phase 1 (MVP)     → Categories + Signals           ← fase 1
Phase 2 (Growth)  → + User Tags (setelah ada community)
Phase 3 (Scale)   → + AI-Inferred Tags (setelah ada data review)
```
