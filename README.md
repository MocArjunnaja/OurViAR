<div id="top">

<div align="center">

# OurViAR — X-Ray Education VR

<em>Reducing Patient Anxiety Through Immersive Pre-Procedure Virtual Reality Education</em>

<!-- BADGES -->
<img src="https://img.shields.io/badge/A--Frame-1.3.0-EF2D5E.svg?style=flat&logo=aframe&logoColor=white" alt="A-Frame">
<img src="https://img.shields.io/badge/WebVR-Supported-4CAF50.svg?style=flat" alt="WebVR">
<img src="https://img.shields.io/badge/HTML5-E34F26.svg?style=flat&logo=HTML5&logoColor=white" alt="HTML5">
<img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat&logo=JavaScript&logoColor=black" alt="JavaScript">
<img src="https://img.shields.io/badge/Adaptive%20Learning-Enabled-blue.svg?style=flat" alt="Adaptive Learning">

<br><br>
<em>Built with the tools and technologies:</em>

<img src="https://img.shields.io/badge/A--Frame-EF2D5E.svg?style=flat&logo=aframe&logoColor=white" alt="A-Frame">
<img src="https://img.shields.io/badge/Blender-F5792A.svg?style=flat&logo=Blender&logoColor=white" alt="Blender">
<img src="https://img.shields.io/badge/HTML-E34F26.svg?style=flat&logo=HTML5&logoColor=white" alt="HTML">
<img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat&logo=JavaScript&logoColor=black" alt="JavaScript">

</div>

<br>

---

## Table of Contents

- [Overview](#overview)
- [The Problem](#the-problem)
- [Features](#features)
- [Learning Flow](#learning-flow)
- [Adaptive System](#adaptive-system)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Usage](#usage)
- [Controls](#controls)
- [Project Structure](#project-structure)
- [Team](#team)
- [License](#license)

---

## Overview

**OurViAR** adalah simulasi Virtual Reality berbasis web yang dirancang untuk mempersiapkan pasien sebelum menjalani pemeriksaan X-Ray. Pasien yang sedang menunggu di ruang tunggu rumah sakit dapat memakai headset VR dan masuk ke simulasi virtual ruang radiologi — memahami prosedur, mendengar simulasi suara alat, dan berinteraksi secara bertahap sebelum masuk ke ruang pemeriksaan nyata.

Dibangun menggunakan **A-Frame (WebVR)** sehingga bisa berjalan langsung di browser tanpa instalasi aplikasi tambahan.

---

## The Problem

Banyak pasien — terutama anak-anak, lansia, dan pasien dengan kecemasan medis — datang ke ruang X-Ray tanpa pemahaman tentang prosedur yang akan dijalani. Hal ini menyebabkan:

- Kecemasan berlebih sebelum dan selama pemeriksaan
- Gerakan tidak terkontrol yang merusak hasil foto X-Ray
- Pertanyaan berulang kepada petugas yang menyita waktu
- Pengalaman buruk yang mempengaruhi kepatuhan medis ke depannya

**OurViAR hadir sebagai solusi edukasi pre-prosedur yang imersif dan adaptif.**

---

## Features

| Fitur | Deskripsi | Status |
|-------|-----------|--------|
| 🏥 Lingkungan Rumah Sakit Virtual | Ruang radiologi 3D yang bisa dijelajahi | ✅ Done |
| 🚶 Navigasi Bebas | WASD + mouse look, mode VR headset | ✅ Done |
| 🪑 Interaksi Duduk | Klik kursi — avatar berpindah ke posisi duduk | 🔧 In Progress |
| 🎬 Video Edukasi | Video tentang prosedur X-Ray diputar di dalam scene | 🔧 In Progress |
| 🧠 Adaptive Learning | Sistem If-Else: video diulang jika pasien belum paham | 🔧 In Progress |
| 🔊 Immersive Audio | Simulasi suara mesin X-Ray dan suasana ruangan | 🔧 In Progress |
| ❓ Evaluasi Pemahaman | Pertanyaan "Apakah Anda memahami?" setelah tiap bagian | 🔧 In Progress |
| ✅ Konfirmasi Kesiapan | "Apakah Anda siap?" sebelum simulasi berakhir | 🔧 In Progress |

---

## Learning Flow

Berikut alur pengalaman pasien di dalam VR:

```
[Pasien memakai headset]
        │
        ▼
[Masuk lingkungan VR — Ruang Radiologi]
        │
        ▼
[Instruksi: "Silakan menuju kursi pemeriksaan"]
        │
        ▼
[Pasien klik kursi → Avatar duduk]
        │
        ▼
[Tombol "Play Video" muncul]
        │
        ▼
[Video edukasi X-Ray diputar]
  • Apa itu X-Ray
  • Apakah sakit?
  • Proses pemeriksaan
  • Posisi tubuh yang benar
  • Suara alat yang akan didengar
        │
        ▼
[Pertanyaan muncul: "Apakah Anda memahami?"]
       / \
      /   \
    YA   BELUM
     │     │
     │     ▼
     │  [Video diulang / penjelasan alternatif]
     │     │
     └──►  ▼
[Simulasi suara mesin X-Ray]
"Nanti Anda akan mendengar suara seperti ini..."
        │
        ▼
[Pertanyaan: "Apakah Anda siap?"]
        │
        ▼
[Sesi VR selesai — Pasien siap masuk ruangan nyata]
```

---

## Adaptive System

Sistem ini menggunakan **branching logic** sederhana berbasis respons pasien:

```javascript
// Pseudocode alur adaptif
if (pasienMemahami === "YA") {
  lanjutKeBagianBerikutnya();
} else {
  // Belum paham
  ulangVideoAtauTampilkanPenjelasanAlternatif();
}
```

Setiap segmen video memiliki checkpoint pemahaman. Jika pasien memilih **"Belum"**, sistem akan:
1. Mengulang video segmen tersebut, atau
2. Menampilkan animasi/penjelasan yang lebih sederhana, atau
3. Menampilkan teks ringkasan poin penting

Pasien baru bisa lanjut ke bagian berikutnya setelah memilih **"Ya"** atau setelah maksimal 2 kali pengulangan.

---

## Getting Started

### Prerequisites

- Browser modern: **Chrome** (v90+), Firefox, atau Edge
- Python 3.x, Node.js, atau VS Code + Live Server extension

> **Penting:** File `.glb` tidak dapat diload via `file://`. Wajib pakai HTTP server lokal.

### Installation

```bash
git clone https://github.com/username/OurViAR.git
cd OurViAR
```

Pastikan file `kidman_room.glb` dan file video berada di folder yang sesuai.

### Usage

**Python:**
```bash
python -m http.server 8000
# Buka: http://localhost:8000/Main.html
```

**Node.js:**
```bash
npx serve .
```

**VS Code:** Klik kanan `Main.html` → Open with Live Server

---

## Controls

| Input | Aksi |
|-------|------|
| `W A S D` / Arrow Keys | Bergerak di ruangan |
| Mouse drag | Lihat ke segala arah |
| Klik objek | Berinteraksi (duduk, play video, pilih jawaban) |
| Tombol VR (pojok kanan bawah) | Masuk mode headset VR |
| **DUDUK** | Pindah ke posisi duduk |
| **PLAY VIDEO** | Mulai video edukasi |
| **YA / BELUM** | Jawab pertanyaan pemahaman |
| **NEXT** | Lanjut ke bagian berikutnya |
| **SIAP** | Konfirmasi kesiapan, akhiri sesi VR |

---

## Project Structure

```
OurViAR/
├── Main.html              # Entry point — scene VR utama
├── README.md              # Dokumentasi project
├── PLANNER.md             # Pembagian tugas tim
├── LICENSE
├── kidman_room.glb        # Model 3D ruang radiologi
├── video/
│   ├── xray_intro.mp4     # Video: apa itu X-Ray
│   ├── xray_process.mp4   # Video: proses pemeriksaan
│   └── xray_position.mp4  # Video: posisi tubuh
├── sounds/
│   ├── xray_machine.mp3   # Suara mesin X-Ray
│   └── ambient_hospital.mp3  # Suasana ruang tunggu
└── docs/
    ├── SCRIPT_NARASI.md   # Script lengkap narasi
    └── STORYBOARD.md      # Storyboard alur VR
```

---

## Team

Project ini dikerjakan untuk tugas mata kuliah **Augmented & Virtual Reality**.

| Nama | Peran |
|------|-------|
| **Tegar** | Konsep & Script — narasi, storyboard, pertanyaan evaluasi |
| **Arjun** | Setup Scene VR — struktur A-Frame, model GLB, lighting, kamera |
| **Abdillah** | Navigasi & Interaksi — WASD, tombol DUDUK/NEXT, adaptive logic |
| **Sihaam** | UI, Testing & Bug Fixing — instruksi, label, kuis, QA |
| **Leandro** | Optimasi Asset — export `.glb`, optimasi texture dan ukuran file |

---

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.

---

<div align="center">
  <sub>Project AR/VR — Simulasi Edukasi Pasien X-Ray</sub>
  <br>
  <a href="#top">Back to top</a>
</div>
