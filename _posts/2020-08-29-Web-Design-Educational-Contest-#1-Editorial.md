---
layout: post
title: "WEB DESIGN EDUCATIONAL CONTEST #1 EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---
### Penulis Soal

| Judul Soal                  | Author | Editorialis    |
| --------------------------- | ------ | -------------- |
| B. Ketuhanan yang Maha Esa  | QWludW4g | QWludW4g          |
| C. Kemanusiaan yang Adil dan Beradab          | QWludW4g  | QWludW4g          |
| D. Persatuan Indonesia         | Elrond  | Elrond + QWludW4g          |
| E. Sila Keempat      | Elrond | Elrond |
| F. Keadilan Sosial | Elrond  | Elrond |
| G. Penyimpangan Pancasila | Kenanya | Elrond

---
## B. Ketuhanan yang Maha Esa
Misalkan setiap kucing mendapatkan $$B$$ buah kaleng dan total kaleng yang dimiliki Budi sebanyak $$A$$ kaleng. Maka banyaknya kaleng yang dimiliki oleh Budi adalah banyaknya kucing yang disantuni Budi, yaitu $$N$$, dikali dengan $$B$$, lalu ditambah dengan sisa kaleng yang dimiliki Budi, yaitu $$P$$. Secara matematis dapat ditulis:

$$A = (B \times N) + P$$

Lalu beberapa operasi sehingga diperoleh nilai dari $$B$$

$$B \times N = A - P$$ $$B = \frac{A - P}{N}$$

Perhatikan bahwa setiap kucing mendapatkan jumlah yang sama. Maka jawaban dari soal ini adalah kita hanya perlu mengecek di setiap pertanyaan apakah $$A – P$$ habis dibagi oleh $$N$$. Jika $$A – P$$ habis dibagi oleh $$N$$, keluarkan ``“kamu tau dari mana?”``, jika tidak, keluarkan ``“sok tau kamu”`` tanpa tanda petik. Untuk mengecek apakah $$A – P$$ habis dibagi $$N$$, kita dapat menggunakan operator modulo dan percabangan.

Berikut adalah contoh *code* dalam bahasa C++:

```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int a,b,q,c;
    cin>>a>>b>>q;
    while(q--){
        cin>>c;
        if((c-a)%b==0) cout<<"kamu dikasih tau siapa?\n";
        else cout<<"sok tau kamu\n";
    }
    return 0;
}
```
**Kompleksitas waktu** : $$O(Q)$$

---

## C. Kemanusiaan yang Adil dan Beradab

Soal tersebut merupakan deret aritmatika dengan beda (b) $$1$$ dan suku pertamanya (a) $$1$$. Untuk mencari jumlah dari suku ke-$$K$$ dari soal tersebut, kita dapat menggunakan rumus
deret aritmatika.

$$S_n = \frac{n}{2} \times [2a + (n-1)b]$$

Masukkan angka yang diketahui, yaitu $$a$$ dan $$b$$. Maka : 

$$S_n = \frac{n}{2} \times [2 \times 1 + (n-1)1]$$ 

$$S_n = \frac{n}{2} \times [2 + n - 1]$$ 

$$S_n = \frac{n}{2} \times [n + 1]$$

Sehingga jawaban dari soal ini adalah

$$S_n = \frac{n}{2} \times [n + 1]$$

Berikut adalah contoh kode dalam bahasa C++:

```cpp
//solution - kemanusiaan yang adil dan beradab
#include <bits/stdc++.h>
using namespace std;

int main(){
	long long n;
	cin>>n;
	cout<<n*(n+1)/2<<endl;
	return 0;
}
```
**Kompleksitas waktu** : $$O(1)$$

---

## D. Persatuan Indonesia

Perhatikan bahwa kemanapun Budi berkunjung, dari koordinat negatif ke negatif, negatif ke positif, maupun positif ke positif, jarak yang ditempuh Budi akan **selalu positif**, karena jarak tidak bisa berupa nilai negatif.

Soal ini tidak beda jauh dengan soal jarak manhattan, hanya saja setiap jarak yang ditempuh Budi, Budi harus mengeluarkan biaya sebesar $$N$$ rupiah. Maka soal ini dapat diselesaikan secara matematis :

$$(\left\lvert A-C\right\rvert + \left\lvert B-D\right\rvert) \times N$$

Dengan $$(\left\lvert A-C\right\rvert)$$ menyatakan nilai mutlak dari $$A - C$$ dan $$(\left\lvert B-D\right\rvert)$$ menyatakan nilai mutlak $$B – D$$. Jika keduanya ditambah, menghasilkan jarak yang ditempuh Budi. Lalu Budi mengeluarkan $$jarak \times N$$ rupiah. Terdapat dua cara dalam menyelesaikan soal ini

- Menggunakan fungsi `abs`
Pemanggilan `abs(a)` mengembalikan nilai mutlak dari $$a$$, sebagai contoh `abs(1)` akan mengembalikan $$1$$ sedangkan `abs(-8)` akan mengembalikan $$8$$.
Berikut adalah contoh program menggunakan bahasa C++:

```cpp
#include <bits\stdc++.h>
using namespace std;

int main(){
    int a,b,c,d,n;
    long long jarak, harga;
    cin >> a >> b >> c >> d >> n;
    jarak = abs(a-c) + (d-b)
    harga = n * jarak;
    cout << harga << endl;
}
```

- Menggunakan **percabangan** `if`
Solusi lain adalah menggunakan percabangan. Salah cara untuk merubah bilangan negatif menjadi bilangan positif adalah mengalikan bilangan tersebut dengan `-1`.

Pertama kita menyimpan nilai jarak pada sumbu `x (A dan C)` pada suatu variabel, misal `hasil1`, lalu kita menyimpan nilai jarak pada sumbu `y (B dan D)` pada suatu variabel, misal `hasil2`. Lalu kita mengecek, apakah hasil1 dan hasil2 merupakan bilangan negatif, **jika negatif, maka kalikan dengan -1**.

Contoh programnya dalam bahasa C++ sebagai berikut :
```cpp
#include <bits\stdc++.h>
using namespace std;

int main(){
    long long a,b,c,d,n,hasil1,hasil2;
    hasil1 = a - c;
    hasil2 = b - d;
    if(hasil1 < 0) hasil1 *= -1;
    if(hasil2 < 0) hasil2 *= -1;
    cout << n * (hasil1 + hasil2) << endl;
}
```
**Kompleksitas waktu** : $$O(1)$$

---

## E. Sila Keempat
Perhatikan bahwa Budi menjadi ketua kelas **Jika dan hanya jika setengah dari jumlah siswa menyatakan “SETUJU”**. Jika tidak, maka anak lain menjadi ketua kelas. Kita dapat menampung jumlah suara saat ada yang menyatakan setuju. Misal kita mempunyai variabel `vote`. Kita inisiasikan nilai awal $$0$$ pada variabel `vote` ini. Lalu setiap kali ada input yang berupa “SETUJU”, maka nilai vote bertambah satu.

#include <bits\stdc++.h>
using namespace std;

```cpp
int main(){
    int n, vote=0;
    string s;
    cin >> n;
    for(int i=0;i<n;i++){
        cin >> s;
        if(s == "SETUJU") vote++;
    }
    if(2 * vote >= n) cout << "Budi adalah ketua kelas" << endl;
    else cout << "Pilih anak lain" << endl;
}
```

**Kompleksitas waktu** : $$O(N)$$

Perhatikan bahwa pada program diatas, kita menggunakan `if (2 * vote >= n)` dan tidak menggunakan `if (vote >= n / 2)`, karena pada C++, operasi `(/)` adalah operasi `div`, yaitu pembulatan kebawah. Jika $$n = 3$$, maka $$3 / 2 = 1$$, padahal $$1$$ bukan setengah dari $$3$$. Ini berlaku untuk semua bilangan ganjil. Maka kita dapat mengatasinya dengan `if (2 * vote >= n)`.

---

## F. Keadilan Sosial

Tujuan dari soal ini adalah membandingkan dua variabel $$A$$ dan $$B$$. Jika $$A$$ lebih besar dari $$B$$, maka keluarkan ``“Ani”`` tanpa tanda petik. Jika $$B$$ lebih besar dari $$A$$, maka keluarkan ``“Budi”`` tanpa tanda petik. Jika $$A$$ dan $$B$$ bernilai sama, maka keluarkan ``“Seri”`` tanpa tanda petik. Soal ini dapat diselesaikan menggunakan percabangan. Berikut program dalam bahasa C++ :

```cpp
#include <bits\stdc++.h>
using namespace std;

int main(){
    int a,b;
    cin >> a >> b;
    if(a > b) cout << "Ani" << endl;
    else if(a == b) << "Seri" << endl;
    else cout << "Budi" << endl;
}
```

**Kompleksitas waktu** : $$O(1)$$

---

## G. Penyimpangan Pancasila

Klembu memiliki kata ``“panca”`` dengan setiap karakter dalam
kata tersebut mempunyai indeks dari $$1$$ sampai $$5$$. Seperti pada tabel di bawah, karakter `p` mempunyai indeks $$1$$, `a` mempunyai indeks $$2$$, `n` mempunyai indeks $$3$$, `c` mempunyai indeks $$4$$, `a` mempunyai indeks $$5$$

| 1 | 2 | 3 | 4 | 5 |
| --|---| --| --| --|
| p | a | n | c | a |

Maksud dari soal ini adalah mengeluarkan kata ``“panca”`` namun dengan karakter indeks ke total, diubah menjadi karakter uppercase (kapital). **Anggap variabel `total` adalah total dari kode – kode rahasia Klembu yang sudah di modulo $$5$$**.

* Note : modulo adalah hasil sisa dari operasi pembagian

Karena Klembu mempunyai 5 karakter dalam kata ``“panca”``, dan kita bisa merubah salah satu dari lima karakter tersebut, maka kita bisa membagi persoalan ini menjadi 5 kasus.

1. **Kasus 1** : saat ``total = 1``, maka keluarkan ``“Panca”`` tanpa tanda petik.
2. **Kasus 2** : saat ``total = 2``, maka keluarkan ``“pAnca”`` tanpa tanda petik.
3. **Kasus 3** : saat ``total = 3``, maka keluarkan ``“paNca”`` tanpa tanda petik.
4. **Kasus 4** : saat ``total = 4``, maka keluarkan ``“panCa”`` tanpa tanda petik.
5. **Kasus 5** : saat ``total = 0``, maka keluarkan ``“pancA”`` tanpa tanda petik.

Maka dalam program dapat dituliskan sebagai : 

```cpp
#include <bits\stdc++.h>
using namespace std;

int main(){
    unsigned long long int n,m,total;
    cin >> n;
    for(int i=0;i<n;i++){
        cin >> m;
        total = total + m;
        total = total % 5;
    }
    if(total == 1) cout << "Panca" << endl;
    else if(total == 2) cout << "pAnca" << endl;
    else if(total == 3) cout << "paNca" << endl;
    else if(total == 4) cout << "pAnca" << endl;
    else if(total == 5) cout << "paNca" << endl;
}
```

Perhatikan juga, kita mengambil input sebanyak $$N$$ kali, maka kita dapat menggunakan perulangan untuk mengambil inputnya.

Kita juga bisa menggunakan percabangan `case`. Dapat kita implementasikan dalam program sebagai berikut : 

```cpp
#include <bits\stdc++.h>
using namespace std;

int main(){
    unsigned long long int n,m,total;
    cin >> n;
    for(int i=0;i<n;i++){
        cin >> m;
        total = total + m;
        total = total % 5;
    }
    switch(total){
        case 0 :
            cout << "pancA" << endl;
            break;
        case 1 :
            cout << "Panca" << endl;
            break;
        case 2 :
            cout << "pAnca" << endl;
            break;
        case 3 :
            cout << "paNca" << endl;
            break;
        case 4 :
            cout << "panCa" <<endl;
            break;
    }
}
```

**Kompleksitas waktu** : $$O(N)$$
