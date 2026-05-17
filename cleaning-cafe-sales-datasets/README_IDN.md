# Data Cleaning & Reconstruction Project

# Overview

Proyek ini berfokus pada pembersihan, standarisasi, dan rekonstruksi dataset transaksi yang terdiri dari ~10,001 baris dan 8 kolom.

Dataset mentah memiliki format yang tidak konsisten, struktur kolom yang berantakan, serta nilai yang hilang di beberapa field penting. Tujuan dari proyek ini adalah mengubah dataset tersebut menjadi bersih, terstruktur, dan siap untuk analisis menggunakan pendekatan rule-based data cleaning dan teknik rekonstruksi logis.

---

## Dataset Structure

Dataset yang telah dibersihkan memiliki kolom berikut:

* transaction_id
* item
* quantity
* price_per_item
* total_spent
* payment_method
* location
* transaction_date

---

## Data Cleaning Process

```
1. Column Standardization
  Dataset awal memiliki format kolom yang berantakan dan tidak konsisten. Langkah-langkah berikut dilakukan:

	* Menyusun ulang kolom menggunakan shortcut Excel:
	
	  * `Alt + H + O + A` (AutoFit Column Width)
	  * `Alt + H + O + I` (AutoFit Row Height)
	  * Menghapus spasi yang tidak perlu
	  * Mengubah semua header kolom menjadi huruf kecil
	  * Mengganti spasi dengan underscore (`_`) untuk konsistensi
```

---

```
2. Handling Missing Values

	# Numerical Reconstruction

		Nilai yang hilang pada kolom numerik direkonstruksi menggunakan hubungan matematika:
		
		* `total_spent = price_per_item × quantity`
		
		Logika rekonstruksi:
		
		* `price_per_item` yang hilang → dihitung menggunakan `total_spent / quantity`
		* `quantity` yang hilang → dihitung menggunakan `total_spent / price_per_item`
```

---

```
	# Item-Based Imputation

		* Ditemukan bahwa item yang sama cenderung memiliki harga yang konsisten
		* Nilai `price_per_item` yang hilang diisi menggunakan harga dari item yang sama pada baris lain
```

---

# Unrecoverable Cases

Beberapa data tidak dapat direkonstruksi karena informasi yang tidak mencukupi:

```
* Baris di mana `quantity` dan `total_spent` sama-sama kosong
* Kasus di mana beberapa item memiliki harga yang sama, sehingga identifikasi balik menjadi tidak reliabel

Nilai-nilai tersebut dibiarkan kosong untuk menjaga integritas data.
```

---

# Key Insights

```
* Hubungan matematika efektif untuk memulihkan nilai numerik yang hilang
* Imputasi berbasis item bekerja dengan baik, namun bergantung pada konsistensi data
* Harga tidak dapat dijadikan identifier unik untuk item
* Kehilangan data tidak dapat dihindari dalam dataset yang tidak lengkap
```

---

# Output

```
* Dataset yang telah dibersihkan dan distandarisasi
* Nilai yang hilang telah direkonstruksi jika memungkinkan secara logis
* Nilai yang masih hilang ditandai dengan jelas
```

---

# Future Improvements

```
* Mengimplementasikan pembersihan otomatis menggunakan Python (Pandas)
* Menerapkan teknik imputasi lanjutan (misalnya statistik atau berbasis machine learning)
* Menambahkan validasi untuk mendeteksi anomali setelah rekonstruksi
```

---

#Author Notes
Proyek ini menekankan pemecahan masalah praktis dalam menghadapi data dunia nyata yang berantakan.
Seluruh proses pembersihan dan rekonstruksi dilakukan menggunakan pendekatan berbasis aturan dan validasi manual untuk memastikan konsistensi dan keandalan.

---

# Tools Used

* Microsoft Excel

---

# Closing

Proyek ini menunjukkan kemampuan dalam menangani data mentah yang tidak terstruktur dan mengubahnya menjadi dataset yang andal dan siap untuk analisis.
