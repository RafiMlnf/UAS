# Project UAS - Semester 1

```Python
Nama    : Rafi Maulana Firdaus
NIM     : 312210382
Kelas   : TI 22 A4
Matkul  : Bahasa Pemrograman
```

--------------------------------------------------------------------------------------------------------------------------------------

## Penjelasan
> Konsep projek ini membuat sebuah daftar mahasiwa dan daftar nilainya, yang nantinya dapat menambahkan  data mahasiswa, menambahkan nim, melihat, mencari, dan menghapus data mahasiswa yang telah di input. Dengan menggunakan bahasa pemrograman Python yang dimana tugas-tugas tersebut dapat dibungkus menjadi sebuah Package (Folder) yang didalamnya terdapat Modul (File). Konsep Package dan Modul memudahkan untuk mengorganisir sebuah program.

## Tampilan Menu Utama
> Mengisi `main.py` dengan program berupa menu utama yang berisi   
> `menu = input("[(T)ambah, (I)nput Nilai, (L)ihat, (C)ari, (H)apus, (U)bah, (K)eluar] : ")`

``` Python
from view import input_nilai, view_nilai
from model import daftar_nilai
data = daftar_nilai.Data_mahasiswa()
print("="*20)
print("|PROGRAM INPUT DATA|")
print("="*20)
while True: 
    print()
    menu = input("[(T)ambah, (I)nputNilai, (L)ihat, (C)ari, (H)apus, (U)bah, (K)eluar] : ")
    print("~"*78)
    print()
    if menu.lower() == 't':
        data.tambah()
    elif menu.lower() == "i":
        input_nilai.nilai()
    elif menu.lower() == 'l':
        if data.nama:
            view_nilai.lihat()
        else:
            print("BELUM ADA DATA!, pilih [T/t] untuk menambah data")  
    elif menu.lower() == 'c':
        if data.nama:
            data.cari()
        else:
            print("BELUM ADA DATA!, pilih [T/t] untuk menambah data") 
            
    elif menu.lower() == "h":
        data.hapus(data.nama)
    elif menu.lower() == "u":
        data.ubah(data.nama) 
    elif menu.lower() == "k":
        print("Program selesai, Terima Kasih :) ")
        break
    else:
        print("\n INPUT {} TIDAK ADA!, Silakan pilih [T/L/I/H/U/K] untuk menjalankan program!".format(menu))
```
## Penjelasan 
> Di program utama ini terdapat modul yg di import ke file `from view import input_nilai, view_nilai` &
`from model import daftar_nilai`. Modul memungkinkan Anda menulis kode yang terdiri dari beberapa file dan membaginya menjadi bagian-bagian yang lebih kecil, yang dapat diimport sesuai kebutuhan.

#### Contoh tampilan menu :
![01](https://user-images.githubusercontent.com/115614668/211688008-ab60b7ec-e3f2-40fc-bc23-b8cd6892a5fe.png)

------------------------------------------------------------------------------------------------------------------------------------------

## Daftar Nilai
> Di dalam file `daftar_nilai.py` ini terdapat sourcecode `input("[(T)ambah, (C)ari, (H)apus, (U)bah] ")`


``` Python
class Data_mahasiswa:
    nama = []
    nim = []
    uts = []
    uas = []
    tugas = []
    # Tambah data
    def tambah(self):
        print("Tambah data\n")
        nama    = input("Nama           : ")
        self.nama.append(nama)
        nim     = int(input("NIM            : "))
        self.nim.append(nim)
        uts     = 0
        self.uts.append(uts)
        uas     = 0
        self.uas.append(uas)
        tugas   = 0
        self.tugas.append(tugas)
        print("\nData {0} berhasil di tambahkan".format(nama))
                
    # Menghapus inputan nama
    def hapus(self, nama):
        print("Hapus data inputan")
        print("="*15)
        nama = (input("\nMasukan Nama berdasarkan inputan : "))
        if nama in self.nama:
            print("Data {0} berhasil di hapus".format(nama))
            index = self.nama.index(nama)
            del self.nama[index]
            del self.nim[index]
            del self.uts[index]
            del self.uas[index]
            del self.tugas[index]
        else:
            print("NAMA {0} TIDAK ADA!".format(nama))
    
        # Mengubah data NIM
    def ubah(self, nama):
        print("Ubah data NIM")
        print("="*15)
        input_nama = input("Masukan Nama : ")
        if input_nama in nama:
            index = nama.index(input_nama)
            self.nim[index]     = int(input("NIM            : "))
            print("\nNIM Data {0} berhasil di ubah".format(input_nama))
        else:
            print("NAMA {0} TIDAK ADA! / ANDA BELUM MENAMBAHKAN DATA".format(input_nama))
            
        # Mencari data yg sudah di input 
    def cari(self):
        print("Mencari data")
        print("="*15)
        nama = (input("\nMasukan Nama yg ingin di cari : "))
        if nama in self.nama:
            index = self.nama.index(nama)
            print(f"Nama Mahasiswa: {self.nama[index]}")
            print(f"NIM Mahasiswa : {self.nim[index]}")
            print(f"Nilai UTS     : {self.uts[index]}")
            print(f"Nilai UAS     : {self.uas[index]}")
            print(f"Nilai TUGAS   : {self.tugas[index]}")
        else:
            print("NAMA {0} TIDAK ADA!".format(nama))
```

## Penjelasan 
> Pada bagian dari `daftar_nilai.py` berisi program dengan perintah menambahkan data, hapus data, ubah data NIM,
dan mencari salah satu data yg sudah di input.


#### Tampilan output tambah data :
![02](https://user-images.githubusercontent.com/115614668/211688561-50f69df4-7c44-441c-b9ac-d8d4b152a637.png)  
#### Tampilan output hapus data :
![03](https://user-images.githubusercontent.com/115614668/211688822-4d4794bb-a8f8-4b92-a6ca-b2acd872965d.png)  
#### Tampilan output ubah NIM :
![04](https://user-images.githubusercontent.com/115614668/211689039-e398f23d-4a91-4cec-93cb-b985c04d7398.png)  
#### Tampilan output cari data :
![05](https://user-images.githubusercontent.com/115614668/211708058-ff5fca5c-fb94-45bd-a618-9e4dfc30dab8.png)

------------------------------------------------------------------------------------------------------------------------------------------

## View Nilai
> `view_nilai.py` berisi sourcode yg berfungsi menampilkan atau mencetak seluruh data yang telah di input sebelumnya, program ini menampilkan nama dan nim mahasiswa, nilai UAS, UTS, dan tugas



``` Python
from model import daftar_nilai
data = daftar_nilai.Data_mahasiswa()
# Menampilkan seluruh data 
def lihat():
    for i in range(len(data.nama)):
        print(f"\nData ke -{i+1}")
        print(f"Nama Mahasiswa: {data.nama[i]}")
        print(f"NIM Mahasiswa : {data.nim[i]}")
        print(f"Nilai UTS     : {data.uts[i]}")
        print(f"Nilai UAS     : {data.uas[i]}")
        print(f"Nilai TUGAS   : {data.tugas[i]}")
```

## Penjelasan 
> Di program ini terdapat modul yg menyambungkan `view_nilai.py` kedalam file program `daftar_nilai.py` 
dengan syntax `from model import daftar_nilai`. Fungsi ny mirip seperti `input = "[(C)ari]"`, tapi fitur ini menampilkan
seluruh data yg sudah di input.


------------------------------------------------------------------------------------------------------------------------------------------

## Input Nilai
> `input_nilai.py` berisi code yg berfungsi untuk menginput data yaitu nilai


``` Python
from model import daftar_nilai
data = daftar_nilai.Data_mahasiswa()
def nilai():
        print("Input Nilai")
        print("="*15)
        input_nama = input("Masukan Nama   : ")
        if input_nama in data.nama:
            index = data.nama.index(input_nama)
            data.uts[index]     = int(input("Nilai UTS      : "))
            data.uas[index]     = int(input("Nilai UAS      : "))
            data.tugas[index]   = int(input("Nilai Tugas    : "))
            print("\nData nilai berhasil di input!")
        else:
            print("NAMA {0} TIDAK ADA! / ANDA BELUM MENAMBAH DATA".format(input_nama))
```

## Penjelasan 
> Di program ini terdapat modul yg menyambungkann `input_nilai.py` kedalam file program `daftar_nilai.py` 
dengan syntax `from model import daftar_nilai`. Fitur ini khusus untuk menginput nilai

#### Tampilan output `input_nilai.py` :
![06](https://user-images.githubusercontent.com/115614668/211708382-42a6aa04-9c16-4df7-ae40-3ace6e03bc03.png)
