# Collection Lxscore — Panduan Kolaborasi via Git

Repo: https://github.com/Firgiii3/collection-lxscore.git

Collection ini di-share lewat Git supaya perubahan (request baru, update vars, dsb) bisa saling sinkron antar anggota tim. Setiap orang tetap kerja normal di Bruno seperti biasa — Git cuma jadi jembatan untuk saling tarik/kirim perubahan.

---

## 1. Setup Awal (dilakukan SEKALI saja per orang)

### a. Install Git
Cek dulu apakah Git sudah terpasang:
```bash
git --version
```
Kalau belum ada, download di https://git-scm.com/downloads

### b. Clone repo
Buka terminal/PowerShell, arahkan ke folder tempat kamu biasa simpan collection Bruno (misal `Documents\bruno\`), lalu:
```bash
git clone https://github.com/Firgiii3/collection-lxscore.git
```
Ini akan membuat folder baru bernama `collection-lxscore` berisi semua file collection.

### c. Buka di Bruno
1. Buka aplikasi Bruno.
2. Klik **Open Collection**.
3. Arahkan ke folder hasil clone tadi (`...\collection-lxscore`).
4. Collection akan langsung muncul lengkap dengan request, folder, dan **collection variables** (vars ikut karena tersimpan di file `bruno.json`, bukan di memory).

Setelah ini, kamu tinggal kerja seperti biasa di Bruno — tambah request, edit vars, dll.

---

## 2. Kalau Ada Perubahan dari Kamu (mau kirim update ke tim)

Setiap kali habis mengubah sesuatu di Bruno (request baru, edit vars, dsb) dan mau dibagikan ke yang lain, jalankan di terminal, dari dalam folder `collection-lxscore`:

```bash
git add .
git commit -m "deskripsi singkat perubahan, misal: tambah endpoint get-match"
git push
```

- `git add .` → menandai semua file yang berubah untuk dikirim
- `git commit -m "..."` → menyimpan perubahan itu sebagai satu titik riwayat (isi pesannya sesingkat tapi sejelas mungkin biar tim lain tahu perubahannya apa)
- `git push` → mengirim perubahan ke GitHub, supaya bisa ditarik anggota lain

---

## 3. Kalau Mau Ambil Perubahan Terbaru dari Tim

Sebelum mulai kerja (atau kalau curiga ada update dari orang lain), jalankan:

```bash
git pull
```

Ini akan menarik semua perubahan terbaru dari GitHub ke folder lokal kamu. Setelah itu, buka/refresh Bruno — perubahan (request baru, vars terbaru, dll) akan otomatis kelihatan, tanpa perlu import ulang apapun.

> **Kebiasaan baik:** selalu `git pull` dulu sebelum mulai kerja, dan `git push` setelah selesai kerja — supaya versi kamu dan tim selalu sinkron.

---

## 4. Kalau Terjadi Konflik (dua orang edit hal yang sama bersamaan)

Kalau saat `git pull` muncul pesan **CONFLICT**, artinya ada file yang diedit oleh dua orang di bagian yang sama. Langkah aman:
1. Jangan panik, jangan langsung push.
2. Screenshot pesan error/konfliknya.
3. Koordinasi dulu di tim siapa yang perubahannya dipakai.
4. Kalau belum yakin cara resolve manual, share screenshot error-nya ke yang paham Git di tim untuk dibantu.

---

## 5. Ringkasan Command Sehari-hari

| Situasi | Command |
|---|---|
| Pertama kali gabung | `git clone https://github.com/Firgiii3/collection-lxscore.git` |
| Sebelum mulai kerja | `git pull` |
| Setelah selesai edit | `git add .` → `git commit -m "pesan"` → `git push` |
| Cek status file yang berubah | `git status` |
| Lihat riwayat perubahan | `git log --oneline` |

---

## 6. Catatan Penting

- **Jangan** pakai fitur *Import Collection* dari file `.json` export untuk update — itu bisa bikin vars/struktur tidak konsisten. Selalu andalkan `git pull` untuk update.
- Kalau ada variable/token sensitif, pastikan sudah ditandai sebagai **Secret** di Bruno (tab Vars/Secrets) supaya tidak ikut ter-commit ke Git dalam bentuk plain text.
- Kalau bingung di tengah proses, jangan asal klik "Remove"/"Close All" di Bruno — itu cuma menyembunyikan dari tampilan, bukan menghapus file. Data aman selama foldernya tidak dihapus manual.
