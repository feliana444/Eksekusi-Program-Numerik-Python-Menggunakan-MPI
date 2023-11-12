# Eksekusi-Program-Numerik-Python-Menggunakan-MPI
## Topologi
![Topologi)](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/e6393cd6-9525-452e-a15a-94c587a56c1e)

## Langkah Awal
Pastikan pada komputer sudah menginstall MPI, berikut adalah link cara menginstall MPI <br> ![MPI](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI/tree/main)

## 1. New User
### 1.1 Buat User <br>
    sudo adduser <nama user>
### 1.2 Beri Akses Root
    sudo usermod -aG <nama user>
### 1.3 Login ke user yang sudah dibuat <br>
    su - <nama user>
  
## 2. Buat file
### 2.1 Buat File pada user menggunakan perintah <br> 
    touch <nama file.py>
### 2.2 Edit File <br>
    sudo nano <nama file>
### 2.3 Masukkan Program Numerik.py ke dalam file yang sudah dibuat <br>
    Berikut ini adalah program yang kami gunakan
![NP](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/055a6de1-16fd-42b0-a662-2e74293717af)


## 3. Perbedaan Time Eksekusi pada Multinode dan SingleNode
### 3.1 Multinode
    mpirun -n 4 -host danserver,slave,slave2,slave3 python3 numerik.py <br>
![MN](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/2c90cdb5-8a79-456c-8f45-ec8a8a3c979c)
### 3.2 SingleNode
    python3 numerik.py <br>  
![SN](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/21273505-8c79-40ad-bf94-f701ff97f117)

    
