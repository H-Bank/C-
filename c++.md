# C++
C++ alapok

## Main
Ez egy függvény, ami szám típussal tér vissza. Ha 0, akkor minden rendben lefutott, de ha 0-tól eltérő a szám, akkor hiba történt futás közben.
```
int main()
{
}
```

## Using

Ennél az összes std-nél megengedjük, hogy használjük szimplán.
```
using namespace std;
```
Csak a cout-ra adunk engedélyt! (Többinél is így működik)
```
using std::cout;
```

## Kiíratás/bekérés
```
std::string firstName;
std::cout << "What's your name? ";
std::cin >> firstName;
std::cout << "Hello "<< firstName<< "!\n";
```
A std::cout lehet kiírni a console-ra és azt írja ki, ami << után szerepel.
A std::cin lehet bekérni az adatot egy változóba. Jelenleg a >> mögött álló szöveg változóba írjuk be az adatokat.
Ha consolera kiszeretnénk írni változót, akkor << IDE << ebben a formátumban az IDE helyére kell írni a változó nevét.

## Típusok
### Szám
Ebből nagyon sok féle variáció szerepel, de nem tudjuk, hogy hány bit-en van tárolva. Illetve fontos, hogy a típushoz megfelelően adjuk meg a számokat is, hivatkozni kell a típusra érték adásnál is (pl majd az unsigned int-nél)!
- Int
```
int a = 5;
```
- unsigned int (nincs előjele)
```
unsigned int b = 12U;
```
- short int
```
short int c;
```
- unsigned short int (nincs előjele)
```
unsigned short int d;
```
- long int
```
long int e = 12L;
```
- unsigned long int (nincs előjele)
```
unsigned long int f = 344ul;
```
- long long
```
long long g;
```

Egész típusok amik a C++11 óta léteznek.
Ezeknél már tudjuk, hogy hány bit-et foglal. 
```
int8_t a;
uint8_t b;
```
Lehetségesek: 4, 8, 16, 32, 64

### Lebegőpontos típusok
```
float f = 3.14f;
double d = 314;
```
Float-nál az f fontos a számhoz.

### Karakter
Fixen tudjuk, hogy 8 bit unsigned.
```
char h='a';
```

### Logikai
```
bool b = true;
b = 56;
```
Érdekesség, hogy lehet számot is megadni és ha nem 0, akkor igaz az értéke.

### Referencia típus
Lehet hivatkozni arra, hogy a memoriában hol van az adat a változóval, de az értékére.
```
int a = 5;
int& b = a;
```

### Konstans érték
Amikor létrehozzuk, csak akkor tudunk neki értéket adni és későbbiekben már nem lehet!
```
const int b = 6;
```

### konstans referencia
```
const int c = 6;
const int& d = c;
const int& f = 42;
```

### Pointerek
Pl.:
```
int a = 5;
std::cout << "a erteke: " << a << "a cime. " << &a << std::endl;
int* p = &a; // p pointer egy int-re
std::cout << p << std::endl;
std::cout << *p << std::endl;

const int b = 4;
const int* pb = &b; //pb egy pointer, ami const, értékét ilyenkor a *pb-n keresztül érjük el
*pb = 10 //új érték azon a memória területen 10 lesz

int* const pa = &a; // pa egy conts pointer egy int-re

const int* const pc = nullptr;
```

## típusokhoz segítő dolgok
### Szám mérete:
```
int a = 5;
int b = sizeof(a);
```
### Min/Max méret: (int helyett lehet más típust oda írni)
```
int a = std::numeric_limits<int>::min();
int b = std::numeric_limits<int>::max();

int a = std::numeric_limits<decltype(a)>::min();
int b = std::numeric_limits<decltype(a)>::max();
```
### Castolás: (Lehetnek vesztések)
```
uint32_t b = 65536;
uint16_t a = static_cast<uint16_t>(b);
```

## Több adat tárolása
### Tömb
```
int t[5];
int tt[] = {1,2,3,4,5};
```
Hivatkozás:
```
int t[5];
t[3] = 13;
*(t+2) = 13; //Az előzővel megegyezik
```
Tömb mérete megkapása:
```
int t[5];
int sizeOfT = sizeof(t) / sizeof(t[0]);
```

### Vector
Létrehozása: (int helyett lehet más típust használni)
```
std::vector<int> v;
```
Méretnek lekérése:
```
v.size();
```
Elem berakása:
```
v.push_back(10);
```
Elem lekérése:
```
v[0] //ez lesz a 10-es
```

## Vezérlési szerkezetek
### Ha:
```
if (true) //logika
{} //igaz ág
else
{} //hamis ág
```

### Switch:
```
switch ()
{
  case 1:
        //1. ág
        break;
  case 2:
        //2. ág
        break;
  default:
        //default ág
        break;
}
```

### Fori:
```
for (int i = 0; i < 10; i++)
{
}
```

### While: (elől tesztelő)
```
int i=0;
while (i<10)
{
i++;
}
```

### Dowhile: (hátul tesztelő
```
int i=0;
do {
i++;
} while (i<10)
```
