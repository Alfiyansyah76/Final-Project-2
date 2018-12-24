# Kamus Bahasa Indonesia
* [Deskripsi](#deskripsi)
* [Menu](#Menu)
* [kamus.h](#code)


## Deskripsi

<p>Program ini dibuat demi memenuhi tuntutan proyek akhir, pada mata kuliah pemograman lanjut. Pada kesempatan ini saya bersama rekan saya berkesempatan membuat program "Kamus Besar Bahasa Indonesia dan Latihan Soal". Sesuai dengan judulnya, konsep dari program ini adalah sebuah program yang mengimplementasikan linked list dalam bentuk kamus, jadi isi dari kamus ini diinput melalui file.bin dan user
dapat mengupdate isi kamus dengan menginput kata, definisi, dan tipe kata, melalui opsi insert pada program, dan kata yang sudah di insert akan langsung disorting secara otomatis sesuai abjad. Serta pada program kami terdapat fitur search yang ditujukan untuk mencari kata yang ingin kita mau, serta fitur latihan soal.</p>

<p>Created by:
<br>              Aqdam Zain Hajj & Muhammad Alfiyansyah 
<br>                        Teknik Komputer
<br>                     Universitas Indonesia</p>

## MENU

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Menu.JPG" alt="Menu">

### Lihat Kamus

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/List%20kata.JPG" alt="Lihat kamus">
<p> Dapat melihat keseluruhan isi kamus.</p>

<p>code</p>

```
// Create a new HTTP client with a default timeout
timeout := 1000 * time.Millisecond
client := httpclient.NewClient(httpclient.WithHTTPTimeout(timeout))

// Use the clients GET method to create and execute the request
res, err := client.Get("http://google.com", nil)
if err != nil{
	panic(err)
}

// Heimdall returns the standard *http.Response object
body, err := ioutil.ReadAll(res.Body)
fmt.Println(string(body))


### Cari

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Cari.JPG" alt="Lihat kamus">

### Masukan Kata

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Masukan.JPG" alt="Lihat kamus">

### Latihan

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/soal1.JPG" alt="Lihat kamus">
<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/soal2.JPG" alt="Lihat kamus">
<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Soal3.JPG" alt="Lihat kamus">

### Keluar



## kamus.h

