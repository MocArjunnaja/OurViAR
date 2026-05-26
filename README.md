<div id="top">

<div align="center">

# OurViAR — KIDMAN ROOM VR

<em>Immersive Virtual Learning Experience Through WebVR Technology</em>

<!-- BADGES -->
<img src="https://img.shields.io/badge/A--Frame-EF2D5E.svg?style=flat&logo=aframe&logoColor=white" alt="A-Frame">
<img src="https://img.shields.io/badge/WebVR-Supported-brightgreen.svg?style=flat" alt="WebVR">
<img src="https://img.shields.io/badge/HTML5-E34F26.svg?style=flat&logo=HTML5&logoColor=white" alt="HTML5">
<img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat&logo=JavaScript&logoColor=black" alt="JavaScript">
<img src="https://img.shields.io/badge/GLTF-Model-blue.svg?style=flat" alt="GLTF">

<br><br>
<em>Built with the tools and technologies:</em>

<img src="https://img.shields.io/badge/A--Frame-1.3.0-EF2D5E.svg?style=flat&logo=aframe&logoColor=white" alt="A-Frame">
<img src="https://img.shields.io/badge/Blender-F5792A.svg?style=flat&logo=Blender&logoColor=white" alt="Blender">
<img src="https://img.shields.io/badge/HTML-E34F26.svg?style=flat&logo=HTML5&logoColor=white" alt="HTML">

</div>

<br>

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
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

**OurViAR — KIDMAN ROOM** adalah aplikasi Virtual Reality berbasis web yang dibangun menggunakan A-Frame. Project ini merupakan tugas mata kuliah AR/VR yang menghadirkan pengalaman belajar immersive di dalam lingkungan ruangan virtual 3D.

User dapat menjelajahi ruangan virtual, menonton video pembelajaran, dan menjawab pertanyaan evaluasi — semuanya langsung dari browser tanpa perlu aplikasi tambahan.

**Mengapa OurViAR?**

Project ini mengeksplorasi potensi WebVR sebagai medium pembelajaran interaktif:

- 🏠 **Lingkungan 3D Imersif:** Ruangan virtual Kidman Room yang detail, dapat dijelajahi secara bebas.
- 🎮 **Navigasi Intuitif:** Gerakan WASD + mouse look yang responsif, mendukung mode headset VR.
- 🎬 **Video Pembelajaran:** Konten video edukatif yang diputar langsung di dalam scene VR.
- 🖱️ **Interaksi Bertahap:** Tombol DUDUK, NEXT, dan TIDAK untuk mengontrol alur pembelajaran.
- ❓ **Evaluasi Akhir:** Pertanyaan kuis di akhir sesi untuk mengukur pemahaman.
- 🌐 **Zero Install:** Berjalan langsung di browser modern, tidak perlu install apapun.

---

## Features

| Fitur | Deskripsi | Status |
|-------|-----------|--------|
| Scene VR 3D | Ruangan Kidman Room dalam format `.glb` | ✅ Done |
| Navigasi WASD | Bergerak bebas di dalam ruangan | ✅ Done |
| Mouse Look | Lihat ke segala arah dengan mouse/drag | ✅ Done |
| VR Headset Mode | Tombol enter VR untuk headset (Cardboard, Quest) | ✅ Done |
| Tombol DUDUK | User berpindah ke posisi duduk di dalam ruangan | 🔧 In Progress |
| Trigger Video | Memutar video pembelajaran di dalam scene | 🔧 In Progress |
| Tombol NEXT | Lanjut ke bagian konten berikutnya | 🔧 In Progress |
| Tombol TIDAK | Skip atau kembali ke posisi awal | 🔧 In Progress |
| Pertanyaan Akhir | Tampilan kuis evaluasi setelah video selesai | 🔧 In Progress |

---

## Getting Started

### Prerequisites

Pastikan kamu memiliki salah satu dari berikut:

- Browser modern: **Chrome** (v90+), Firefox, Edge
- Python 3.x (untuk menjalankan HTTP server lokal), atau
- VS Code dengan extension **Live Server**

> **Penting:** File `.glb` tidak dapat diload via `file://` secara langsung. Wajib menggunakan HTTP server.

### Installation

1. Clone atau download repository ini:
   ```bash
   git clone https://github.com/username/OurViAR.git
   cd OurViAR
   ```

2. Pastikan file `kidman_room.glb` berada di dalam folder project (satu level dengan `Main.html`).

### Usage

**Opsi 1 — Python HTTP Server:**
```bash
# Di dalam folder OurViAR/
python -m http.server 8000
```
Kemudian buka browser dan akses: `http://localhost:8000/Main.html`

**Opsi 2 — VS Code Live Server:**
1. Install extension **Live Server** di VS Code
2. Klik kanan `Main.html` → **Open with Live Server**

**Opsi 3 — Node.js:**
```bash
npx serve .
```

---

## Controls

| Input | Aksi |
|-------|------|
| `W` / `↑` | Maju |
| `S` / `↓` | Mundur |
| `A` / `←` | Geser kiri |
| `D` / `→` | Geser kanan |
| Mouse drag | Lihat ke segala arah |
| Tombol VR (kanan bawah) | Masuk mode VR headset |
| Tombol **DUDUK** | Pindah ke posisi duduk |
| Tombol **NEXT** | Lanjut konten berikutnya |
| Tombol **TIDAK** | Skip / kembali |

---

## Project Structure

```
OurViAR/
├── Main.html              # Entry point — scene VR utama
├── README.md              # Dokumentasi project
├── PLANNER.md             # Pembagian tugas tim
├── LICENSE                # Lisensi project
├── kidman_room.glb        # Model 3D ruangan (Blender export)
├── video/
│   └── materi.mp4         # Video pembelajaran
├── sounds/
│   └── ambient.mp3        # Audio ambient (opsional)
└── docs/
    ├── SCRIPT_NARASI.md   # Script narasi video
    └── STORYBOARD.md      # Storyboard konten
```

---

## Team

Project ini dikerjakan oleh tim untuk tugas mata kuliah **Augmented & Virtual Reality**.

| Nama | Peran |
|------|-------|
| **Tegar** | Konsep Video Pembelajaran — script narasi, storyboard, pertanyaan akhir |
| **Arjun** | Setup Scene VR — struktur A-Frame, model GLB, lighting, kamera |
| **Abdillah** | Navigasi & Interaksi — WASD, tombol DUDUK/NEXT/TIDAK, trigger video |
| **Sihaam** | UI, Testing & Bug Fixing — instruksi, label tombol, kuis, QA |
| **Leandro** | Optimasi Asset — export `.glb`, optimasi texture dan ukuran file |

---

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.

---

<div align="center">
  <a href="#top">Back to top</a>
</div>
