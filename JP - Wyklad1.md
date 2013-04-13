### Treść zadania 1
Napisz funkcję obliczającą pole kuli o podanym promieniu.
```c
#include <stdio.h>
#include <math.h>

double pole(double r);

int main() {
    double r, p;
    printf("Podaj promien kuli: ");
    scanf("%lf",&r);
    p=pole(r);
    printf("\n\n Pole kola o promieniu %lf ma wartosc %lf", r, p);
    getchar();
    getchar();
    return 0;
        }   

double pole(double r) {
    double p;
    p=4*M_PI*r*r;                                                          
    return p;    
}
```
### Treść zadania 2
Napisz funkcję warBezwzgledna zwracajaca wartość bezwzględną z liczby całkowitej.

```c
#include <stdio.h>

int wartBezwzgledna(int x);

int main() {
    int x,y;
    puts("Podaj liczbe: ");
    scanf("%d",&x);
    y=wartBezwzgledna(x);
    printf("\n\n Wartosc bezwzgledna z %d wynosi %d", x, y);
    getchar();
    getchar();
    return 0;
        }   

int wartBezwzgledna(int x) {
    if(x<=0)
    x=-x;
    return x;    
}
```

### Treść zadania 3
Napisz funkcję obliczającą a do potęgi n dla n należącego do N za pomocą pętli.

```c
#include <stdio.h>
int main() {
    double a,x=1;
    int n, i;
    puts("Podaj liczbe: ");
    scanf("%lf",&a);
    puts("Podaj wykladnik (liczba naturalna): ");
    scanf("%d",&n);
    for(i=1;i<=n;i++){
    x=x*a;
}
    printf("\n\n Wartosc %lf do potegi %d wynosi %lf ", a, n, x);
    getchar();
    getchar();
    return 0;
        }
```

lub jako funkcja

```c
#include <stdio.h>
double potegaAn(double a, int n);

int main() {
    double a, x;
    int n;
    puts("Podaj liczbe: ");
    scanf("%lf",&a);
    puts("Podaj wykladnik (liczba naturalna): ");
    scanf("%d",&n);
    x=potegaAn(a,n);
    printf("\n\n Wartosc %lf do potegi %d wynosi %lf ", a, n, x);
    getchar();
    getchar();
    return 0;
        }   
double potegaAn(double a, int n) {
    int i;
    double x=1.0;
    for(i=1;i<=n;i++){
    x=x*a;
}
    return x;
}

```c

