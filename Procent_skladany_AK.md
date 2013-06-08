//Procent skladany - zaliczenie.

#include <stdio.h>
#include <string.h>
#include <math.h>



// zwraca wartosc rozna od 0 gdy liczba nie zawiera jednosci (wielokrotnosc 10 lub -nascie)
int nieMaJednosci(unsigned int liczba)
{
  liczba %= 100;
  return ( liczba >= 10 && liczba < 20 );
}

// zamien jednosci na slowa
const char *jednosci(unsigned int liczba)
{
  if ( nieMaJednosci(liczba) ) // wyjdz jesli liczba z przedzialu [10-19]
    return "";

  liczba %= 10; // wyciagnij jednosci z liczby
  switch (liczba) {
  case 1: return "jeden ";
  case 2: return "dwa ";
  case 3: return "trzy ";
  case 4: return "cztery ";
  case 5: return "piec ";
  case 6: return "szesc ";
  case 7: return "siedem ";
  case 8: return "osiem ";
  case 9: return "dziewiec ";
  default : return ""; // pozoztale liczby ignoruj 
  }
}

// zamienia na slowa liczby od z przedzialu [10-19]
const char *nascie(unsigned int liczba)
{  
  liczba %= 100; // obetnij liczbe ponizej stu
  switch (liczba) {
  case 10: return "dziesiec ";
  case 11: return "jedenascie ";
  case 12: return "dwanascie ";
  case 13: return "trzynascie ";
  case 14: return "czternascie ";
  case 15: return "pietnascie ";
  case 16: return "szesnascie ";
  case 17: return "siedemnascie ";
  case 18: return "osiemnascie ";
  case 19: return "dziewietnascie ";
  default: return ""; // pozostale liczby ignoruj
  }


}

// zamienia na slowa liczby od z przedzialu [1-19]
const char *jednosciLubNascie(unsigned int liczba)
{
  switch (liczba % 100) {
  case 10: return "dziesiec ";
  case 11: return "jedenascie ";
  case 12: return "dwanascie ";
  case 13: return "trzynascie ";
  case 14: return "czternascie ";
  case 15: return "pietnascie ";
  case 16: return "szesnascie ";
  case 17: return "siedemnascie ";
  case 18: return "osiemnascie ";
  case 19: return "dziewietnascie ";
  default: break;
  }

  switch (liczba % 10) {
  case 1: return "jeden ";
  case 2: return "dwa ";
  case 3: return "trzy ";
  case 4: return "cztery ";
  case 5: return "piec ";
  case 6: return "szesc ";
  case 7: return "siedem ";
  case 8: return "osiem ";
  case 9: return "dziewiec ";
  default : return ""; // pozoztale liczbu ignoruj 
  }

}

// zamienia na slowa pelne dziesiatki
const char *dziesiatki(unsigned int liczba)
{
  // oblicz pelne dziesiatki
  liczba %= 100;
  liczba -= (liczba % 10);

  switch (liczba) {
  case 20: return "dwadziescia ";
  case 30: return "trzydziesci ";
  case 40: return "czterdziesci ";
  case 50: return "piecdziesiat ";
  case 60: return "szescdziesiat ";
  case 70: return "siedemdziesiat ";
  case 80: return "osiemdziesiat ";
  case 90: return "dziewiecdziesiat ";
  default : return ""; // pozoztale liczbu ignoruj
  }
}


// zamienia na slowa pelne setki
const char *setki(unsigned int liczba)
{
  // oblicz pelne setki
  liczba %= 1000;
  liczba -= (liczba % 100);

  switch (liczba) {
  case 100: return "sto ";
  case 200: return "dwiescie ";
  case 300: return "trzysta ";
  case 400: return "czterysta ";
  case 500: return "piecset ";
  case 600: return "szescset ";
  case 700: return "siedemset ";
  case 800: return "osiemset ";
  case 900: return "dziewiecset ";
  default : return "";    
  }
}

// zamienia na slowa liczby dodatnie, mniejsze od 1000
const char *liczbaDo1000Slownie(unsigned int liczba)
{
  static char slownie[256];
  
  slownie[0] = '\0';

  strcat( slownie, setki( liczba ) );
  
  strcat( slownie, dziesiatki( liczba) );
  strcat( slownie, jednosciLubNascie( liczba) );
  //strcat( slownie, nascie( liczba ) );

  if ( liczba > 0 ) {
    
    // strcat( slownie, jednosci( liczba ) );
  } else {  
    if ( strlen(slownie) == 0) {
      strcat( slownie, "zero" );
    }
  }
  return slownie;
}


// zamien liczbe na slowa
// zamienia liczby mniejsze niz 1e12
const char *liczbaSlownie(unsigned int liczba, char *slownie) 
{
  slownie[0] = '\0';
  
  if ( liczba / 1000000000 > 0 ) {
    strcat( slownie, liczbaDo1000Slownie( liczba / 1000000000 ) );
    strcat( slownie, "mld ");
    liczba %= 1000000000; // pozbadz sie miliardow
  }
  
  if ( (liczba / 1000000) > 0 ) {
    strcat( slownie, liczbaDo1000Slownie( liczba / 1000000 ) );
    strcat( slownie, "mln " );
    liczba %= 1000000; // pozbadz sie milionow
  }

  if ( (liczba / 1000) > 0 ) {
    strcat( slownie, liczbaDo1000Slownie( liczba / 1000) );
    strcat( slownie, "tys. " );
    liczba %= 1000; // pozbadz sie tysiecy
  }

  strcat( slownie, liczbaDo1000Slownie( liczba ) );

  return slownie;
}

double procent_skladany (double kwota, double oprocent, int okres_kapit, int okres_lokaty)
{
  double ilosc_kapit = 12.0 / okres_kapit;
	double okres_lokaty_lata = okres_lokaty/12.0;
	double oprocent_ulamek = oprocent/100.0;
	
	double kwota_koncowa = kwota * pow(1+oprocent_ulamek/ilosc_kapit, okres_lokaty_lata*ilosc_kapit);
	
	return kwota_koncowa;
	
}

int main(void)
{
  double kwota, oprocent, kwota_koncowa;
  int okres_kapit, okres_lokaty;
  int kwota_koncowa_zlote, kwota_koncowa_grosze;
  char zlote_slownie[200], grosze_slownie[200] ;	
	
  printf("Podaj kwote poczatkowa: ");
  scanf("%lf", &kwota);
  printf("Podaj oprocentowanie w stosunku rocznym (procent): ");
  scanf("%lf", &oprocent);
  printf("Podaj okres kapitalizacji odsetek (miesiecy): ");
  scanf("%d", &okres_kapit);
  printf("Podaj okres lokaty (miesiecy): ");
  scanf("%d", &okres_lokaty);
  kwota_koncowa = procent_skladany(kwota, oprocent, okres_kapit, okres_lokaty);
  kwota_koncowa_zlote = floor (kwota_koncowa); // pozbadz sie czesci ulamkowej (groszy)
  kwota_koncowa_grosze = round((kwota_koncowa-kwota_koncowa_zlote)*100); // oblicz czesc ulamkowa i zamien na grosze i zaokraglij
  
  printf("Kwota do wyplaty: %d,%d\n", kwota_koncowa_zlote, kwota_koncowa_grosze);
  printf("Kwota do wyplaty slownie: %s zl %s gr\n", liczbaSlownie (kwota_koncowa_zlote,zlote_slownie), liczbaSlownie (kwota_koncowa_grosze, grosze_slownie));
  
  
  getchar();
  getchar();

  return 0;
}
