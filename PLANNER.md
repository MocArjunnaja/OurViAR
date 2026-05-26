# PLANNER — Project AR/VR KIDMAN ROOM

**Nama Project:** OurViAR — KIDMAN ROOM VR  
**Tech Stack:** A-Frame (WebVR), GLTF/GLB models, HTML/JS  
**Deadline:** _(isi sesuai jadwal kuliah)_

---

## Ringkasan Pembagian Tugas

| No | Nama | Bagian Tugas | Output Utama |
|----|------|--------------|--------------|
| 1 | **Tegar** | Konsep Video Pembelajaran | Konsep video, script narasi, storyboard, pertanyaan akhir |
| 2 | **Arjun** | Setup Scene VR | Scene VR bisa dibuka dan room muncul |
| 3 | **Abdillah** | Navigasi & Interaksi User | User bisa bergerak dan berinteraksi |
| 4 | **Sihaam** | UI, Testing, dan Bug Fixing | UI rapi, bug list, dan project stabil |
| 5 | **Leandro** | Optimasi Asset & Export `.glb` | File `kidman_room.glb` final |

---

## Detail Tugas per Anggota

---

### 1. Tegar — Konsep Video Pembelajaran

**Tujuan:** Merancang kerangka konten edukatif yang akan dipresentasikan di dalam VR.

**Detail Tugas:**
- Menentukan tema video pembelajaran (topik apa yang disampaikan di Kidman Room)
- Menyusun alur cerita / struktur video (intro → isi → penutup)
- Menulis script narasi (teks yang akan dibaca/ditampilkan)
- Membuat storyboard sederhana (bisa sketsa tangan atau tabel urutan scene)
- Menentukan isi materi per bagian ruangan
- Menyusun pertanyaan akhir video (kuis/evaluasi)

**Prosedur:**
1. Diskusi dengan tim: topik apa yang mau diajarkan melalui VR ini?
2. Tulis outline konten: bagian 1, bagian 2, dst.
3. Tulis script narasi lengkap (estimasi durasi ± berapa menit?)
4. Gambar/buat storyboard — minimal urutan scene utama
5. Buat daftar 3-5 pertanyaan evaluasi di akhir video
6. Serahkan ke **Abdillah** untuk diimplementasikan sebagai trigger video/teks di scene

**Output yang Dihasilkan:**
- [ ] Dokumen `SCRIPT_NARASI.md` atau `.docx` berisi teks narasi lengkap
- [ ] File storyboard (foto sketsa / tabel di dokumen)
- [ ] Daftar pertanyaan akhir (minimal 3 pertanyaan + jawaban benar)
- [ ] Deskripsi singkat tiap titik penting di ruangan (untuk dijadikan hotspot label)

**Dependensi:** Output ini jadi bahan utama untuk tugas Abdillah (no. 3) dan Sihaam (no. 4).

---

### 2. Arjun — Setup Scene VR

**Tujuan:** Membangun fondasi scene VR agar bisa dibuka di browser dan model ruangan muncul dengan benar.

**Detail Tugas:**
- Membuat struktur utama HTML menggunakan A-Frame
- Memasukkan model `.glb` ke dalam scene
- Mengatur kamera (posisi awal user di dalam ruangan)
- Mengatur lighting (ambient + directional light)
- Mengatur background scene
- Memastikan posisi awal user masuk akal (tidak melayang, tidak di dalam dinding)

**Prosedur:**
1. Pastikan file `kidman_room.glb` sudah diterima dari **Leandro** (versi final)
2. Buat/update `Main.html` dengan struktur A-Frame dasar:
   ```html
   <a-scene background="color: #111" renderer="antialias: true">
     <a-assets>
       <a-asset-item id="room-model" src="kidman_room.glb"></a-asset-item>
     </a-assets>
     <a-entity gltf-model="#room-model" position="0 0 0" rotation="0 180 0" scale="0.8 0.8 0.8"></a-entity>
     ...
   </a-scene>
   ```
3. Pasang 3 layer lighting: ambient (fill), directional (utama), directional (fill dari belakang)
4. Set `cameraRig` di posisi yang masuk akal dalam ruangan (misal: `position="0 1.6 3"`)
5. Test buka di browser — model harus muncul tanpa error console
6. Adjust scale/posisi model sampai proporsional dengan ukuran manusia

**Output yang Dihasilkan:**
- [ ] `Main.html` yang bisa dibuka di browser dan menampilkan ruangan
- [ ] Model tidak terbalik, tidak melayang, tidak terlalu kecil/besar
- [ ] Lighting terlihat natural (tidak flat putih semua, tidak gelap total)
- [ ] Posisi awal user berada di dalam ruangan menghadap ke arah yang tepat
- [ ] Tidak ada error merah di browser console

**Catatan Teknis:**
- GLTF/GLB tidak bisa diload via `file://` — harus pakai HTTP server
- Jalankan: `python -m http.server 8000` di folder project, lalu buka `localhost:8000`
- Atau pakai VS Code extension **Live Server**

---

### 3. Abdillah — Navigasi & Interaksi User

**Tujuan:** User bisa bergerak di dalam ruangan dan mengaktifkan konten interaktif (video, tombol, dll).

**Detail Tugas:**
- Membuat WASD movement dan mouse look
- Membuat tombol **DUDUK** (user pindah ke posisi duduk / kamera turun)
- Membuat trigger video (memutar video pembelajaran saat diaktifkan)
- Membuat tombol **TIDAK** (menolak/skip sesuatu)
- Membuat tombol **NEXT** (lanjut ke bagian berikutnya)

**Prosedur:**
1. Pastikan `wasd-controls` dan `look-controls` sudah aktif di kamera (base dari Arjun)
2. Implementasi tombol **DUDUK**:
   ```javascript
   function duduk() {
     document.querySelector('#cameraRig').setAttribute('position', '0 0.8 2');
   }
   ```
3. Implementasi trigger video — saat user klik objek/tombol tertentu, video diputar:
   ```html
   <a-assets>
     <video id="edu-video" src="video/materi.mp4"></video>
   </a-assets>
   <a-video src="#edu-video" position="0 2 -3" width="4" height="2.25"></a-video>
   ```
4. Implementasi tombol **NEXT** — pindah ke section/slide berikutnya (toggle visibility atau pindah posisi)
5. Implementasi tombol **TIDAK** — dismiss/hide konten atau kembali ke posisi awal
6. Tambahkan `a-cursor` untuk deteksi klik di VR mode (tanpa mouse fisik)
7. Test semua tombol berfungsi

**Output yang Dihasilkan:**
- [ ] WASD + mouse look berfungsi smooth
- [ ] Tombol DUDUK mengubah posisi kamera ke posisi duduk
- [ ] Video bisa diputar saat trigger diaktifkan
- [ ] Tombol TIDAK berfungsi (dismiss/kembali)
- [ ] Tombol NEXT berfungsi (lanjut ke konten berikutnya)
- [ ] Cursor/reticle muncul di tengah layar untuk navigasi VR

**Dependensi:** Butuh script narasi dari **Tegar** untuk tahu urutan konten, dan scene dasar dari **Arjun**.

---

### 4. Sihaam — UI, Testing, dan Bug Fixing

**Tujuan:** Tampilan antarmuka bersih dan mudah dipahami, semua fitur sudah ditest dan bug dicatat/diperbaiki.

**Detail Tugas:**
- Membuat instruksi penggunaan di layar (UI overlay)
- Membuat label tombol yang jelas (DUDUK, TIDAK, NEXT, dll)
- Membuat tampilan pertanyaan akhir video (quiz/evaluasi)
- Melakukan testing semua fitur
- Mencatat bug dan membantu perbaikan error

**Prosedur UI:**
1. Update panel instruksi di pojok kiri atas — tambahkan info tombol custom (DUDUK, NEXT, TIDAK)
2. Buat label tombol yang visible di scene (bisa `a-text` di atas tombol 3D atau div HTML)
3. Buat tampilan pertanyaan akhir:
   - Bisa berupa `a-plane` dengan `a-text` di scene, atau
   - Div HTML overlay yang muncul setelah video selesai
4. Styling: pastikan teks mudah dibaca (kontras cukup, ukuran font cukup)

**Prosedur Testing:**
1. Test di Chrome (primary target)
2. Test di Firefox
3. Test di mobile browser (Android Chrome)
4. Cek semua tombol: DUDUK, NEXT, TIDAK, trigger video
5. Cek audio (jika ada)
6. Cek VR mode button (pojok kanan bawah)
7. Catat semua bug yang ditemukan di tabel bug list

**Template Bug List:**

| # | Deskripsi Bug | Langkah Reproduce | Status | Fix oleh |
|---|---------------|-------------------|--------|----------|
| 1 | | | Open | |
| 2 | | | Open | |

**Output yang Dihasilkan:**
- [ ] UI panel instruksi lengkap dan terbaca
- [ ] Label setiap tombol interaktif jelas
- [ ] Tampilan pertanyaan akhir tampil setelah video selesai
- [ ] Bug list terisi (minimal dari hasil testing sendiri)
- [ ] Semua bug critical sudah diperbaiki sebelum deadline
- [ ] Project stabil: tidak crash, tidak freeze saat digunakan

---

### 5. Leandro — Optimasi Asset & Export `.glb`

**Tujuan:** File `kidman_room.glb` dalam kondisi optimal — tidak terlalu besar, texture bersih, siap dipakai di web.

**Detail Tugas:**
- Merapikan asset/model ruangan di Blender (atau tools 3D lainnya)
- Mengecek dan mengoptimasi ukuran file
- Mengoptimasi texture (resize, compress jika perlu)
- Memastikan file tidak terlalu berat untuk web (target < 20MB)
- Export ke format `.glb` yang siap dipakai

**Prosedur:**
1. Buka model di **Blender**
2. Cek polygon count — jika terlalu tinggi, gunakan Decimate modifier
3. Cek texture: ukuran tiap texture max 2048x2048px, format PNG/JPG
4. Compress texture menggunakan:
   - Blender bawaan (Image Editor > Pack/Export)
   - Atau tools online: [tinypng.com](https://tinypng.com)
5. Pastikan model sudah di-apply semua transform (Ctrl+A → All Transforms)
6. Export via **File > Export > glTF 2.0 (.glb)**:
   - Format: GLB (Binary)
   - Include: Selected Objects (atau All)
   - Geometry: Apply Modifiers ✓
   - Compression: Draco (opsional, untuk ukuran lebih kecil)
7. Test file GLB di browser (via `localhost`) — pastikan model tampil benar
8. Cek ukuran file akhir
9. Serahkan ke **Arjun** untuk dipakai di scene

**Checklist Optimasi:**

| Cek | Target | Aktual |
|-----|--------|--------|
| Ukuran file `.glb` | < 20 MB | ___ MB |
| Polygon count | < 500k tris | ___ tris |
| Ukuran texture terbesar | ≤ 2048px | ___ px |
| Load time di browser | < 10 detik | ___ detik |

**Output yang Dihasilkan:**
- [ ] File `kidman_room.glb` final siap pakai
- [ ] Ukuran file < 20MB (idealnya < 10MB)
- [ ] Model tampil benar saat di-load di browser (tidak ada bagian yang hilang)
- [ ] Texture tidak buram/pecah
- [ ] File diserahkan ke Arjun sebelum ia mulai setup scene

**Dependensi:** Ini adalah langkah paling awal — **Leandro harus selesai duluan** agar Arjun bisa mulai setup scene.

---

## Urutan Pengerjaan yang Disarankan

```
Leandro ──► Arjun ──► Abdillah ──► Sihaam (testing)
               ▲                        │
            Tegar (script/konten) ──────┘
```

1. **Leandro** mulai duluan — optimasi dan export `.glb`
2. **Tegar** mulai duluan paralel — tulis script, storyboard, pertanyaan
3. **Arjun** mulai setup scene setelah `.glb` dari Leandro siap
4. **Abdillah** mulai implementasi interaksi setelah scene dasar dari Arjun jalan
5. **Sihaam** mulai testing setelah fitur utama dari Abdillah selesai, sambil juga garap UI

---

## Struktur File Project

```
OurViAR/
├── Main.html              # Entry point utama (Arjun)
├── README.md              # Dokumentasi project
├── PLANNER.md             # File ini
├── LICENSE
├── kidman_room.glb        # Model 3D final (Leandro → Arjun)
├── video/
│   └── materi.mp4         # Video pembelajaran (Tegar + Abdillah)
├── sounds/
│   └── ambient.mp3        # Audio ambient (opsional)
└── docs/
    ├── SCRIPT_NARASI.md   # Script video (Tegar)
    ├── STORYBOARD.md      # Storyboard (Tegar)
    └── BUG_LIST.md        # Catatan bug (Sihaam)
```

---

## Checklist Final Sebelum Pengumpulan

- [ ] `kidman_room.glb` terupload dan load benar di browser
- [ ] Scene VR terbuka tanpa error console (Arjun)
- [ ] WASD + mouse look berfungsi (Abdillah)
- [ ] Tombol DUDUK, NEXT, TIDAK berfungsi (Abdillah)
- [ ] Video pembelajaran bisa diputar (Abdillah)
- [ ] Pertanyaan akhir tampil setelah video (Sihaam)
- [ ] UI instruksi jelas dan terbaca (Sihaam)
- [ ] Tidak ada bug critical (Sihaam)
- [ ] Script narasi & storyboard selesai (Tegar)
- [ ] README.md diupdate dengan deskripsi lengkap
