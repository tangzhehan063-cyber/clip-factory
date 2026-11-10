# Clip Factory — Progres Setup (Dev)

Tujuan: clipping video (Whop Content Rewards) tanpa edit di device sendiri. Semua proses (download, AI, subtitle, face tracking, render 9:16) jalan di **Kaggle GPU**. Device cukup untuk browser.

- Repo: `tangzhehan063-cyber/clip-factory` (fork dari `NaufalRizqullah/opensource-clipping`)
- Studio (UI browser): https://naufalrizqullah.github.io/opensource-clipping/studio/
- Import notebook ke Kaggle (File → Import Notebook → Link):
  `https://raw.githubusercontent.com/tangzhehan063-cyber/clip-factory/main/notebooks/kaggle-studio-server.ipynb`

## Perubahan di repo ini

1. `notebooks/kaggle-studio-server.ipynb` clone dari `clip-factory` (bukan repo asli).
2. `scripts/kaggle_studio.py`: Kaggle sekarang Python 3.13, jadi setup otomatis download Python 3.12 via `uv` dan membuat venv dari situ (sudah dites, test lulus).

## Checklist

- [x] Step 1 — Fork repo
- [x] Step 2 — Akun Kaggle (verifikasi HP), Gemini API key, ngrok authtoken
- [x] Step 3 — Import notebook, Settings: GPU T4 x2 + Internet ON, Secrets `GOOGLE_API_KEY` & `NGROK_AUTHTOKEN` (checkbox dicentang)
- [ ] **Step 4 — LANJUT DARI SINI**
  1. Cell baru di atas cell setup: `!cd /kaggle/working/opensource-clipping && git pull`
  2. Jalankan cell setup (②) — harus muncul `Host Python 3.13 is unsupported; downloading a standalone Python 3.12 via uv...`, lalu tunggu 5–15 menit
  3. Cell FFmpeg → `FFmpeg ready.`
  4. Cell Secrets → `GOOGLE_API_KEY` & `NGROK_AUTHTOKEN` = configured
  5. Cell Cookies (opsional, boleh dilewati dulu)
- [ ] Step 5 — Jalankan cell server → tunggu `BACKEND SERVER READY` → copy Public URL → Studio → Connect
- [ ] Step 6 — Tes clip pertama

Catatan: kalau sesi Kaggle mati, folder `/kaggle/working` hilang → jalankan ulang dari cell clone + setup.

## Batas gratis

| Layanan | Batas | Reset |
|---|---|---|
| Kaggle GPU | ~30 jam/minggu, maks 12 jam/sesi (dihitung selama sesi menyala) | Mingguan (cek sidebar) |
| Gemini API | Per menit & per hari (cek AI Studio) | Harian, ~15.00 WIB |
| ngrok | 1 GB traffic keluar & 20.000 request/bulan | Tanggal 1 tiap bulan |

Tips hemat:
- Matikan sesi Kaggle setelah selesai.
- Jangan preview video di Studio; download hasil lewat panel Output/Files Kaggle (tidak makan kuota ngrok).
- Jangan simpan video sumber di device: download hasil → upload → hapus.
- Kalau YouTube blokir download → `youtube_cookies.txt` dari akun YouTube cadangan (JANGAN di-commit).

## Ide konten (biar beda dari clipper lain)

Pilih campaign trading/finance, tambahkan breakdown/penjelasan sendiri (hook + clip + penjelasan gold/XAUUSD), bukan clip mentah.
