---
layout: post
title: "WEB DESIGN EDUCATIONAL CONTEST #3 EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---

### Penulis Soal


| Judul Soal                                | Author | Editorialis |
| ----------------------------------------- | ------ | ----------- |
| Div 2B. Klembu dan Es Krim                | Ainun  | Ainun       |
| Div 2C. Jangan Aneh - Aneh                | Elrond | Elrond      |
| Div 1B/2D. Nilai Rapor Epen               | Ainun  | Elrond      |
| Div 1C/2E. Tugas lagi, Tugas lagi!        | Elrond | Elrond      |
| Div 1D/2F. Kecemburuan dalam Persahabatan | Arie   | Elrond      |
| Div 1E. Tamu Spesial                      | Elrond | Ainun       |
| Div 1F. Harta, Tahta, dan Ranking 1       | Ainun  | Ainun       |

---

## 2B. Klembu dan Es Krim

Misalkan $$p$$ adalah banyak kotak es krim, $$q$$ adalah banyak es krim pada setiap kotak, dan $$r$$ adalah kapasitas perut Klembu per harinya. Maka, stok es krim klembu akan habis dalam $$\frac{p \times q}{r}$$ hari. Sehingga hari ke-$$\frac{p \times q}{r}+1$$ kedua orang tua Klembu harus beli es krim lagi.

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
  int p,q,r;
  cin >> p >> q >> r;
  cout << ((p*q)/r)+1 << endl;
}
```

**Kompleksitas waktu** : $$O(1)$$

---

## 2C. Jangan Aneh - Aneh

Kita tampung terlebih dahulu nama – nama hari pada sebuah `array` dengan tipe data string secara berurutan.

Untuk mencari tahu hari apa setelah $$N$$ hari adalah kita pertama mencari indeks hari tersebut. Karena hari – hari tersebut berurutan (0 based), kita anggap :

| Hari | Indeks |
| ---- | ------ |
| Senin | 0 |
| Selasa | 1 |
| Rabu | 2 |
| Kamis | 3 |
| Jumat | 4 |
| Sabtu | 5 |
| Minggu | 6 |

Untuk mencari hari apa setelah $&N&$ hari, kita dapat mencarinya dengan $$N \mod 7$$. Dan untuk mencatat pada apa hari ini, kita dapat menambahkan indeks nya. Jadi jawabannya ada di  `Hari[((n%7) + (index % 7)) % 7]`

Berikut solusi dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
	string s;
	string hari[7] = {"senin","selasa","rabu","kamis","jumat","sabtu","minggu"};
	unsigned long long int n;
	cin >> s >> n;
	
	int index;
	if(s == "senin") index = 0;
	else if(s == "selasa") index = 1;
	else if(s == "rabu") index = 2;
	else if(s == "kamis") index = 3;
	else if(s == "jumat") index = 4;
	else if(s == "sabtu") index = 5;
	else if(s == "minggu") index = 6;
	
	string hariapaya = hari[((n%7) + (index % 7))% 7];
	cout<<hariapaya<<endl;
}
```

**Kompleksitas waktu :** $$O(1)$$

---

## 1B/2D. Nilai Rapor Epen

Untuk mencari adanya kemunduran nilai atau tidak, kita membandingkan nilai satu – persatu pada kedua nilai di semester awal maupun di semester kedua. Jika ada satu pun nilai dari semester 2 yang turun / lebih kecil dari semester 1, maka keluarkan `ADA`, jika nilai Epen sama saja atau lebih besar keluarkan `TIDAK ADA`. Kita bisa menggunakan bool untuk menyelesaikan ini.

Berikut solusi dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
  int n,sem1[10001],sem2[10001];
  bool ada = false;
  cin >> n;
  for(int i=1; i<=n; i++){
    cin >> sem1[i];
  }
  for(int i=1; i<=n; i++){
    cin >> sem2[i];
  }
  for(int i=1; i<=n; i++){
    if(sem2[i] < sem1[i]){
      ada = true;
      break;
    }
  }
  if(ada) cout << "ADA" << endl;
  else cout << "TIDAK ADA" << endl;
}
```

**Kompleksitas waktu :** $$O(N)$$

---

## 1C/2E. Tugas lagi, Tugas lagi!

Pada problem ini kita mencari selisih jumlah elemen – elemen pada diagonal utama dan jumlah elemen – elemen pada diagonal samping. Diagonal utama adalah diagonal yang membentuk dari sisi pojok kiri atas sampai sisi pojok kanan bawah.

Diagonal utama pada matriks dapat didapatkan jika indeks baris dan indeks kolom sama. Diagonal samping pada matriks dapat didapatkan jika matriks indeks [sisi – baris + 1] dan indeks kolom sama.

Karena kita mencari selisih, maka kita mencari nilai mutlak dari diagonal utama dikurangi diagonal samping

Berikut solusi dalam bahasa C++ :

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
  int n, arr[1001][1001],utama = 0, samping = 0;
  cin >> n;
  for(int i=1; i<=n; i++){
    for(int j=1; j<=n; j++){
      cin >> arr[i][j];
    }
  }
  
  for(int i=1; i<=n; i++){
    for(int j=1; j<=n; j++){
      if(i == j) utama += arr[i][j];
      if(n-i+1 == j) samping += arr[i][j];
    }
  }
  
  cout << abs(utama - samping) << endl;
}
```

**Kompleksitas waktu :** $$O({N}^{2})$$

---

## 1D/2F. Kecemburuan Dalam Persahabatan

Pertama kita mengecek apakah setengah panjang dan setengah lebar bingkai kurang dari jarak antara bingkai dan foto. Jika tidak, maka keluarkan “bingkai kurang besar.” Jika iya, maka kita keluarkan pola nya. Langkah – langkah membuat pola nya :

1. Membuat ketebalan pada sisi panjang bagian kiri (jika variabel iterasi baris kurang sama dengan tebal)
2. Membuat ketebalan pada sisi atas (jika variabel iterasi kolom kurang sama dengan tebal)
3. Membuat ketebalan pada sisi panjang bagian kanan (jika variabel iterasi baris lebih dari (baris – tebal))
4. Membuat ketebalan pada sisi bawah (jika variabel iterasi kolom lebih dari (kolom – tebal))

Contoh solusi pada bahasa C++ :

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int a,b,c;
	cin >> a >> b >> c;
	if (2 * c < a && 2 * c < b) {
	    for (int i = 1; i <= a; i++) {
    	        for (int j = 1; j <= b; j++) {
    			if (i <= c || j <=c || i>a-c || j>b-c) cout << "*";
    			else cout << " ";
                }
                cout << endl;
	        }
	}
        else cout << "bingkai tidak cukup ruang untuk diberi foto" << endl;
}
```

**Kompleksitas waktu :** $$O(N^{2})$$

---

## 1E. Tamu Spesial

Karena 3 tanggal yang diketahui berurutan, kita cukup menyimpan tanggal awal dan tanggal akhirnya saja. Misalkan tanggal awal adalah `mi` dan tanggal akhir adalah `ma`. Kemudian, kasus terburuk nya adalah ketika tanggal ke $$mi-(n-3)$$ merupakan tanggal terakhir datangnya tamu spesial dan ketika tanggal ke $$ma+(n-3)$$. Untuk $$n = 5$$, visualisasi terlihat pada gambar dibawah:

<div align="center">
    <img src="https://i.imgur.com/QCK9szt.png"/>
</div>    


Maka, tanggal aman bagi Romeo ada pada tanggal sebelum tanggal pertama atau tanggal setelah tanggal terakhir. Tanggal sebelum tanggal pertama adalah $$mi-(n-3)-1$$ dan tanggal sebelum tanggal terakhir adalah $$ma+(n-3)+1$$. Kemudian kita cukup cek apakah kedua tanggal tersebut ada pada jangkauan kalender.

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
  string s[101];
  int n,mi=INT_MAX,ma=INT_MIN;
  cin >> n;
  int a=1;
  for(int i=1; i<=5; i++){
    for(int j=1; j<=6; j++){
      cin >> s[a];
      if(s[a]=="X"){
        mi=min(mi,a);
        ma=max(ma,a);
      }
      a++;
    }
  }
  int sisa=n-3;
  if(mi - sisa > 0) s[mi-sisa-1]="O";
  if(ma + sisa + 1 <= 30) s[ma+sisa+1]="O";
  for(int i=0; i<=4; i++){
    for(int j=1; j<=6; j++){
      cout <<s[(i*6)+j];
      if(j < 6) cout << " ";
    }
    cout << endl;
  }
}
```

**Kompleksitas waktu** : $$O(N)$$

---

## 1F. Harta, Tahta, dan Ranking 1

Supaya uang yang dikeluarkan Epen minimum, maka Epen harus menyogok gurunya yang memiliki jasa paling besar. Untuk mendapatkan ini, cukup urutkan array jasa gurunya secara menurun lalu lakukan *looping* sampai semua mata pelajaran telah berhasil dirubah menjadi 100.

Apabila Epen tidak bisa membuat seluruh nilainya menjadi 100, maka ia tidak berhasil menjadi ranking 1. Sehingga ia tidak mengeluarkan uang sama sekali. Pada kasus ini, cukup keluarkan 0.

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
  long long MOD=1e9+7; //mirip kayak 10^9 + 7
  long long n,m,l,k[2000];
  cin >> n >> m >> l;
  for(int i=1; i<=m; i++) cin >> k[i];
  for(int i=1; i<=m; i++){
    for(int j=i+1; j<=m; j++){
      if(k[i]<k[j]) swap(k[i],k[j]);
      //swap(a,b) : inbuilt function untuk
      //menukar dua buah nilai variabel
    }
  }
  long long cnt=0,ans=0;
  for(int i=1; i<=m; i++){
    if(cnt>=n) break;
    else {
      cnt+=k[i];
      ans+=l;
      ans%=MOD;
    }
  }
  if(cnt<n) cout << "0\n";
  else cout << ans << endl;
}
```

Algoritma pengurutan diatas adalah *Bubble Sort*. Anda bisa mempelajari lebih lanjut [disini.](https://www.geeksforgeeks.org/bubble-sort/)

**Kompleksitas waktu** : $$O({N}^{2})$ atau $O(N \log{N})$$
