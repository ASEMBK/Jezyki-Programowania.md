Języki Programowania - Wykład 1.
Treść zadania pierwszego:

"Wypisz liczby całkowite od 0 do 23 za pomocą pętli for, while i do-while."

    ```c
    pętla for:

#include <stdio.h>
int main() {
int i;
for (i=0; i<=23; i++) {
printf("%d,", i);
}
getchar();
return 0;
}

    pętla while:

#include <stdio.h>
int main() {
int i=0;
while (i<=23) {
printf("%d,", i);
i++;
}
getchar();
return 0;
}

    pętla do-while:

#include <stdio.h>
int main() {
int i=0;
do {
printf("%d,", i);
i++;
}
while(i<=23);
getchar();
return 0;
}

    połączenie wszystkich pętli w jednym programie - potrójnie wyświetla listę:

#include <stdio.h>
int main() {
int i;
for (i=0; i<=23; i++) {
printf("%d,", i);
}
putchar('\n');


i=0;
while (i<=23) {
printf("%d,", i);
i++;
}
putchar('\n');


i=0;
do {
printf("%d,", i);
i++;
}
while(i<=23);

getchar();
return 0;
}

Treść zadania drugiego:

"Wypisz liczby od -3.5 do 7.5 z krokiem co 0.5 za pomocą pętli for i while."

#include <stdio.h>
int main() {
double i;
for (i=-3.5; i<=7.5; i=i+0.5) {
    printf("%.1lf,", i);
}

printf("\n\n\n");

i=-3.5;
while (i<=7.5) {
      printf("%4.1lf,\n", i);
      i=i+0.5;
}
getchar();
return 0;
}

Treść zadania trzeciego:

"Wczytaj n liczb i wyświetl ich sume i średnią arytmetyczną."

# include <stdio.h>
int main () {
    int n, i;
    double x, suma=0.0, srednia;
    do     {
    printf("Podaj ilosc liczb (co najmniej 1):");
    scanf("%d", &n);
    }
    while(n<1);

    for(i=1;i<=n;i++) {
                     printf("Podaj %d liczbe:", i);
                     scanf("%lf", &x);
                     suma=suma+x;
                     }
    srednia=suma/n;
    printf("Suma podanych %d liczb wynosi: %lf \n", n, suma);
    printf("Srednia z podanych %d liczb wynosi: %lf", n,srednia);
    getchar();
    getchar();
    return 0;
}

Treść zadania czwartego:

"Wypisz kwadraty i sześciany liczb naturalnych od 1 do liczby podanej przez użytkownika za pomocą pętli for, while i do-while."

#include <stdio.h>
int main() {
int i, n;
    printf("Podaj liczbe:");
    scanf("%d", &n);
    for(i=1;i<=n;i++) {                     /*Pętla for*/
    printf("%d %d %d \n", i, i*i, i*i*i);
    }

    printf("\n");                               /*oddzielenie wyników*/

    i=1;                                        /*Pętla while*/
    while(i<=n) {
    printf("%d %d %d \n", i, i*i, i*i*i);
    i++;
    }

    printf("\n");                               /*oddzielenie wyników*/

    i=1;                                        /*Pętla do-while*/
    do  {
    printf("%d %d %d \n", i, i*i, i*i*i);
    i++;
        }
    while(i<=n);
    getchar();
    getchar();
    return 0;
}

Treść zadania piątego:

"Oblicz za pomocą pętli for i while sumę kwadratów liczb od 3 do 15."

#include <stdio.h>
int main() {
int i, suma=0;
    for(i=3;i<=15;i++) {  /*Pętla for*/
        suma=suma+(i*i);
    }
    printf("%d \n",suma);

    printf("\n");       /*Rozdzielenie wyników */


    i=3;            /*Pętla while; w tym miejscu ustawiamy i */
    suma=0;         /*wyzerowanie sumy, ponieważ nie jest już =0*/
    while(i<=15)    {
    suma=suma+(i*i);
    i++;
    }
    printf("%d \n",suma);
    getchar();
    return 0;
}

Treść zadania szóstego:

"Wypisz sinusy i cosinusy kątów 0…180 stopni z krokiem co 30 stopni za pomocą pętli for."

#include <stdio.h>
#include <math.h>
int main() {
double i;
    for(i=0;i<=180;i=i+30) {
       printf("sin(%.0lf)= %lf \n",i,sin(i*M_PI/180));
       printf("cos(%.0lf)= %lf \n\n",i ,cos(i*M_PI/180));
}
    getchar();
    return 0;
}

Treść zadania siódmego:

"Wypisz znaki do ‘a’ do ‘k’ wraz z ich kodami ASCII (dziesiętnie i szesnastkowo) w kolejności rosnącej i malejącej za pomocą pętli for."

#include <stdio.h>
int main() {
char i='a';
    for(i='a';i<='k';i++) {
    printf("Litera: %c znak ASCII: %3d szesnastkowo: %2x \n",i,i,i);
    }
    getchar();
    return 0;
}

Treść zadania ósmego:

"Napisz pętle while wypisującą na ekran znaki podane przez użytkownika, aż do napotkania znaku ‘x’."

    Wersja 1:

#include <stdio.h>
#define znak 'x'
int main() {
char i='a';
    while(i!=znak)    {
       printf("Podaj litere:");
       scanf("%c", &i);
       printf("Podales litere:%c \n\n",i);
       getchar();
  }
    getchar();
    return 0;
}

    Wersja 2:

#include <stdio.h>
int main() {
char i;
    while((i=getchar())!='x' && i!='X')
    putchar(i);
    getchar();
    return 0;
}

Treść zadania dziewiątego:

"Napisz program wyświetlający tabliczkę mnożenia do 13 (użyj pętli !)."

    Program - pierwsza wersja:

#include <stdio.h> 
int main() 
{ 
int i,j; 
for(i=1;i<=13;i++)   { 
    for(j=1;j<=13;j++)  {
        printf("%4d ",j*i); 
                        }
    putchar('\n'); 
                    } 
getchar();
return 0;
}

    Program - wersja ulepszona:

#include <stdio.h> 
int main() 
{ 
int i,j;
printf("    |");
for(i=1;i<=13;i++)  {
                    printf("%4d ",i);
                    }
printf("\n----|----------------------------------------------------------------\n");                 
for(i=1;i<=13;i++)  { 
    for(j=1;j<=13;j++)  {
                                                if(j==1){
                                 printf("%3d |",j*i);
                                 }
        printf("%4d ",j*i); 
                        }
    putchar('\n'); 
                    } 
getchar();
return 0;
}
```c
