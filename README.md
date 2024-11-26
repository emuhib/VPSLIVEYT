
# Setup Server dan Live Streaming YouTube dengan FFmpeg dan gdown

Proyek ini menjelaskan langkah-langkah untuk mengatur server Ubuntu agar dapat digunakan untuk live streaming di YouTube menggunakan **FFmpeg**. Selain itu, akan dijelaskan cara mengelola sesi dengan **tmux** dan mendownload video dari Google Drive menggunakan **gdown**.

## Persyaratan
- **Server Ubuntu** dengan akses root
- **VPS atau server cloud** (misalnya DigitalOcean, AWS, atau lainnya)
- **Stream Key YouTube**

---

## Langkah-Langkah Instalasi

1. **Update dan upgrade sistem:**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install tmux:**
   ```bash
   sudo apt install tmux -y
   ```

3. **Install FFmpeg:**
   ```bash
   sudo apt install ffmpeg -y
   ```

4. **Install Python3 dan pip:**
   ```bash
   sudo apt install python3 python3-pip -y
   ```

5. **Install gdown untuk download file dari Google Drive:**
   ```bash
   pip install gdown
   ```

---

## Menggunakan gdown untuk Mengunduh Video

Unduh video dari Google Drive dengan perintah berikut:
```bash
gdown https://drive.google.com/uc?id=your_file_id
```

Ganti `your_file_id` dengan **ID file Google Drive** Anda.

---

## Mengelola Sesi tmux

**1. Mulai sesi baru:**
```bash
tmux new -s Mainan
```

**2. Monitoring sesi tmux yang sudah ada:**
```bash
tmux attach -t Hujan
```

**3. Menghentikan sesi tmux:**
```bash
tmux kill-session -t Hujan
```

---

## Live Streaming ke YouTube Menggunakan FFmpeg

Untuk memulai live streaming di YouTube, gunakan perintah berikut:
```bash
ffmpeg -stream_loop -1 -re -i /root/live.mp4 -f flv -c:v copy -c:a copy rtmp://a.rtmp.youtube.com/live2/your_StreamKey
```

### Penjelasan:
- **`/root/live.mp4`**: Path file video Anda (pastikan file ini sudah ada di server).
- **`your_StreamKey`**: Ganti dengan Stream Key dari YouTube Live.

---

## Catatan
- Gunakan **tmux** untuk menjalankan FFmpeg sehingga live streaming tetap berjalan meskipun Anda keluar dari sesi SSH.
- Jangan lupa memastikan bahwa video Anda telah diunggah atau tersedia di server.

---
