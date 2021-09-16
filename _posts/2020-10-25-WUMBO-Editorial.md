---
layout: post
title: "WEB DESIGN UNITING MEMBER BECOME ONE EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---

### Penulis Soal


| Judul Soal                      | Author          | Editorialis |
| ------------------------------- | --------------- | ----------- |
| B. Akhirnya Matwaku 100 | Ainun | Elrond |
| C. Pola Unik | Ainun | Elrond |
| D. Impostor | Elrond | Elrond |

---

## B. Akhirnya Matwaku 100

Pada problem ini kita dapat mengoutputkan tiga angka apapun yang jika dijumlahkan sama dengan $$N$$. Salah satu contohnya adalah jika $$N = 3$$, maka kondisi satu satunya yang memenuhi adalah $${1, 1, 1}$$. Jika $$N = 4$$, maka elemen elemen yang membentuk adalah $${1,1,2}$$ . Jika $$N = 100$$, maka salah satu kombinasi elemen yang mungkin adalah $${1,1,98}$$.

Sebenarnya ada banyak cara untuk menyelesaikan problem ini karena banyak kemungkinannya. Namun salah satu cara yang akan kita bahas adalah, mengoutputkan angka $$1$$ dua kali, dan $$(N-2)$$ pada posisi apapun. Dengan cara ini bisa dijamin ketiga angka tersebut membentuk $$N$$.

Jika $$N \le 2$$, bisa dipastikan tidak ada tiga elemen positif yang membentuk $$N$$.maka, outputkan `NO` jika tidak ada tiga elemen positif yang membentuk $$N$$.

Berikut contoh program dalam bahasa C++ :
 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n;
    cin >>n;
    if(n <= 2) cout << "NO" << endl;
    else{
        cout << "YES" << endl;
        cout << 1 << " " << 1 << " " << n-2 << endl;
    }
}
```

**Kompleksitas waktu** : $$O(1)$$

---

## C. Pola Unik

Pada problem ini, kita menggambar sebuah bidang kartesius dengan garis sumbu $$x$$ nya pada baris ke – $$n$$ dari bawah dan garis sumbu $$y$$ nya pada kolom ke – $$n$$ dari kiri. Dan kedua sumbu tersebut terdiri dari angka $$0$$ sampai $$9$$. Selain sumbu, kita mengoutputkan titik.

Pertama kita observasi, karena kita mengoutputkan angka $$0$$ – $$9$$ dari bawah, maka dari atas adalah kebalikannya, yaitu $$9$$ sampai $$0$$. Kita dapat mengiterasikannya dari $$9$$ mundur sampai $$0$$. Lalu yang kita perlu ketahui selanjutnya adalah, sumbu $$x$$ adalah dimana saat baris ke – $$i$$ sama dengan $$n$$, dan sumbu $$y$$ adalah dimana saat kolom ke – $$j$$ sama dengan $$n$$.

Berikut adalah contoh program dalam bahasa C++:
 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int n;
    cin >>n;
    for(int i=9;i>=0;i--){
        for(int j=0;j<=9;j++){
            if(j == n) cout << i << endl;
            else if(i == n) cout << j << endl;
            else cout << "." << endl;
        }
        cout << endl;
    }
}
```

**Kompleksitas waktu** : $$O(N^{2})$$

---

## D. Impostor

Pada problem ini, kita akan mengoutputkan bilangan yang **TIDAK** prima. Untuk mengetahui bilangan itu tidak prima, maka kita iterasi dulu dari $$2$$ sampai $$\sqrt{n}$$ , anggap saja variabel iterasi $$i$$. Jika $$N$$ habis dibagi dengan $$i$$ dan $$i \times i < n$$, maka $$N$$ bukan prima, outputkan $$N$$. Dan jangan lupa, jika $$N = 1$$, maka outputkan juga, karena $$1$$ bukanlah bilangan prima.

 
```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int t;
    cin >> t;
    if(n == 1) cout << 1 << endl;
    else{
        for(int i=2;(i*i)<=n;i++){
            if(n%i == 0) {
                cout  << n << endl;
                break;
            }
        }
    }
}
```

**Kompleksitas waktu** : $$O(N \sqrt{N})$$

#### Challenge 
dapatkah kalian mengerjakan soal ini dalam $$O(N \log N)$$?
