# Eksekusi-Program-Numerik-Python-Menggunakan-MPI
## Topologi
![Topologi)](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/e6393cd6-9525-452e-a15a-94c587a56c1e)

## Langkah Awal
Pastikan pada komputer sudah menginstall MPI, berikut adalah link cara menginstall MPI <br> ![MPI](https://github.com/feliana444/Eksekusi-Program-Buble-Sort-Python-Menggunakan-MPI)

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
```sh
from mpi4py import MPI
import time

start = time.time()

def main():
    comm = MPI.COMM_WORLD
    rank = comm.Get_rank()
    size = comm.Get_size()

    if rank == 0:
        # Ambil input dari pengguna
        input_str = input("Masukkan data, dipisahkan dengan spasi: ")
        data = list(map(int, input_str.split()))
    else:
        data = None

    # Broadcast data dari proses 0 ke semua proses
    data = comm.bcast(data, root=0)

    chunk_size = len(data) // size
    start = rank * chunk_size
    end = (rank + 1) * chunk_size

    if rank == size - 1:
        end = len(data)

    local_sum = sum(data[start:end])

    total_sum = comm.reduce(local_sum, op=MPI.SUM, root=0)

    if rank == 0:
        print("Total hasil perhitungan:", total_sum)

if __name__ == '__main__':
    main()
end = time.time()
print("waktu dikerjakan", end - start)
```

## 3. Perbedaan Time Eksekusi pada Multinode dan SingleNode
### 3.1 Multinode
    mpirun -n 4 -host danserver,slave,slave2,slave3 python3 numerik.py 
![MN](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/2c90cdb5-8a79-456c-8f45-ec8a8a3c979c)
### 3.2 SingleNode
    python3 numerik.py 
![SN](https://github.com/feliana444/Eksekusi-Program-Numerik-Python-Menggunakan-MPI/assets/145323449/21273505-8c79-40ad-bf94-f701ff97f117)

    
