# DES

Nama : Ahmad Ihsanudin
KELOMPOK 2

Dokumentasi Program :

Implementasi DES untuk tugas Keamanan Jaringan dan Kriptografi ILKOMP UGM 2016

initTable() : Memasukan nilai - nilai indeks permutasi ke dalam array-array dan memasukkan nilai jumlah left shift sesuai left shift schedule ke dalam array. Indeks permutasi dan jumlah left shift mengacu pada standar Algoritma DES, dan berada pada file bernama file.in

inputKey() : Menerima input key 64bit biner dari user berupa string yang akan langsung di permutasi sesuai tabel permutasi PC_1 dan dipindahkan bit per bit ke sebuah array integer

buildCD() : membagi Key menjadi 2 bagian membentuk C-0, D-0 hingga C-16,D-16 dengan melakukan shift sebanyak LS[i] pada C-(i-1) untuk membentuk C-i, dan D-(i-1) untuk membentuk D-i

buildK() : membentuk K-i dengan menggabung C-i dan D-i, lalu melakukan permutasi sesuai tabel permutasi PC_2

string charToBit(char) : menerima sebuah argumen berupa char, lalu mengubahnya menjadi 8bit biner dengan nilai desimal sesuai kode ascii char tersebut, dengan keluaran 8bit biner tersebut dalam bentuk string

buildLR(string) : menerima masukkan sebuah string yang adalah potongan plainteks yang telah dikonversi menjadi 64bit biner, lalu melakukan permutasi pada plainteks sesuai tabel IP dan memasukkannya bit per bit ke dalam sebuah array of integer. Setelah itu dibagi 2 menjadi L-0 dan R-0

buildF(int) : menerima masukkan sebuah integer m, lalu akan menghasilkan F(R-(m-1), K-m). R-(m-1) di expand sesuai tabel permutasi E lalu di xor dengan K-m menghasilkan array Rexp, lalu Rexp menjadi 8 bagian. Untuk tiap bagian i masukkan ke Sbox ke - i, lalu hasilnya berupa integer val masukkan ke F dengan memanggil insertToF(i,val)

insertToF(int,int) : menerima masukkan m, dan val,mengubah val menjadi 4bit biner lalu dimasukkan ke array F mulai dari indeks ke m4 hingga m4+3

string intToHexa(int) : menerima masukkan integer val, mengubah val menjadi 2 digit hexadecimal dalam bentuk string

string bitToHexa(string) : menerima masukkan untaian biner dalam bentuk string s, lalu setiap 8bit kita ubah ke hexadecimal berupa string, tiap perubahan lalu di concate ke perubahan sebelumnya

string bitToString(string) : menerima masukkan untaian biner dalam bentuk string s, lalu setiap 8bit kita ambil nilai desimalnya yang akan kita pakai sebagai kode ascii untuk char yang akan kita concate ke string keluaran

string enc(string) : menerima masukkan plainteks berupa string s, buildLR() sesuai s. Lalu lakukan ke-16 ronde membentuk L-1,R-1 hingga L-16,R-16. setelah itu menyiapkan keluaran berupa string ret, ret adalah R-16 diconcate dengan L-16. ret kita permutasi sesuai tabel IP_1, lalu jika user sedang mengenkripsi maka fungsi enc mengeluarkan bitToHexa(ret) jika dekripsi maka mengeluarakan bitToString(ret)

string encrypt(string) : menerima masukkan plainteks berupa string s, string s dibuah menjadi dalam bentuk biner. lalu setiap 64bit biner didalamnya kita lakukan DES melalui fungsi enc(string) dengan masukkan potongan string 64bit biner tersebut. Keluaran dari enc(string) kita simpan ke string ret, dengan mengconcate , lalu setelah telah kita lakukan DES pada seluruh bit biner pada plainteks, keluarkan ret

string hexaToBit(string) : menerima sebuah hexadecimal string s, lalu diubah menjadi bilangan biner dalam bentuk string yang menjadi keluaran fungsi ini

string decrypt(string) : menerima masukkan berupa bilangan hexadesimal berupa string s, lalu kita ubah ke bentuk bilangan biner, dan kita lakukan enc() dengan masukkan tiap 64bit biner dari s

pada main terjadi initTable(), masukkan pilihan user untuk decrypt atau encrypt, inputKey(),buildCD(),buildK()

jika user memilih encrypt, maka masukkan string , jika panjang string bukan kelipatan 8 tambahkan karakter spasi ' ' ke string tersebut hingga panjangnya adalah kelipatan 8, chipertext adalah decrypt() dengan masukkan string tersebut

jika user memilih decrypt, maka masukkan string, lalu kita ubah urutan K-1 hingga ke-16 sehingga K-1 ditukar dengan K-16, K-2 dengan K-15, K-3 dengan K-14, dan seterusnya. plaintext adalah keluaran dari decrypt() dengan masukkan string tersebut

keluarkan chipertext atau plaintext

Kontribusi dalam Tim :
1. Mengikuti Presentasi
2. Membuat salah satu fungsi, yaitu: input Key(),buildCD(), buildK()

Fungsi input Key() adalah untuk menerima key/kunci yang diinputkan. yang mana diprogram ditampung divariabel inp. Lalu disini key yang
                   dimasukkan harus 64 bit, yang mana nanti akan dipindahkan untuk index dalam array int dengan melakukan for. Setelah itu key 64 bit kita permutasi dengan tabel PC_1 dan hanya menyisakan 56 bit dari key aslinya yang berjumlah 64 bit.

Fungsi buildCD()   adalah untuk mesplit/membagi key/kunci yang telah terkena permutasi oleh tabel PC_1 yang berjumlah 56 bit menjadi 2                        bagian kiri(C) dan kanan(D), dimana masing-masing memiliki 28 bit. C(dari bit ke 1-28), D(dari bit ke 29-56). hal ini                      kita buat dengan menggunakan for. Setelah itu kita gunakan for lagi untuk membuat enam belas blok Cn dan Dn, 1<=n<=16.                    Setiap pasangan blok Cn dan Dn terbentuk dari pasangan sebelumnya CN1 dan DN1,masing-masing, untuk n = 1, 2, ..., 16,                      menggunakan jadwal  dari tabel left shifts/pergeseran kiri dari blok sebelumnya. Untuk melakukan left shifts, bit                          paling kiri bergerak/berpindah ke ujung blok. Jumlah bit kiri yang berpindah itu tercantum dalam Number of left                            shiftsnya.

Fungsi buildK()    adalah untuk membuat key/kunci K dari penggabungan key C dan D. dimana pertama kali diprogram itu kita buat variabel                      int tKey yang menampung 56 bit, lalu kita buat for untuk membuat K1-K16.dengan for lagi didalamnya untuk mengisi K1-K16                    nya itu adalah bit C dan D digabungkan(K1->isi bit dari C1 dan D1). Setelah tergabung kita lakukan for lagi untuk                          dipermutasi oleh tabel PC_2 yang mana bit asli sebelum dipermutasi itu berjumlah 56 bit, menjadi hanya 48 bit.
