## 20104006_Aditya-Rizkiawan-Nugraha_S1SE4A_Pemrograman2
Mata kuliah Pemrograman2

### DASAR TEORI 
* Package <br>
Sarana/ cara pengelompokan dan pengorganisasian kelas - kelas dan interface yang sekelompok menjadi suatu unit tunggal dalam library. Package juga memiliki hak akses seperti pengaruh terhadap method main(). Suatu cara memanage atau mengemlompokan class - class yang dibuat berdasarkan kesamaan atau kemiripan fungsi.

* Import Class <br>
Merupakan kata kunci untuk melibatkan class class lain yang terhimpun di dalam package yang akan di import. This hanya bisa digunakan dalam class tidak di dalam main, Jika dilakukan di dalam main maka akan terjadi error. 
* This <br>
This merupakan referensi ke objek yang sedang aktif dan digunakan untuk di dalam method untuk mewakili nama kelas bersangkutan. 



<hr>

### PRAKTIKUM PERCOBAAN
<hr>
Soal : <br>
1. Memakai kata kunci this pada overloading constructor <br> 

<br>[Kodingan Mahasiswa](https://github.com/adityarizn31/20104006_Aditya-Rizkiawan-Nugraha_S1SE4A_Pemrograman2/blob/modul5/Percobaan/Mahasiswa.java)
<hr>

 ```java
 package Modul5.Percobaan;

public class Mahasiswa {
    private int nrp;
    private String nama;


    public Mahasiswa() {
        this(0,"");
    }

    public Mahasiswa(String nama) {
        this(0, nama);
    }

    public Mahasiswa(int nrp, String nama){
        this.nrp = nrp;
        this.nama = nama;


    }
}
```
<br> **Penjelasan** : Pada class mahasiswa terdapat dua variabel dengan tipe data yang berbeda. Ada private int nrp dan private String nama. Selanjutya dibuat 3 constructor yang tidak menggunakan parameter dan menggunakan parameter namun berbeda yaitu Mahasiswa dengan di dalamnya terdapat this(0,"") lalu ada Mahasiswa (String nama) dan Mahasiswa (int nrp, String nama) yang terdapat this.nrp dan this.nama

<hr>


<br>
2. Menggunakan Package dan Import

<br>[Kodingan Kelas](https://github.com/adityarizn31/20104006_Aditya-Rizkiawan-Nugraha_S1SE4A_Pemrograman2/blob/modul5/Percobaan/Sekolah/Kelas.java)
<hr>

```java
package Modul5.Percobaan.Sekolah;

import Modul5.Percobaan.Mahasiswa;

public class Kelas {
    private int kodekelas;
    private String namakelas;
    private Mahasiswa mahasiswa;

    public Kelas (int kode, String nama){
        this.kodekelas = kode;
        this.namakelas = nama;
    }

    public void SetMhs(Mahasiswa mhs){
        this.mahasiswa = mhs;
    }
}
```
<br> **Penjelasan** : Di dalam class kelas terdapat dua variabel yaitu int kodekelas, String namakelas dan objek dari kelas Mahasiswa mahasiswa. Selanjutnya ada constructor dan method yaitu kelas dengan parameter int kode dan String nama dan method void set mahasiswa yang berfungsi mengisikan kepada variabel mhs.

<br>[Kodingan Mahasiswa](https://github.com/adityarizn31/20104006_Aditya-Rizkiawan-Nugraha_S1SE4A_Pemrograman2/blob/modul5/Percobaan/Sekolah/Mahasiswa.java)

<hr>

```java
package Modul5.Percobaan.Sekolah;

public class Mahasiswa {
    private int nrp;
    private String nama;

    public Mahasiswa(int nrp, String nama) {
        this.nrp = nrp;
        this.nama = nama;
    }
}
```
<br> **Penjelasan** : Di dalam kelas Mahasiswa ini ada dua varibale yang itu int nrp dan String nama dan ada juga contructor dengan parameter yang sama seperti variabel yang di dalamnya terdapat this.nrp dan this.nama.

<hr>

<br>
<br>
<hr>

### PRAKTIKUM LATIHAN
<hr>
3. Mengimplementasikan UML Class Diagram dalam program untuk package Perbankan

<br> Transformasikan class diagram di atas ke dalam bentuk program !! Tulislah listing program tersebut sebagai pengetesan

[Kodingan Mahasiswa]()<br>

```java
package Modul5.Latihan.Perbankan;

public class Nasabah {

    String namaAwal;
    String namaAkhir;
    Tabungan tabungan;

    public Nasabah(String namaAwal, String namaAkhir){
        this.namaAwal = namaAwal;
        this.namaAkhir = namaAkhir;
    }

    public String getNamaAwal() {
        return namaAwal;
    }

    public String getNamaAkhir() {
        return namaAkhir;
    }

    public void setTabungan(Tabungan tabungan) {
        this.tabungan = tabungan;
    }

    public Tabungan getTabungan() {
        return tabungan;
    }
}
```

<br>[Kodingan Tabungan]()

```java
package Modul5.Latihan.Perbankan;

public class Tabungan {
    int saldo;

    public Tabungan (int saldo){
        this.saldo = saldo;
    }

    public int getSaldo (){
        return saldo;
    }

    public void setSaldo(int saldo) {
        this.saldo = saldo;
    }

    public void simpanUang(int jumlah){
        this.saldo = saldo + jumlah;
    }

    public boolean ambilUang(int jumlah){
        if (jumlah < this.getSaldo()) {
            this.setSaldo(getSaldo()-jumlah);
            return true;
        } else {
            return false;
        }
    }
}
```

<br> [Kodingan TesLatihan]()

```java
package Modul5.Latihan;

import Modul5.Latihan.Perbankan.Nasabah;
import Modul5.Latihan.Perbankan.Tabungan;


public class TesLatihan {
        public static void main(String[] args) {
            int tmp;

            boolean status = true;

            Nasabah nasabah=new Nasabah("Agus","Daryanto");
            System.out.println("Nasabah atas nama : " +
                    nasabah.getNamaAwal() + " " + nasabah.getNamaAkhir());
            nasabah.setTabungan(new Tabungan(5000));
            tmp=nasabah.getTabungan().getSaldo();
            System.out.println("Saldo awal : " + tmp);
            nasabah.getTabungan().simpanUang(3000);
            System.out.println("Jumlah uang yang disimpan : 3000");
            status=nasabah.getTabungan().ambilUang(6000);
            System.out.print("Jumlah uang yang diambil : 6000");
            if (status) System.out.println(" ok");
            else
                System.out.println(" gagal");
            nasabah.getTabungan().simpanUang(3500);
            System.out.println("Jumlah uang yang disimpan : 3500");
            status=nasabah.getTabungan().ambilUang(4000);
            System.out.print("Jumlah uang yang diambil : 4000");
            if (status) System.out.println(" ok");
            else
                System.out.println(" gagal");
            status=nasabah.getTabungan().ambilUang(1600);
            System.out.print("Jumlah uang yang diambil : 1600");
            if (status) System.out.println(" ok");
            else
                System.out.println(" gagal");
            nasabah.getTabungan().simpanUang(2000);
            System.out.println("Jumlah uang yang disimpan : 2000");
            tmp=nasabah.getTabungan().getSaldo();
            System.out.println("Saldo sekarang = " + tmp);
    }
}
```

Hasil run menampilkan : 
<hr>

Nasabah atas nama : Agus Daryanto <br>
Saldo awal : 5000 <br>
Jumlah uang yang disimpan : 3000 <br>
Jumlah uang yang diambil : 6000 ok <br>
Jumlah uang yang disimpan : 3500 <br>
Jumlah uang yang diambil : 4000 ok <br>
Jumlah uang yang diambil : 1600 gagal <br>
Jumlah uang yang disimpan : 2000 <br>
Saldo sekarang = 3500 <br>

<hr>



### KESIMPULAN
Kesimpulan pada praktikum mengenai Package, Kata kunci this dan import class ini mahasiswa harus mengetahui terlebih dahulu
