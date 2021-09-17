---
layout: post
title: "WEB DESIGN EDUCATIONAL CONTEST #4 EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---

### Penulis Soal

| Soal | Judul soal | Author | Editorialis | Translator |
| ---- | ---------- | ------ | ----------- | ---------- |
|Div 2B|Bilangan Terbesar|Elrond|Elrond|-|
|Div 2C|Faktor Bilangan|Elrond|Elrond|-|
|Div 1B/2D|Ujian Tersusah Arpa dan Kecurangan Mehrdad yang Naif|[Batman](https://codeforces.com/profile/Batman)|Ainun|Ainun|
|Div 2E|Bilangan yang Hilang|Elrond|Elrond|-|
|Div 2F|Bilangan Urut|Elrond|Elrond|-|
|Div 1C|Bilangan Terdekat yang Menarik|[MikeMirzayanov](https://codeforces.com/profile/MikeMirzayanov)|[MikeMirzayanov](https://codeforces.com/profile/MikeMirzayanov)|Ainun|
|Div 1D|Bilangan yang Adil|[neckbotov](https://codeforces.com/profile/neckbotov)|[neckbotov](https://codeforces.com/profile/neckbotov)|Ainun|
|Div 1E|Roti Sobek|Elrond|Elrond + Ainun|-|
|Div 1F| Rantai Sepeda|[NALP](https://codeforces.com/profile/NALP)|[NALP](https://codeforces.com/profile/NALP)|Ainun|


## 2B. Bilangan Terbesar
Permasalahan ini dapat diselesaikan dengan menggunakan operasi logika **and** ``&&``. Jika suatu bilangan $$A$$ lebih besar dari bilangan $$B$$ dan bilangan $$C$$, maka sudah dapat dipastikan $$A$$ adalah yang terbesar. Begitu pula kasusnya dengan bilangan $$B$$ dan $$C$$. Namun karena ada kemungkinan banyaknya angka terbesar lebih dari satu, maka membandingkannya dengan lebih besar sama dengan.

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
  int a,b,c;
  cin >> a >> b >> c;
  if(a>=b && a>=c){
      cout << a << endl;
  }
  else if(b>=a && b >= c){
      cout << b << endl;
  }
  else if(c>=a && c>=b){
      cout << c << endl;
  }
}
```

**Kompleksitas waktu** : $$O(1)$$

---

## 2C. Faktor Bilangan

Untuk menyelesaikan permasalahan ini, kita dapat menggunakan loop dari $$i=1$$ sampai $$n$$, dan jika $$n$$ habis dibagi dengan angka ke – $$i$$, maka dapat dipastikan bahwa angka tersebut adalah faktor dari $$n$$. Lalu kita tentukan faktor itu merupakan angka ganjil atau genap menggunakan `if` condition.

Berikut solusi dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
	int n;
    cin >> n;
    for(int i=1;i<=n;i++){
        if(n%i==0){
            if(i%2==0){
                cout <<"genap" << endl;
            }
            else{
                cout <<"ganjil" << endl;
            }
        }
    }
}
```

**Kompleksitas waktu :** $$O(N)$$

---

## 1B/2D. Ujian Tersusah Arpa dan Kecurangan Mehrdad yang Naif
$$
8^{1} = 8\\
8^{2} = 64\\
8^{3} = 512\\
8^{4} = 4096\\
8^{5} = 32768\\
$$
Perhatikan bahwa angka satuan dari pola tersebut adalah 8,4,2,6,8,… . Pola ini berulang sebanyak 4 kali. Maka kita hanya perlu mencari modulo 4 dari pola tersebut. Ada 4 kasus :
1. $$N \mod 4 = 0$$, maka keluarkan $$6$$
2. $$N \mod 4 = 1$$, maka keluarkan $$8$$
3. $$N \mod 4 = 2$$, maka keluarkan $$4$$
4. $$N \mod 4 = 3$$, maka keluarkan $$2$$

Perhatikan pula ketika $$N$$ = $$0$$, maka $$8^{0}=1$$. Sehingga ketika $$N=0$$, kita hanya perlu mengeluarkan $$1$$. 

**Fun Fact** : Yang menyiapkan soal lupa masukin tc ini.
 
Berikut solusi dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n;
    cin >> n;
    if(n == 0){
        cout << 1 << endl;
    }
    else if(n%4 == 0){
        cout << 6 << endl;
    }
    else if(n%4 == 1){
        cout << 8 << endl;
    }
    else if(n%4 == 2){
        cout << 4 << endl;
    }
    else if(n%4 == 3){
        cout << 2 << endl;
    }
}
```

**Kompleksitas waktu :** $$O(1)$$

---

## 2E. Bilangan yang Hilang

Untuk mengetahui sebuah bilangan yang hilang dari sebuah deret $$1$$ sampai $$n$$ terurut secara menaik, kita bisa menjumlahkan : $$1 + 2 + 3 + 4 + … + n$$ lalu dikurangi dengan jumlah bilangan yang tidak hilang. Misal contoh input :

```
4
1 2 4
```

Penyelesaian :

Jumlah deret $$1$$ sampai $$n$$ : $$1 + 2 + 3 + 4 = 10$$
Jumlah bilangan yang tidak hilang : $$1 + 2 + 4 = 7$$

Maka bilangan yang menghilang adalah  $$10 - 7  = 3$$
Berikut solusi dalam bahasa C++ :

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    long long n,a,sum=0,sum2=0;
    cin >> n;
    for(int i=1;i<=n;i++){
        sum += i;
    }
    for(int i=1;i<n;i++){
        cin >> a;
        sum2+=a;
    }
    cout << sum - sum2 << endl;
}
```

**Kompleksitas waktu :** $$O(N)$$

---

## 2F. Bilangan Urut

Sebuah $$T\ Sequence$$ adalah di mana angka ke – $$i$$ tidak lebih besar dari angka ke – $$i + 1$$. Untuk menyelesaikan ini kita bisa menggunakan sebuah variabel penampung dan diinisiasi dengan nilai negatif. Nanti nya, variabel penampung ini berfungsi untuk menampung setiap angka yang diinputkan. Lalu jika variabel penampung itu lebih besar dari angka yang diinputkan, maka hentikan `loop` nya. Hasil yang kita keluarkan terakhir adalah variabel penampung tersebut.

**Fun Fact** : Soal ini telah mengalami revisi sebanyak 6 kali.

Contoh solusi pada bahasa C++ :

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n,a,temp=-1;
    cin >> n;
    for(int i=1;i<=n;i++){
        cin >> a;
        if(temp>a){
            break;
        }
        temp = a;
    }
    cout << temp << endl;
}
```

**Kompleksitas waktu :** $$O(N)$$

---

## 1C. Bilangan Terdekat yang Menarik

Bahkan jika kita akan meng-iterasi semua kemungkinan angka mulai $$a$$ dari dan memeriksa apakah jumlah digit dari angka saat ini habis dibagi $$4$$ , kita akan menemukan jawabannya dengan sangat cepat. Jumlah maksimum yang mungkin dari iterasi tidak lebih dari $$5$$.

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int sum(int a){
    int result=0;
    while(a>0){
        result += a%10;
        a/=10;
    }
    return result;
}
int main(){
    int a;
    cin >> a;
    while(sum(a)%4!=0){
        a++;
    }
    cout << a << endl;
}
```

**Kompleksitas waktu** : $$O(N)$$

---

## 1D. Bilangan yang Adil

Mari kita sebut sebuah nomor `super-fair` jika habis dibagi oleh masing-masing nomor $$1 \dots 9$$. Dapat dikatakan bahwa bilangan `super-fair` juga dapat dibagi oleh $$KPK(1 \dots 9)$$ yaitu sama dengan $$2520$$. Jawabannya tidak lebih besar dari bilangan `super-fair` terdekat, yang artinya Anda dapat menambah nilai dari $$n$$ oleh satu sampai menjadi `fair-numbers`. Kita dapat menentukan apakah nomor tersebut adil dengan memeriksa setiap digitnya secara terpisah.

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

bool check(long long a){
    long long tmp=a;
    while(tmp>0){
        long long res=tmp%10;
        tmp/=10;
        if((res>0)&&(a%res!=0)){
            return false;
        }
    }
    return true;
}
int main(){
    int t;
    cin >> t;
    while(t--){
        long long p;
        cin >> p;
        while(true){
            if(check(p)){
                cout << p << endl;
                break;
            }
            else{
                p++;
            }
        }
    }
}
```
**Kompleksitas waktu** : $$O(N)$$

## 1E. Roti Sobek

Karena kita akan mencari tahu kemungkinan roti yang terkontaminasi coklat, maka kita harus mengecek bagian atas, bawah, kiri, dan kanan roti yang mengandung coklat.

Dengan $$i$$ adalah baris ke dan $$j$$ adalah kolom ke :
1. $$(i-1, j)$$ adalah arah ke atas
2. $$(i, +1j)$$ adalah arah ke kanan
3. $$(i+1, j)$$ adalah arah ke bawah
4. $$(i, j-1)$$ adalah arah ke kiri

Kita sediakan array untuk menampung nilai – nilai arah tersebut.
$$\\dx[] = \{-1,0,1,0\}\\dy[] = \{0,1,0,-1\}$$

Lalu, saat kita iterasikan $$m$$ kali dan menginputkan koordinatnya, kita dapat mengiterasikan lagi setiap kali input koordinat $$a$$ dan $$b$$, pindah ke array atas, kanan, bawah, dan kiri nya dan selama dia masih ada di dalam jangkauan alias tidak keluar dari roti tersebut ``(x>=1 && x<=n && y>=1 && y<=2)`` maka kontaminasikan.

Lalu untuk hasil terakhir, iterasikan seluruh roti nya $$(n \times 2)$$ dan cek mana saja yang tidak mengandung maupun terkontaminasi coklat

**Fun Fact** : Problem tester nge-bug yang sangat memalukan sekali (salah taruh “;”)

Berikut adalah contoh kode dalam bahasa C++:


```cpp
#include <bits/stdc++.h>
using namespace std;

int n,m,dx[]={-1,0,1,0},dy[]={0,1,0,-1};

// array untuk menampung bagian yang mengandung
// atau terkontaminasi coklat

bool c[100001][3];

// fungsi untuk mengecek apakah masih ada di dalam
// jangkauan atau di dalam roti
bool inGrid(int x, int y){
    return x>=1 && x<=n && y>=1 && y<=2;
}

int main(){
    cin >> n >> m;
    for(int i=1;i<=m;i++){
        int a,b;
        cin >> a >> b;
        for(int j=0;j<=3;j++){
            int x=a+dx[j], y=b+dy[j];
            if(inGrid(x,y)){
                c[x][y]=true;
            } 
        }
        c[a][b] = true;
    }
    int count = 0;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=2;j++){
            if(!c[i][j]){
                count++;
            }
        }
    }
    cout << count << endl;
}
```
**Kompleksitas waktu** : $$O(N)$$

## 1F. Rantai Sepeda

Karena batasan pada soal tergolong kecil, kita dapat melakukan iterasi dari $$1$$ ke $$n$$, iterasi dari $$1$$ ke $$m$$, kemudian periksa bahwa $$b_i$$ habis dibagi $$a_i$$, dan cari nilai maksimalnya. Kemudian kita dapat memulai proses ini lagi dan menemukan jumlah pasangan yang merupakan nilai maksimum dari $$\frac{b_j}{a_i}$$

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    long long n,m,a[10001],b[10001];
    cin >> n;
    for(int i=1;i<=n;i++){
        cin >> a[i];
    }
    cin >> m;
    for(int j=1;j<=m;j++){
        cin >> b[i];
    }
    long long ans=0,ma=-1;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            if(b[j]%a[i]==0){
                if(b[j]>ma*a[i]){
                    ans=1;
                    ma=b[j]/a[i];
                }
                else if(b[j] == ma*a[i]){
                    ans++;
                }
            }
        }
    }
}
```
**Kompleksitas waktu** : $$O(NM)$$
