---
layout: post
title: "WEB DESIGN MOCK CONTEST 2020 EDITORIAL"
categories : Programming 
tags: ["wd-contest","programming"]
katex: yes
published: yes
---
# WEB DESIGN MOCK CONTEST 2020 EDITORIAL

### Penulis Soal

| Judul Soal                  | Author | Editorialis    |
| --------------------------- | ------ | -------------- |
| A. Klembu dan Jagung        | Elrond | Ainun          |
| B. Klembu dan Saham         | Elrond | Ainun          |
| C. Klembu dan Maze          | Ainun  | Ainun          |
| D. Klembu dan Loka          | Ainun  | Ainun          |
| E. Klembu dan Ratu          | Elrond | Elrond + Ainun |
| F. Klembu dan Pesan Rahasia | Ainun  | Elrond + Ainun |

---

## A. Klembu dan Jagung

Klembu mengidam jagung pada tanggal ganjil, dan merasa sebal dengan penjual jagung jika tanggalnya genap. Sehingga Shiro harus membelikan Klembu jagung hanya pada tanggal ganjil saja. Terdapat dua cara dalam menyelesaikan soal ini:

### Cara 1 : Menggunakan **operator modulo** (`mod, %, dll`) dan **percabangan if**

Perhatikan bahwa **bilangan ganjil** adalah bilangan yang jika dibagi dua menghasilkan **sisa 1**, sedangkan **bilangan genap** adalah bilangan yang jika dibagi dua menghasilkan **sisa  0**. Gunakan operator modulo dan percabangan untuk mengecek **bilangan ganjil** ($$\mod 2 = 1$$ ) atau **bilangan genap** ($$\mod 2 = 0$$).

Berikut adalah contoh kode dalam bahasa *python*:

```python
n = int(input())
if n % 2 != 0:
    print("Beli bang")
else:
    print("Beli besok aja")
```

Berikut adalah contoh kode dalam bahasa *C++*:

```cpp
#include <iostream> //untuk mengakses input-output
using namespace std;
int main(){
 	long long int s;
	cin >> s; //untuk membaca input
	if(s%2 == 1) 
		cout << "Beli bang\n";
	else 
		cout << "Beli besok aja\n";
	return 0;
}
```

#### Catatan:

* Operator modulo pada setiap bahasa berbeda beda, ada yang menggunakan `%` seperti *python* dan *C++*, ada juga yang menggunakan `mod` seperti *pascal*.

### Cara 2: Menggunakan **operasi string**

Ambil input sebagai sebuah string, lalu perhatikan karakter terakhir dari string tersebut. Jika karakter terakhirnya adalah `1`, `3`, `5`, `7` `9` maka Shiro akan membelikan Klembu jagung. Selain itu, klembu tidak akan membelikan Klembu jagung.
	
Berikut adalah contoh kode dalam bahasa *Python*:

```python
s = str(input())
if int(s[-1])% 2 == 0:
	print("Beli besok aja")
else:
	print("Beli bang")
```

Berikut adalah contoh kode dalam bahasa *C++*:

```cpp
#include <iostream> //untuk mengakses input-output
#include <string> //untuk mengakses operasi pada string
using namespace std;
int main(){
	string s;
	cin >> s; //untuk membaca input
	if(s[s.length()-1]=='1' || s[s.length()-1]=='3' || 
	   s[s.length()-1]=='5' || s[s.length()-1]=='7' || 
	   s[s.length()-1]=='9')
		cout << "Beli bang\n";
	else
		cout << "Beli besok aja\n";
	return 0;
}
```

#### Catatan:

* `s.length()` untuk menghitung panjang dari string `s`
* Operator `or` dalam bahasa *C++* dinyatakan dengan `||`

**Kompleksitas waktu :** $$O(1)$$

---

## B. Klembu dan Saham

Soal ini dapat diselesaikan menggunakan rumus suku ke-n dari deret geometri.

$$U_n=a \times {r}^{n-1}$$

Perhatikan bahwa setiap satu dollar uang milik Klembu akan menghasilkan satu dollar lainnya. Misalkan Klembu memiliki uang sebesar $$1$$ dollar, maka uang Klembu selanjutnya akan menjadi $$1 + 1 = 2$$ dollar, selanjutnya menjadi $$2 + 2 = 4$$ dollar, selanjutnya menjadi $$4+4 = 8$$ dollar, dan seterusnya.

Ini berarti jika Klembu memiliki $$N$$ dollar, maka di hari berikutnya ia akan memiliki $$2N$$ dollar. Maka **rasio dari deret ini adalah $$2$$**, dengan suku pertama adalah $$N$$ dan banyaknya suku dari deret ini adalah $$M$$, sehingga penyelesaian dari soal ini adalah

$$U_M=N \times {r}^{M-1}$$

Berikut adalah contoh kode dalam bahasa *python* : 

```python
n,m = map(int, input().split()) #untuk membaca input
rasio = 2
MOD = 1000000007
total = n * (rasio ** (m-1)) % MOD
print(total)
```

**Kompleksitas waktu**: $$O(1)$$

Berikut adalah contoh kode dalam bahasa C++ menggunakan *fast exponential* :

```cpp
#include <iostream> // untuk mengakses input-output
#include <cmath> // untuk mengakses operasi matematika
#define MOD 1000000007
using namespace std;
typedef long long int lll;
lll f(int x,int y){
    if(y==1) return x;
    else {
		lll temp=f(x,y/2);
		if(y%2==0) 
			return ((temp%MOD)*(temp%MOD))%MOD;
		else 
			return ((x*((temp%MOD)*(temp%MOD)))%MOD);
    }
}
int main(){
    int n,m;
    cin >> n >> m;
    cout << ((f(2,m-1) % MOD)*(n%MOD))%MOD<<"\n";
    return 0;
}
```

**Kompleksitas waktu** : $$O(log M)$$

Berikut adalah contoh kode dalam bahasa C++ menggunakan `for-loop`:

```cpp
#include <iostream> // untuk mengakses input-output
#include <cmath> // untuk mengakses operasi matematika
#define MOD 1000000007
using namespace std;
int main(){
    long long int n,m;
    cin >> n >> m;
    for(int i=1; i<m; i++){
        n *= 2;
        n %= MOD;
    }
    cout << n <<"\n";
    return 0;
}
```

**Kompleksitas waktu** : $$O(M)$$

#### Catatan:

* Karena terdapat overflow ketika kita menggunakan `pow(2,m-1)`, maka kita bisa menggunakan `for-loop` atau *fast exponential* seperti code diatas.


---

## C. Klembu dan Maze

Asumsikan bahwa kita sedang berada di sebuah petak, maka hanya ada satu cara dari luar petak menuju petak ($$1,1$$) seperti yang ditunjukkan pada gambar : 

<div align="center">
    <img src="https://i.imgur.com/tnKte86.png" alt="maze1"/>
</div>

Angka yang berwarna kuning merupakan indeks dari masing masing petak.

Perhatikan baris pertama dari petak tersebut. Jika kita ingin pergi ke sembarang petak pada baris pertama, sebut saja ($$1,k$$) dengan $$1 < k \le m$$, maka hanya ada satu cara untuk pergike petak ($$1,k$$) dari petak ($$1,1$$). Hal yang sama juga terjadi jika kita ingin pergi ke sembarang petak pada kolom pertama, maka hanya ada satu cara untuk pergi ke petak ($$1,k$$) dengan $$1 < k \le n$$ dari petak ($$1,1$$) seperti yang ditunjukkan pada gambar :

<div align="center">
    <img src="https://i.imgur.com/3jNXDyw.png" alt="maze2"/>
</div>


Perhatikan bahwa untuk setiap petak ($$x,y$$), ada dua jalan untuk menujunya, yaitu dari petak kirinya ($$x,y-1$$) atau dari petak atasnya ($$x-1,y$$). Karena hanya bisa bergerak ke kanan atau bawah, maka dari petak ($$x,y-1$$) kita tidak bisa bergerak ke petak ($$x-1,y$$) begitu pula sebaliknya sehingga kedua kasus tersebut saling lepas.

Misalkan array dua dimensi $$path[x][y]$$ adalah array yang menampung banyaknya cara menuju petak ($$x,y$$) jika awalnya kita berada pada petak ($$1,1$$). Maka, secara matematis penjelasan pada paragraph dapat ditulis menjadi:
$$path[x][y] = path[x][y-1] + path[x-1][y]$$

Berikut adalah ilustrasi dari rumus tersebut:

<div align="center">
    <img src="https://i.imgur.com/uAMp4Ag.png" alt="maze-final"/>
</div>

Jawaban akhirnya ada di $$path[n][m]$$.

Berikut adalah contoh kode dalam bahasa *python* :

```python
n,m = map(int,input().split())
MOD = 1000000007
path = [0]*(n+1)

for i in range(n+1):
	path[i] = [0]*(m+1)
	path[i][1] = 1
	
for i in range(m+1):
	path[1][i] = 1
	
for i in range (2, n+1):
	for j in range(2, m+1):
		path[i][j] = (path[i-1][j] + path[i][j-1]) % MOD
		
print(path[n][m])
```

Berikut adalah contoh kode dalam bahasa *C++*:

```cpp
#include <iostream> //untuk mengakses input-output
using namespace std;
int main(){
	int n,m;
	cin >> n >> m;
	
	long long path[n+1][m+1], MOD = 1000000007;
	
	for(int i=1; i<=n; i++) //kolom pertama
		path[i][1] = 1;
	
	for(int i=1; i<=m; i++) //baris pertama
		path[1][i] = 1;
	
	for(int i=2; i<=n; i++)
		for(int j=2; j<=m; j++)
			path[i][j] = (path[i-1][j] + path[i][j-1])%MOD;

	cout << path[n][m] << "\n";
	return 0;
}
```

#### Catatan:

* Operator modulo pada setiap bahasa berbeda beda, ada yang menggunakan `%` seperti *python* dan *C++*, ada juga yang menggunakan `mod` seperti *pascal*.

**Kompleksitas waktu :** $$O(NM)$$

---

## D. Klembu dan Loka

Soal ini dapat diselesaikan menggunakan `for-loop`. Untuk mempermudah pemahaman, misalkan karakter spasi diganti dengan karakter `#`. Maka output menjadi :

<div align="center">
    <img src="https://i.imgur.com/QeazY8s.png" alt="ilus-diam1"/>
</div>

Untuk mempermudah pengerjaan, mari selesaikan separuh dari pola terlebih dahulu. Yaitu:

<div align="center">
    <img src="https://i.imgur.com/ygSm5bF.png" alt="ilus-diam2"/>
</div>

Perhatikan bahwa untuk $$n = 4$$, jumlah karakter `#` pada baris pertama $$3$$, lalu berkurang $$1$$ pada setiap barisnya dan jumlah karakter `*` pada baris ke-$$i$$ menunjukkan bilangan ganjil ke-$$i$$ pertama. Tabel dibawah ini dapat mempermudah Anda dalam memvisualisasi.

| Baris | Jumlah `#` | Jumlah `*` |
| ----- | ---------- | ---------- |
| 1     | 3          | 1          |
| 2     | 2          | 3          |
| 3     | 1          | 5          |
| 4     | 0          | 7          |

Ini berarti, untuk mencetak mencetak n baris, dapat menggunakan `for` menaik dari $$1$$ sampai $$n$$. Pada setiap barisnya, untuk mencetak karakter `#` dapat menggunakan `for` menaik dari $$1$$ sampai $$n-i$$, untuk mencetak karakter `*` dapat menggunakan for menaik dari $$1$$ sampai  $$(2 \times i)-1$$.

Untuk pola yang selanjutnya, yaitu separuh terakhirnya.

<div align="center">
    <img src="https://i.imgur.com/oEeTZmk.png"/>
</div>


Perhatikan bahwa untuk $$n = 4$$, jumlah karakter `#` pada baris pertama $$1$$, lalu bertambah $$1$$ pada setiap barisnya dan jumlah karakter `*` pada baris ke-$$i$$ menunjukkan bilangan ganjil ke-$$n-i$$ pertama. Tabel dibawah ini dapat mempermudah Anda dalam memvisualisasi.

| Baris | Jumlah `#` | Jumlah `*` |
| ----- | ---------- | ---------- |
| 1     | 3          | 5          |
| 2     | 2          | 3          |
| 3     | 1          | 1          |

Ini berarti, untuk mencetak mencetak $$n$$ baris, dapat menggunakan `for` menurun dari $$n-1$$ sampai $$1$$. Pada setiap barisnya, untuk mencetak karakter `#` dapat menggunakan `for` menaik dari $$1$$ sampai $$n-i$$, untuk mencetak karakter `*` dapat menggunakan for menaik dari $$1$$ sampai $$(2 \times i)-1$$.

Berikut adalah contoh kode dalam bahasa *python* :

```python
n = int(input()) #untuk membaca input
for i in range(1,n+1,1):
	for j in range (n-i):
		print(" ",end='')
	for j in range ((2*i)-1):
		print("*",end='')
	print("")
for i in range (n-1,0,-1):
	for j in range (n-i):
		print(" ",end='')
	for j in range ((2*i)-1):
		print("*",end='')
	print("")
```

Berikut adalah contoh kode dalam bahasa `C++`:

```cpp
#include <iostream> //untuk mengakses input-output
using namespace std;
int main(){
	int n;
	cin >> n;
	for(int i=1; i<=n; i++){
		for(int j=1; j<= n - i; j++) 
			cout << " ";
		for(int j=1; j<=(2*i) - 1; j++) 
			cout << "*";
		cout << "\n";
	}
	for(int i=n - 1; i>=1; i--){
		for(int j=1; j<= n - i; j++) 
			cout << " ";
		for(int j=1; j<=(2*i) - 1; j++) 
			cout << "*";
		cout << "\n";
	}
	return 0;
}
```

**Kompleksitas waktu :** $$O({N}^{2})$$

---

## E. Klembu dan Ratu

Soal ini dapat diselesaikan dengan **melihat pola dan dengan bantuan *greedy***. Inti dari soal ini adalah meletakkan ratu sebanyak banyaknya pada papan berukuran $$n \times n$$. Misalkan kita meletakkan ratu pertama pada pojok kiri bawah dari papan tersebut, maka ratu selanjutnya diletakkan pada petak yang paling dekat dengan ratu pertama tetapi tidak sampai melanggar peraturan agar mendapat hasil paling maksimal dan membentuk pola.

Setelah pola di observasi, terbentuklah pola yang dimaksud. Ada 3 basecase di problem ini, yaitu $$f(1) = 1$$; $$f(2) =1$$; $$f(3) = 2$$; $$f(4) = 4$$. Lalu pola nya berlaku mulai $$n \le 5$$. 

**Jika $$n$$ adalah bilangan ganjil**, maka **keluarannya adalah $$n$$**, **jika $$n$$ adalah bilangan genap**, maka **keluarannya adalah $$n-1$$**. Bisa dilihat di papan $$5 \times 5$$ berikut ini:

<div align="center">
    <img src="https://i.imgur.com/fcAxMu7.jpg"/>
</div>

Pada papan $$5 \times 5$$, karena $$5$$ adalah bilangan **ganjil**, maka keluarannya adalah $$n$$, yaitu $$5$$.

<div align="center">
    <img src="https://i.imgur.com/8vurMn4.png"/>
</div>

Pada papan $$6 \times 6$$, karena $$6$$ adalah bilangan **genap**, maka keluarannya adalah $$n-1$$, yaitu $$5$$.

Berikut contoh kode dalam bahasa *python* :

```python
n = int(input())
if n == 1 or n == 2:
    print(1)
elif n == 3:
    print(2)
elif n == 4:
    print(4)
elif n >= 5:
    if n % 2 == 0:
        print(n-1)
    else:
        print(n)
```

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <iostream>
using namespace std;
int main(){
    long long n; // 10^8 lebih aman menggunakan long long
    cin >> n;
    if(n == 1 || n == 2) cout << "1\n";
    else if(n == 3) cout << "2\n";
    else if(n == 4) cout << "4\n";
    else {
        if( n % 2 == 1) cout << n << "\n";
        else cout << n-1 << "\n";
    }
return 0;
}
```

**Kompleksitas waktu** : $$O(1)$$

---

## F. Klembu dan Pesan Rahasia

Pesan yang diberikan Shiro kepada Klembu memiliki pola. Misalkan `string ans` adalah string yang menyimpan hasil dari pola tersebut, misalkan juga `int index=0` adalah index pada masukan dengan nilai inisialisasi $$0$$ dan misalkan `int dif = 1` adalah selisih index pada masukan dengan nilai inisialisasi $$1$$.

Polanya adalah karakter yang diambil untuk keluaran adalah karakter yang berasal dari inputan, dipilih dengan jarak (index) yang semakin meningkat. Selama nilai index $$\le$$ panjang dari string masukan, tambahkan `string ans` dengan karakter ke-`index` dari string masukan. Lalu tambahkan nilai `index` dengan `dif` dan kemudian tambahkan nilai `dif` dengan $$1$$. Lakukan hal ini berulang kali hingga nilai index $$>$$ panjang dari string masukan.

Pada contoh masukan : `haplokozm`. Panjang string nya 9. Visualisasi ada pada tabel.
<div align="center">
    <img src="https://i.imgur.com/tBpTIo0.png"/>
</div>

Maka output dari input tersebut adalah ‘halo’ tanpa tanda petik yang diambil dari '**ha**p**l**ok**o**zm'
Berikut adalah contoh kode dalam bahasa *python* :

```python
pesan = str(input())
ans = ""
ind = 0
panjang = len(pesan)
inc = 1
while ind < panjang:
    ans += pesan[ind]
    ind += inc
    inc +=1
print(ans)
```

Berikut adalah contoh kode dalam bahasa C++:

```cpp
#include <bits/stdc++.h> //semua library tersedia disini
using namespace std;
int main(){
    string s="";
    string pesan,jawaban="";
    cin>>pesan;
    int panjang=pesan.length(),index=0,increment=1;
    while(index<panjang){
        jawaban+=pesan[index];
        index+=increment;
        increment++;
    }
    cout<<jawaban<<"\n";
}
```

**Kompleksitas waktu:** $$O(N)$$
