---
layout: post
title: "WEB DESIGN EDUCATIONAL CONTEST #5 EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---

### Penulis Soal

| Soal | Judul Soal                     | Author | Editorialis |
| ---- | ------------------------------ | ------ | :---------- |
| B    | Transpos Matriks A + Matriks A | Atha   | Atha        |
| C    | Selisih Umur                   | Aydin  | Aydin       |
| D    | Aturan Umur                    | Elrond | Elrond      |
| E    | Asisten Guru                   | Elrond | Elrond      |
| F    | Deadliner Sejati               | Elrond | Elrond      |
| G    | Vending Machine Aneh           | Elrond | Elrond      |


## B. Transpos Matriks A + Matriks A

Tujuan dari soal ini untuk mengetahui hasil penjumlahan transpos dari matriks A + matriks A

Misalkan matriks A adalah 
$$
\begin{bmatrix}
a & b & c\\
d & e & f\\
g & h & i\\
\end{bmatrix}
$$

Maka transpos dari matriks A adalah
$$
\begin{bmatrix}
a & d & g\\
b & e & h\\
c & f & i\\
\end{bmatrix}
$$

Sehingga hasil penjumlahannya adalah

$$
\begin{bmatrix}
a & b & c\\
d & e & f\\
g & h & i
\end{bmatrix} +
\begin{bmatrix}
a & d & g\\
b & e & h\\
c & f & i
\end{bmatrix} = \begin{bmatrix}
2a & b+d & c+g\\
d+b & 2e & f+h\\
g+c & h+f & 2i\\
\end{bmatrix}
$$

Berikut program dalam bahasa C++ :
```cpp
#include <bits/stdc++.h>
 
using namespace std;
 
int main()
{
    int a,b,c,d,e,f,g,h,i;
    cin >> a >> b >> c;
    cin >> d >> e >> f;
    cin >> g >> h >> i;
    cout << a+a << " " << b+d << " " << g+c << endl;
    cout << d+b << " " << e+e << " " << f+h << endl;
    cout << g+c << " " << h+f << " " << i+i << endl;
}
```

**Kompleksitas Waktu** : $$O(1)$$

---

## C. Selisih Umur

Tujuan dari soal ini untuk mengetahui selisih umur antara Agos dan Budi. Misalkan selisih umur Agos dan Budi adalah $$X$$, maka :
- Jika umur Agos lebih besar dari Budi maka keluarkan `agos X tahun lebih tua dari budi`. 
- Jika umur Budi lebih besar dari Agos maka keluarkan `budi X tahun lebih tua dari agos`. 

Soal ini dapat diselesaikan menggunakan percabangan. Berikut program dalam bahasa C++ : 

```cpp
#include <iostream>
using namespace std;
int main(){
 int agos,budi;
 cin>>agos>>budi;
 if(agos>budi){
  cout<<"agos "<<agos-budi<<" tahun lebih tua dari budi"<<endl;
 }
 else{
  cout<<"budi "<<budi-agos<<" tahun lebih tua dari agos"<<endl;
  
 }
}
```

**Kompleksitas Waktu** : $$O(1)$$

---
## D. Aturan Umur
Untuk permasalahan ini, kita hanya mengimplementasikan pernyataan-pernyataan yang ada di soal dengan percabangan. 

* Jika ```s == “anak-anak”``` maka berapapun umurnya pasti jawabannya boleh. 
* Jika ```s == “remaja”```, cek apakah $$N >= 13$$, jika iya outputkan boleh, jika tidak outputkan tidak boleh. 
* Jika ```s == “dewasa”```, cek apakah $$N >= 18$$, jika iya outputkan boleh, jika tidak outputkan tidak boleh. 
* Jika ```s == “dewasa-plus”```, cek apakah $$N >= 21$$, jika iya outputkan boleh, jika tidak outputkan tidak boleh.

Berikut program dalam bahasa C++ : 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n;
    string s;
    cin >> n >> s;
    if(s == "anak-anak") {
        cout << "boleh"<<endl;
    } else if(s=="remaja"){
        if(n>=13) cout << "boleh" << endl;
        else cout << "tidak boleh" << endl;
    }
    else if(s=="dewasa"){
        if(n>=18) cout << "boleh" << endl;
        else cout << "tidak boleh" << endl;
    }
    else if(s=="dewasa-plus"){
        if(n>=21) cout << "boleh" << endl;
        else cout << "tidak boleh" << endl;
    }
}
```

**Kompleksitas Waktu** : $$O(1)$$

---

## E. Asisten Guru
Pada problem ini, kita menyediakan suatu variabel untuk menentukan ada berapa banyak soal yang dijawab benar. Kita anggap variabel tersebut benama `benar` dan kita inisiasikan nilai $$0$$. Lalu kita mengambil inputan $$X$$ dan $$Y$$ sebagai tipe data `char` atau `string` sebanyak $$N$$ kali, sekaligus membandingkan apakah `X == Y`. Jika iya, maka tambahkan $$1$$ pada variabel `benar`.

Berikut program dalam bahasa C++ : 

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n,benar=0;
    char x,y;
    cin >> n;
    for(int i=1;i<=n;i++) {
    	cin >> x >> y;
    	if(x == y) benar++;
    }
    cout << benar << endl;
}
```

**Kompleksitas Waktu** : $$O(N)$$

---

## F. Deadliner Sejati
Untuk permasalahan ini, kita menyediakan sebuah variabel untuk menyimpan nilai hasil dari semua penjumlahan $$A_i$$. Anggap kita menggunakan variabe `sum` dan menginisiasikannya nilai $$0$$. Setiap kita mengambil input $$A_i$$, kita menambahkan $$A_i$$ pada `sum`. Hal ini dilakukan untuk menghitung keseluruhan waktu yang dibutuhkan untuk mengerjakan semua tugas yang ada. Langkah terakhirnya adalah mengecek apakah `sum >= m`. Jika iya, keluarkan tidak. Jika tidak keluarkan bisa.

Berikut program dalam bahasa C++ : 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n,m,a,sum=0;
    cin >> n >> m;
    for(int i=1;i<=n;i++){
        cin >> a;
        sum += a;  
    } 
    if(sum >= m) cout << "tidak" << endl;
    else cout << "bisa" << endl;
}
```
**Kompleksitas Waktu** : $$O(N)$$

---

## G. Vending Machine Aneh

Untuk permasalahan ini, kita hanya perlu mengecek apakah $$N$$ habis dibagi dengan $$5000$$. Jika $$N$$ habis dibagi dengan $$5000$$, artinya kita dapat membeli minuman tersebut dengan uang pas, maka kita bisa mengoutputkan $$N$$ langsung. Jika $$N$$ tidak habis dibagi dengan $$5000$$, maka kita tambahkan terus $$N$$ dengan $$1000$$ sampai $$N$$ dapat dibagi dengan $$5000$$. Kita menambahkan $$1000$$ karena $$N$$ merupakan kelipatan $$1000$$.


Kita dapat menggunakan perulangan `while` untuk menyelesaikan permasalahan ini.  Dapat diketahui pada kasus terburuk, program hanya mengulangi $$4$$ kali. 

Berikut program dalam bahasa C++ : 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n;
    cin >> n;
    while(n % 5000 != 0){
        n += 1000;
    }
    cout << n << endl;
}
```

**Kompleksitas Waktu** : $$O(1)$$

**Challenge** : selesaikan soal ini tanpa menggunakan looping
