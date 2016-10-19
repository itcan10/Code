# DES

KELOMPOK 2

Kontribusi dalam Tim :
1. Mengikuti Presentasi
2. Membuat salah satu fungsi, yaitu: input Key(),buildCD(), buildK()

Fungsi input Key() adalah untuk menampung key/kunci yang diinputkan. yang mana diprogram ditampung divariabel inp. Lalu disini key yang
                   dimasukkan harus 64 bit, yang mana nanti akan dibuatkan index dalam int dengan melakukan for. Setelah itu key 64 bit
                   kita permutasi dengan tabel PC_1 dan hanya menyisakan 56 bit dari key aslinya yang berjumlah 64 bit.

Fungsi buildCD()   adalah untuk mesplit/membagi key/kunci yang telah terkena permutasi oleh tabel PC_1 yang berjumlah 56 bit menjadi 2                        bagian kiri(C) dan kanan(D), dimana masing-masing memiliki 28 bit. C(dari bit ke 1-28), D(dari bit ke 29-56). hal ini                      kita buat dengan menggunakan for. Setelah itu kita gunakan for lagi untuk membuat enam belas blok Cn dan Dn, 1<=n<=16.                    Setiap pasangan blok Cn dan Dn terbentuk dari pasangan sebelumnya CN1 dan DN1,masing-masing, untuk n = 1, 2, ..., 16,                      menggunakan jadwal  dari tabel left shifts/pergeseran kiri dari blok sebelumnya. Untuk melakukan left shifts, bit                          paling kiri bergerak/berpindah ke ujung blok. Jumlah bit kiri yang berpindah itu tercantum dalam Number of left                            shiftsnya.

Fungsi buildK()    adalah untuk membuat key/kunci K dari penggabungan key C dan D. dimana pertama kali diprogram itu kita buat variabel                      int tKey yang menampung 56 bit, lalu kita buat for untuk membuat K1-K16.dengan for lagi didalamnya untuk mengisi K1-K16                    nya itu adalah bit C dan D digabungkan(K1->isi bit dari C1 dan D1). Setelah tergabung kita lakukan for lagi untuk                          dipermutasi oleh tabel PC_2 yang mana bit asli sebelum dipermutasi itu berjumlah 56 bit, menjadi hanya 48 bit.
