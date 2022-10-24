# Mitigations

Created: June 22, 2022 1:17 PM

Kita sudah mengetahui kerentanan kerentanan WebSocket. Ada beberapa panduan pencegahan untuk membantu melindungi WebSockets.

# WSS

Hindari penggunaan ws://, ini bukan transportasi yang aman. Sebagai gantinya, gunakan wss://, yang merupakan protokol yang jauh lebih aman karena transaksi diatas TLS. WSS aman, sehingga mencegah hal-hal seperti serangan man-in-the-middle. Transportasi yang aman mencegah banyak serangan dari awal.

# Validasi Input Client

Koneksi WebSocket dapat dengan mudah dibuat di luar browser. Anda akan berurusan dengan data sewenang-wenang apa pun yang terjadi. Data ini memerlukan validasi serta data lainnya yang berasal dari klien sebelum diproses. Mengapa? Karena serangan injeksi seperti OS, SQL, Blind SQL dimungkinkan melalui WebSockets.

# Validasi Data Server

Data yang dikembalikan server juga dapat membawa masalah. Pesan yang diterima di sisi klien harus selalu diproses sebagai data. Menetapkan pesan ini langsung ke DOM atau mengevaluasi sebagai kode tidak disarankan. Dalam hal respons JSON, gunakan JSON.parse() dalam kombinasi dengan penanganan pengecualian dan jika diperlukan metode sanitasi khusus untuk mengurai data dengan aman.