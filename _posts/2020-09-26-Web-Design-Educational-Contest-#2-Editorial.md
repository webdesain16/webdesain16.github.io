---
layout: post
title: "WEB DESIGN EDUCATIONAL CONTEST #2 EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---

### Penulis Soal


| Judul Soal                      | Author          | Editorialis |
| ------------------------------- | --------------- | ----------- |
| B. Lokasi Pertemuan Asian Games | ATHA2DJ         | QWludW4g    |
| C. Wisma Peserta                | QWludW4g        | QWludW4g    |
| D. Mengantri Masuk Stadion      | QWludW4g        | QWludW4g    |
| E. Menonton Pertandingan        | Elrond+QWludW4g | Elrond      |
| F. Petak Pemenang               | Elrond          | Elrond      |
| G. Petak Pemenang               | Elrond          | Elrond      |

---

## B. Lokasi Pertemuan Asian Games

Kita memiliki dua kasus penting, yaitu :

1. **Ketika titik $$(X,Y)$$ berada di luar kertas**

   Pada kasus ini, cek apakah titik $$(X,Y)$$ berada dalam kertas tersebut. Jika $$X < - N$$ dan $$X > N$$ dan $$Y < -N$$ dan $$Y > N$$ langsung outputkan `Di Luar Jangkauan` karena titik tersebut berada diluar kertas dan program berhenti sampai sini.

2. **Ketika titik $$(X,Y)$$ berada didalam kertas**

	<div align="center">
	    <img src="https://i.imgur.com/k9DwXud.png"/>
	</div>

   Pada kasus ini, nilai $$X$$ dan $$Y$$ berada diantara $$–N$$ dan $$N$$ eksklusif. Observasi gambar diatas, maka kita tahu bahwa urutan sumbu yang kita simpan atau outputkan adalah :
       1) sumbu-$$x$$ negatif, sumbu-$$y$$ positif
       2) sumbu-$$x$$ positif, sumbu-$$y$$ positif
       3) sumbu-$$x$$ negatif, sumbu-$$y$$ negatif
       4) sumbu-$$x$$ positif, sumbu-$$y$$ negatif

   Maka untuk kasus ini, cukup lakukan dua nested loop dengan loop terluar menyatakan sumbu-$$y$$ yang sedang kita jelajahi dan loop yang dalam menyatakan sumbu-$$x$$ yang sedang kita jelajahi.

   Ada 3 kasus saat kita sedang menjelajahi kedua sumbu, yaitu:

   1. **Titik yang kita jelajahi sama dengan titik ($X,Y$)** maka outputkan `#`
   2. **Titik yang kita jelajahi merupakan bagian dari sumbu-$$X$$ atau sumbu-$$Y$$** maka outputkan `*`
   3. **Selain kedua kasus diatas**, outputkan  (spasi)

   Dan jangan lupa untuk meng-outputkan ` ` (spasi) diantara dua karakter. Berikut adalah contoh program dalam bahasa C++:

   ```cpp
   #include <bits/stdc++.h>
   using namespace std;
   int main(){
     int n,x,y;
     cin >> n >> x >> y;
     if(x >= -n && x <= n && y >= -n && y <= n){
       for(int i = n; i >= -n; i--){
         for(int j = -n; j <= n; j++){
           if(i == y && j == x) cout << "#";
           else if(i == 0 || j == 0) cout << "*";
           else cout << " ";
           if(j < n) cout << " ";
         }
         cout << endl;
       }
       cout << "( " << x << " , " << y << " )\n";
     } else cout << "Di Luar Jangkauan\n";
     return 0;
   }
   ```

   Anda juga bisa memanfaatkan array 2D pada soal ini. Contoh program diserahkan kepada pembaca sebagai latihan.

**Kompleksitas waktu** : $$O(N^{2})$$

---

## C. Wisma Peserta

Pertama, buat sebuah array 1D `arr` dengan tipe data boolean yang menyatakan apakah kamar ke-$$i$$ berisi pasien ODP/PDP. Kemudian isi array tersebut dengan `false` yang menyatakan tidak ada pasien ODP/PDP pada kamar ke-$$i$$. Lalu lakukan looping dari $$1$$ sampai $$K$$ untuk membaca masukan yang menyatakan nomor-nomor kamar yang berisi pasien ODP/PDP, misalkan nomor kamar tersebut disimpan pada variabel `rooms`. Lalu ubah nilai dari `arr[rooms]` menjadi `true`.

Setelah itu, lakukan looping dari kamar nomor $$1$$ sampai $$N$$. Apabila nomor kamar yang sedang kita jelajahi terdapat pasien ODP / PDP atau `arr[i] = true`, maka ubah tetangga kanan dan kirinya (apabila ada) menjadi `true`.

Terakhir, misalkan kita memiliki variabel `ans` dengan tipe data integer. Atur `ans = 0`. Kemudian lakukan looping dari kamar nomor $$1$$ sampai $$N$$, apabila `arr[i] = true`, maka `ans++`. Setelah looping berhenti, cetak `ans` sebagai jawaban kita. Berikut adalah contoh program dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
  bool arr[200005];
  int N,K,ans=0;
  cin >> N >>> K;
  for(int i = 1; i <= N; i++){
    arr[i] = false;
  }
  for(int i = 0; i < K; i++){
    int rooms;
    cin>>rooms;
    arr[rooms] = true;
  }
  for(int i = 1; i <= N; i++){
    if(x < N) arr[x+1] = true;
    if(x > 1) arr[x-1] = true;
  }
  for(int i = 1; i <= N; i++)
    if(arr[i] == true) ans++;
  cout << ans << "\n";
}
```

**Kompleksitas waktu** : $$O(N)$$


---

## D. Mengantri Masuk Stadion

Misalkan banyaknya orang yang mengantri ada $$5$$, maka antrian yang lama berbentuk:

 

| Nomor Antrian | 1    | 2    | 3    | 4    | 5    |
| ------------- | ---- | ---- | ---- | ---- | ---- |
| Nomor Tiket   | 1    | 2    | 3    | 4    | 5    |

Sedangkan antrian yang baru berbentuk :

| Nomor Antrian | 1    | 2    | 3    |
| ------------- | ---- | ---- | ---- |
| Nomor Tiket   | 1    | 3    | 5    |

| Nomor Antrian | 1    | 2    | 3    |
| ------------- | ---- | ---- | ---- |
| Nomor Tiket   | 4    | 2    |      |

Kita memiliki dua kasus penting, yaitu :

1. **Nomor tiket Atung ganjil**

   Pada kasus ini, misalkan nomor tiket Atung adalah $$K$$. Berdasarkan tabel diatas, maka nomor antrian yang baru adalah $$(K$$ $$div$$  $$2) + 1$$. Maka outputkan nilai dari $$(K$$ $$div$$  $$2) + 1$$

2. **Nomor tiket Atung genap**

   Pada kasus ini, kita memiliki dua kasus lagi, yaitu:

   1. **Banyak orang yang mengantri adalah ganjil**

      Misalkan nomor tiket Atung adalah $$K$$ dan banyak orang yang mengantri adalah $$N$$. Berdasarkan tabel diatas, maka nomor antrian yang baru adalah $$((N-1-K)$$ $$div$$ $$2 ) + 1$$ sehingga cukup outputkan $$((N-1-K)$$ $$div$$ $$2 ) + 1$$

   2. **Banyak orang yang mengantri adalah genap**

      Misalkan banyaknya orang yang mengantri ada $$4$$, maka antrian yang lama berbentuk:

      | Nomor Antrian | 1    | 2    | 3    | 4    |
      | ------------- | ---- | ---- | ---- | ---- |
      | Nomor Tiket   | 1    | 2    | 3    | 4    |

      Sedangkan antrian yang baru berbentuk :

      | Nomor Antrian | 1    | 2    |
      | ------------- | ---- | ---- |
      | Nomor Tiket   | 1    | 3    |

      | Nomor Antrian | 1    | 2    |
      | ------------- | ---- | ---- |
      | Nomor Tiket   | 4    | 2    |

      Misalkan nomor tiket Atung adalah $$K$$ dan banyak orang yang mengantri adalah $$N$$. Berdasarkan tabel diatas, maka nomor antrian yang baru adalah $$((N-K)$$ $$div$$ $$2 ) + 1$$ sehingga cukup outputkan $$((N-K)$$ $$div$$ $$2 ) + 1$$

Berikut adalah contoh program dalam bahasa C++:

```cpp
//Mengantri tiket masuk
#include <bits/stdc++.h>
using namespace std;
int main(){
  int n,k;
  cin>>n>>k;
  if(k%2==1) cout<<(k/2)+1<<endl;
  else {
    if(n%2==1) cout<<(n-1-k)/2 + 1<<endl;
    else cout<<(n-k)/2 + 1<<endl;
  }
  return 0;
}
```

**Kompleksitas waktu :** $$O(1)$$

---

## E. Menonton Pertandingan

Kita sediakan array 2 dimensi bernama `kursi` dan sebuah variabel bernama `kosong` dan diinisiasikan dengan nilai $$0$$. Kita juga menyediakan varaibel `yeyy` bertipe data boolean dan diinisiasikan dengan nilai `false`. Variabel `yeyy` akan kita inisiasikan `true` jika Atung dan Kaka bisa menonton bersama.

Kita menggunakan *nested loop* untuk mengecek semua kursi. Jika kursi pada baris ke – $$i$$ dan kolom ke – $$j$$ bernilai $$0$$, maka kita *increment* (menambahkan $$1$$) pada variabel kosong yang menandakan ada berapa kursi kosong di blok $$N \times M$$ tersebut sekaligus kita cek apakah kursi sebelah kiri dan kanannya kosong.

Kursi sebelah kiri adalah kursi baris ke – $$i$$ dan kolom ke $$j – 1$$. Jika kursi baris ke – $$i$$ dan kolom ke – $$j$$ serta kursi sebalah kirinya kosong, maka kita inisiasikan nilai `true` pada variabel `yeyy`

Untuk menentukan output, kita pertama menentukan apakah jumlah kursi yang ada di blok $$N \times M$$ lebih dari atau sama dengan dua. Jika tidak, maka sudah jelas Kaka dan Atung tidak jadi nonton karena tidak ada atau hanya satu kursi kosong yang tersedia. Jika kursi kosong lebih besar atau sama dengan dua, maka kita cek lagi apakah mereka duduk bersebalahan atau tidak. Berikut adalah contoh program dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int n,m,kursi[1001][1001], kosong = 0;
int main(){
  cin>>n>>m;
  bool yeyy=false;
  for(int i=1; i<=n; i++){
    for(int j=1; j<=m; j++){
      cin>>kursi[i][j];
      if(kursi[i][j]==0) kosong++;
      if(j>1 && kursi[i][j]==0 && kursi[i][j-1]==0) yeyy=true;
    }
  }
  if(kosong>=2){
    if(yeyy) cout<<"best friend forever\n";
    else cout<<"yah terpisah :(" << endl;
  } else cout<<"yah, gajadi nonton" << endl;
}
```

**Kompleksitas waktu :** $$O(NM)$$

---

## F. Lompatan Penentuan

Setelah membaca deskripsi soal, dapat kita simpulkan bahwa *smash* yang dilakukan oleh Kaka berhasil **Jika dan hanya jika** lompatan Kaka lebih tinggi dari seperempat tinggi net dan lompatan Kaka lebih tinggi dari lompatan tertinggi pemain tim lawan Kaka.

Untuk mencari tahu lompatan tertinggi pada tim lawan, kita bisa membuat variabel baru `maksi` untuk menampung elemen dengan nilai terbesar pada sebuah pada sebuah array. Kita inisiasi `maksi` dengan angka negatif (kita inisiasi seminimal mungkin, bahkan dibawah batasan). Lalu kita jalankan perulangan $$1$$ sampai $$K$$ untuk input array sekaligus mencari elemen terbesar pada array, jika array elemen ke – $$i$$ lebih besar daripada `maksi`, maka *assign* nilai array indeks ke – $$i$$ pada variabel `maksi`. Setelah iterasi selasai, kita akan mempunyai data lompatan tertinggi pada tim lawan dan kita bisa mulai melakukan pengecekan pada kedua kondisi wajib yang wajib terpenuhi agar *smash* Kaka berhasil.

Berikut adalah contoh program dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

long long int n,m,k,arr[200005],maksi=-1;
int main(){
  
  cin >> n >> m >> k;
  for(int i=1; i<=k; i++){
    cin >> arr[i];
    if(arr[i]>maksi) maksi = arr[i];
  }
  if((4*m) > n && m > maksi) cout << "Berhasil" << endl;
  else cout << "Masi ada kesempatan lain, jangan menyerah" << endl;
}
```

**Kompleksitas waktu** : $$O(N)$$

---

## G. Petak Pemenang

Jalan tercepat untuk mencapai petak `end` dari petak `start` adalah melalu diagonal utamanya. Jika kita observasi, jalur diagonal dari petak `start` menuju petak `end` adalah saat koordinat dari baris dan kolomnya sama

<div align="center">
    <img src="https://i.imgur.com/j4nwul4.png"/>
</div>


Soal ini dapat diselesaikan dengan *nested loop* (perulangan dalam perulangan) namun solusi tersebut sangatlah lama, maka kita bisa menggunakan perulangan biasa.

Pada solusi yang menggunakan *nested loop*, kita mengeluarkan output berupa koordinat jika nilai variabel iterasi pada for yang ada di luar sama dengan nilai variabel iterasi pada for yang ada di dalam. Berikut adalah contoh program yang mengunakan *nested loop*.

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
  int n;
  cin>>n;
  for(int i=1; i<=n; i++){
    for(int j=1; j<=n; j++){
      if(i == j) cout << i << " "<< j << endl;
    }
  }
}
```

Jika kita perhatikan lagi pernyataan bahwa jalur diagonal akan terbentuk saat koordinat baris dan kolomnya sama, maka kita hanya perlu mengiterasi dari $$1$$ sampai $$N$$ lalu mengeluarkan
variabel iterasi yang dioutputkan dua kali dipisahkan oleh spasi. Berikut adalah contoh program dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
  int n;
  cin>>n;
  for(int i=1; i<=n; i++){
    cout << i << " " << i << endl;
  }
}
```

**Kompleksitas waktu** : $$O(N)$$