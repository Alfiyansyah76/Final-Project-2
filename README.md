# KAMUS BAHASA INDONESIA

* [Deskripsi](#deskripsi)
* [Penggunaan Bahasa Pemprogramman C](#PENGGUNAAN-BAHASA-PEMPROGRAMMAN-C)
* [Penjelasan Menu](#MENU)
	+ [Lihat Kamus](#Lihat-Kamus)
	+ [Cari Kata](#Cari-Kata)
	+ [Masukan Kata](#Masukan-Kata)
	+ [Latihan Kata](#Latihan-Kata)
	+ [Keluar](#Keluar)
* [Header kamus.h dan Fungsi Modular](#HEADER-kamush)


## DESKRIPSI

<p>Program ini dibuat demi memenuhi tuntutan proyek akhir, pada mata kuliah pemograman lanjut. Pada kesempatan kami berkesempatan membuat program "Kamus Besar Bahasa Indonesia dan Latihan Soal". Sesuai dengan judulnya, konsep dari program ini adalah sebuah program yang mengimplementasikan linked list dalam bentuk kamus, jadi isi dari kamus ini diinput melalui file.bin dan user
dapat mengupdate isi kamus dengan menginput kata, definisi, dan tipe kata, melalui opsi insert pada program, dan kata yang sudah di insert akan langsung disorting secara otomatis sesuai abjad. Serta pada program kami terdapat fitur search yang ditujukan untuk mencari kata yang ingin kita mau, serta fitur latihan soal.</p>

<p>Created by:
<br>              Aqdam Zain Hajj & Muhammad Alfiyansyah 
<br>                        Teknik Komputer
<br>                     Universitas Indonesia</p>

## PENGGUNAAN BAHASA PEMPROGRAMMAN C

<p>Aplikasi Kami menggunakan bahasa pemprogramman C. Beberapa penggunaan bahasa pemprogramman C yang penting dalam program kami adalah pointer, struct, dan linked, berikut penjelasan masing-masingya.</p>

* Pointer
<p>Pointer merupakan variabel yang menyimpan address dari memori(variabel lain)</p>
	

## MENU

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Menu.JPG" alt="Menu">

<p>code:</p>

```go
#include "kamus.h" // terdapat struct dan semua fungsi modular yang mendukung applikasi kamus

#include <conio.h>
#include <windows.h>
#include <process.h>



void gotoxy (int x, int y)
{
	COORD coord;
	coord.X=x;
	coord.Y=y;

	SetConsoleCursorPosition (GetStdHandle(STD_OUTPUT_HANDLE), coord);
}


int main (void)
{
	int r,q;
	kamusPtr head = NULL, headCpy = NULL, node = NULL, temp;
	int choice, soal;

	gotoxy(50,25);
	printf("Loading....");
	gotoxy(50,27);
	for (r=1; r<=20; r++)
		{
			for (q=0; q<=100000000; q++);
			printf ("%c", 177);
		}

		inputKamus(&head);
	do
	{

		system ("cls");
		/*printf ("\n\n\t\t\t\t========================================\n");
		printf ("\t\t\t\t========================================\n");
		printf ("\t\t\t\t+        KAMUS BAHASA INDONESIA        +");
		printf ("\n\t\t\t\t+                                      +");
		printf ("\n\t\t\t\t+ 1. Lihat Kamus                       +");
		printf ("\n\t\t\t\t+ 2. Cari Kata                         +");
		printf ("\n\t\t\t\t+ 3. Insert Kata                       +");
		printf ("\n\t\t\t\t+ 4. Latihan Kata                      +");
		printf ("\n\t\t\t\t+ 5. Help                              +");
		printf ("\n\t\t\t\t+ 6. Exit                              +");
		printf ("\n\t\t\t\t+                                      +");
		printf ("\n\t\t\t\t+             COPYRIGHT                +");
		printf ("\n\t\t\t\t========================================");
		printf ("\n\t\t\t\t========================================");*/
		printf("  		    `-::://///:+...-.......-..`                `--....--.........`                \n"
"	            .s::::///::--`             .---.         ---.`                `----`                    \n"
"	       ``...-o::--`                       `.:-     -:.```                      .--.                 \n"
"	      -+```         KAMUS                  ``.:- .:.`````  BAHASA INDONESIA       `...-...-.`       \n"
"	 `--/:./                                   ````-o:```````                                 :`-+--.   \n"
"	+yyo/-`/                                   `````+.```````    .....................        : .+..ss. \n"
"	yy:..-`:`                                  `````/.```````                                 : ./` +y+ \n"
"	yy/.`-`:`     1. Lihat Kamus               `````:.```````    .....................        : ..` +yo \n"
"	sy+.`.`-.                                  `````:-```````                                 / ` ` /yo \n"
"	oyo..``.-     2. Cari Kata                 `````-:```````    .....................        /   ` /yo \n"
"	+ys..```/                                  `````.:```````                                 : `   /yo \n"
"	/yy..```/     3. Masukan Kata              `````./```````    .....................       `:`.   /y+ \n"
"	:yh-.```/                                  `````./```````                                ..`.   /y/ \n"
"	.yy:.```:`    4. Latihan Kata              `````./```````    .....................       :```   +y: \n"
"	`yy+````-.                                 `````./```````                                / .`   oy- \n"
"	 yyo`````:    5. Bantuan                   `````./```````    .....................      `: .`   sh. \n"
"	 ssy```` /                                 `````./```````                               -.`. . `yy` \n"
"	 +yy.`.``:`   6. Keluar                    `````./```````    .....................      / `  - `ys  \n"
"	 /yy-`..`-.                                ``````/```````                              .- ` .. -yo  \n"
"	 -yy/``- `:                                ``````/```````    ```.------.----...```     :` ` :` /y/  \n"
"	 `hyo``:` /       ````...............```  ```````/````````.-............``````.....--`.:  ``/  sy-  \n"
"	  yys`.-. :` ``--.....```````````````...--.``````/`````--..  `` `````                `-:```:- `yy`  \n"
"	  osy...: -:...      ````       ````````` .--.``./``.:-`  ``.``.`````````              `-:`+` -ys   \n"
"	  /yy-.`+--`       ``..-:///+++++++/:-.```   .:-./.:-` ``..:+ossyyyyyyysso++/:.``````....:o:  +y/   \n"
"	  -yy+.::`   ``.-/oosyhhyyyyyyyyyyyyyhhys/.`  `-/o:.`  `/shhhyyyyyyyyyyyyyyyyhhyso+:-.`...-:-`yy.   \n"
"	  `hss/-.-:+osyhhyyyhhhhhhhhhhhhhhhyyysyhdh+.` .-+-.` -yddyyyyyyhhhhhhhhhhhhhhhhyyyhhyso+//:/oys    \n"
"	   syhhhhhhhhhhyysso+//:::--..``        sdhyoo+++o+++oyhhd-        ``..-::://++ossyyhhhhhhhhyyh:    \n"
"	   ./+/:--.`                            `-/+ossssssssso+:.                            `..-::/+:");
		printf ("\n\t\t\t\tInput Pilihan :");
		scanf ("%d", &choice);
		getchar();
		int llen, radnum, correct, jwb, i, j;
		kamusPtr* soalArr;
		char** jwbArr;
		int* intArr;
		char* key;
		char pilihC;
		switch (choice)
		{
		case 1:
		.........
		.........
		case 6:
		}
	}while (choice!=-1);
}
```

[Kembali ke daftar isi](#kamus-bahasa-indonesia)

### Lihat Kamus

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/List%20kata.JPG" alt="Lihat kamus">
<p> Dapat melihat keseluruhan isi kamus.</p>

<p>code:</p>

```go
			case 1://Lihat kata
				system ("cls");
				listkata (head);
				printf("\nTekan Enter untuk lanjutkan: ");
				getchar();
				system ("cls");
				break;
```

[Kembali ke daftar isi](#kamus-bahasa-indonesia)

### Cari Kata

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Cari.JPG" alt="Lihat kamus">
<p>Mencari kata dalam kamus dengan memasukan kata kunci yang sesuai dengan kata yang dicari.</p>
<p>Pencarian menggunakan sequential search pada linked list.</p>

<p>Code:</p>

```go
			case 2://Cari kata
				system ("cls");
				temp = head;
				key = malloc(100*sizeof(char));
				printf(" Input kata kunci: ");
				gets(key);
				realloc(key,(strlen(key)+1)*sizeof(char));
				up_str(key);
				while(temp!=NULL)
                {
                    if(strcmp(key,temp->kata)==0)
                    {
                        printf("Kata:       %s\n", temp->kata);
                        printf("Definisi:   %s\n", temp->definisi);
                        printf("Tipe:       %s\n", temp->tipe);
                    }
                    temp = temp->next;
                }
				getch();
				//free the memory allocation after used
				free(key);
				system ("cls");
				break;
```

[Kembali ke daftar isi](#kamus-bahasa-indonesia)

### Masukan Kata

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Masukan.JPG" alt="Lihat kamus">
<p>Memasukan kata baru ke dalam kamus, inputnya berupa Kata, Definisi, dan Tipe katanya. Kata yang telah dimasukan akan otomatis terurut sesuai abjad</p>

```go
case 3://Masukan kata
				system ("cls");
   				inputKata(&head);
   				printKamusF(head, listLen(head));
   				printf("\nTekan Enter untuk lanjutkan: ");
   				getchar();
   				system ("cls");
    			break;
```

[Kembali ke daftar isi](#kamus-bahasa-indonesia)

### Latihan Kata

<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/soal1.JPG" alt="Lihat kamus">
<p>Menentukan jumlah soal latihan sesuai dengan yang dinginkan</p>
<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/soal2.JPG" alt="Lihat kamus">
<p>Memilih jawaban pada soal</p>
<img src="https://raw.githubusercontent.com/Alfiyansyah76/Kamus-Bahasa-Indonesia/master/Image/Soal3.JPG" alt="Lihat kamus">
<p>Menampilkan seluruh hasil dari jawaban pada soal</p>
<p>Code:</p>

```go
            case 4://Latihan kata
                system("cls");
                printf(" Masukan jumlah soal: ");
                scanf("%d", &soal);
                getchar();
                system("cls");
                correct = 0;
                listCpy(head, &headCpy);
                llen = listLen(headCpy);

                soalArr = malloc(soal*sizeof(kamusPtr));
                jwbArr = malloc(4*sizeof(char*));
                intArr = malloc(4*sizeof(int));

                for(i=0; i<soal; i++) // mengambil soal dari linked list
                {
                    radnum = rand()%(llen);
                    takeNode(&headCpy, radnum, &node);
                    soalArr[i] = node; // Memasukan address node yang telah diambil dari list ke dalam array
                    // soalArr = kumpulan address dari node yang akan menjadi soal dari latihan
                    llen = llen-1;
                }

                for(i=0; i<soal; i++)
                {
                    randnumArr(intArr, 4);
                    do
                    {
                        printf(" %s\n\n", (soalArr[i]->definisi));
                        jwbArr[intArr[0]] = soalArr[i]->kata;//Input pilihan benar ke array dengan nilai index yg random sesuai urutan
                        for(j=1; j<4; j++)
                        {//input pilihan salah ke array dengan nilai index yg random sesuai urutan
                            answerChKat(head, listLen(head), soalArr[i]->kata, &jwbArr[intArr[j]]);//mengambil pilihan salah dari linked list secara acak yang berbeda dengan
                                                                                                        //pilihan benar.
                        }
                        for(j=0; j<4; j++)
                        {
                            printf(" %d. %s\n",(j+1), jwbArr[j]);
                        }
                        printf(" Jawaban: ");
                        scanf("%d", &jwb);
                        getchar();
                        system("cls");

                    }while(jwb<1 || jwb>4);

                    if(strcmp(jwbArr[jwb-1], soalArr[i]->kata)==0)//menghitung nilai jawaban yang benar
                    {
                        correct = correct + 1;
                        printf("\a");
                        printf("\n BENAR!\n");
                    }
                    else
                    {
                        printf("\n SALAH!\n");
                    }
                    Sleep(200);
                    system("cls");
                }
                //menampilkan jawaban benar dan salah
                printf("\n\n Jumlah Benar: %d\n", correct);
                printf(" Salah       : %d\n", (soal-correct));

                printf("\n Kunci Jawaban: \n");

                for(i=0; i<soal; i++)
                {
                    printf(" %d. Definisi: %s\n", (i+1), soalArr[i]->definisi);
                    printf("     Kata    : %s\n\n", soalArr[i]->kata);
                }

                //free the memory allocation after used
                free(soalArr);
                free(jwbArr);
                free(intArr);
                while(headCpy!=NULL)
                {
                    temp = headCpy;
                    headCpy = headCpy->next;
                    free(temp);
                }

                printf("\n Enter untuk kembali ke menu: ");
                getchar();
                system("cls");
                break;
```

[Kembali ke daftar isi](#kamus-bahasa-indonesia)

### Keluar

[Kembali ke daftar isi](#kamus-bahasa-indonesia)

## HEADER kamus.h

[Kembali ke daftar isi](#kamus-bahasa-indonesia)
