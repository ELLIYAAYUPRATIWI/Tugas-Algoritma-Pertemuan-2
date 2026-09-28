# Tugas Algoritma dan Struktur Data Pertemuan 2
**Nama:** Elliya Ayu Pratiwi
**NIM:** 1251170156
**Kelas:** 3D

## STUDI KASUS: Sistem Transaksi dan Validasi Toko Buku Modern

### 1. Analisis Komponen

   a. Identifikasi Variable dan Tipe Data 
   
| No |  Nama Variabel  | Tipe Data |          Keterangan          |
|----| -------------   | --------- | ---------------------------  |
| 1. |  is_member      |   Boolean |    Status Keanggotaan (T/F)    |                                                        | 2. |  jumlah_buku  |     Integer  |   Jumlah buku yang dibeli     |                                                     
| 3. |  total_awal    |     Real   |    Total sebelum dapat diskon  |                                                        
| 4. |  nominal_diskon  |   Real    |   Jumlah potongan harga dalam rupiah |                
| 5. |  total_bayar      |  Real     |  Total yang harus dibayar setelah diskon   |

    
   b. Struktur data kontrol yang digunakan 
      
  a). Sequence: Perintah dilakukan secara berurutan. Input data -> validasi -> menghitung diskon -> menghitung total bayar -> menampilkan output.
      
  b). Loop: Dipakai Waktu input salah. Total awal < 0 atau jumlah buku < 1 ini diulang sampai datanya benar. Validasi harus dilakuin dan minimal satu kali  memeriksa, dan bisa memakai REPEAT-UNTIL untuk memeriksa kondisi di akhir.
      
  c). Selectin: Dipakai buat menentukan diskon yang didapatkan seperti "Apakah orang tersebut adalah member?" Jika iya, akan masuk ke rules member, jika tidak maka tidak akan masuk ke rules member atau masuk ke non-member. Ini bisa disebut sebagai if-else-then


### 2. PSEUDOCODE


  ```
PROGRAM SistemTransaksiTokoBuku       
                                                                                                         
   DEKLARASI:                                                             
    is_member: boolean                                                    
    jumlah_buku: integer                                                  
    total_awal: real                                                      
    nomial_diskon: real                                                   
    total_bayar: real                                                     
                                                                          
   ALGORITMA:                                                             
   INPUT (is_member)                                                      
   INPUT (jumlah_buku)                                                    
   INPUT (total_awal)                                                     
                                                                          
    IF (total_awal < 0 OR (jumlah_buku < 1) THEN                          
       OUTPUT ("Input tidak valid. Silahkan masukkan ulang data.")        
     ENDIF                                                                
                                                                          
   UNTIL (total_awal >= 200000 dan jumlah_buku >= 1)                      
   nominal_diskon <- 0                                                    
                                                       
   IF (is_member=TRUE) THEN                                               
       nominal_diskon <- total diskon x 10%                               
                                                                          
       IF (total_awal >= 200000 AND jumlah_buku >= 3) THEN                
            nominal_diskon ← total_awal × 15%                           
         ENDIF                                                            
                                                                         
   ELSE                                                                   
                                                                          
      IF (total_awal >= 300000) THEN                                      
        nominal_diskon ← total_awal × 5%                                 
      ELSE                                                                
        nominal_diskon ← 0                                               
      ENDIF                                                               
 
   ENDIF                                                                  
                                                                         
   total_bayar ← total_awal - nominal_diskon                              
                                                                          
   OUTPUT(nominal_diskon)                                                
   OUTPUT(total_bayar)                                                    
                                                                          
  END PROGRAM
```


### 3. Table Trace 
1) Kasus A: is_member = True, total_awal = 250000, jumlah_buku = 4
      
| Langkah |        Aksi          |       Kondisi yang diuji         |          Hasil          |
|-------| ----------------------- | ------------------------------ | ---------------------------|
|  1.   | Baca input lalu validasi |   250000 >= 0 AND 4 >= 1     |     Valid, loop stop      |       
|  2.   |     Cek is_member        |     is_member = True          |   Masuk ke aturan member |
|  3.   |    Cek syarat member     | 250000 >= 200000 AND 4 >= 3   |   Kedua syarat terpenuhi |            
|  4.   |  Hitung nominal_diskon   |        250000 x 0.15          |          375000         |                
|  5.   |  Hitung total_bayar      |   250000 - 37500            |       212500               |
    
  _Output: nominal_diskon = 37500, total_bayar = 212500_
        

2) Kasus B: is_member = False, total_awal = 350000, jumlah_buku = 2
      
| Langkah |        Aksi          |       Kondisi yang diuji         |          Hasil          |
|-------| ----------------------- | ------------------------------ | ---------------------------|
|  1.   | Baca input lalu validasi |   350000 >= 0 AND 2 >= 1      |     Valid, loop stop      |       
|  2.   |     Cek is_member        |     is_member = True          |   False, masuk cabang ELSE |
|  3.   | Cek total_awal >= 300000 |   Cek total_awal >= 300000    |        Benar            |            
|  4.   |  Hitung nominal_diskon   |        350000 x 0.05          |          17500        |                
|  5.   |  Hitung total_bayar      |   350000 - 17500            |        332500               |
      
  _Output: nominal_diskon = 17500, total_bayar = 332500_
        

 3) Kasus C: total_awal = -50000 (salah) -> dikoreksi jadi 100000; is_member = False, jumlah_buku = 1

| Langkah |        Aksi          |       Kondisi yang diuji         |          Hasil          |
|-------| ----------------------- | ------------------------------ | ---------------------------|
|  1.   |   Input pertama dibaca   |       total_awal < 0          |        Tidak valid         |             
|  2.   | Input yang dikoreksi dibaca|     100000 >= 0 AND 1 >= 1  |         Valid              |
|  3.   |   Cek is_member           |   is_member = True            |        False              |            
|  4.   |  Cek total_awal >= 300000 |        100000 >= 300000       |    Tidak ada diskon       |                
|  5.   |  Hitung nominal_diskon    |        100000 x 0             |            0              |
|  6.   |   Hitung total_bayar      |        100000 - 0            |        100000              |
      
  _Output: nominal_diskon = 0, total_bayar = 100000_
