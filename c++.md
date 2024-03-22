# C++
C++ alapok

## Működés
1. Előfordítás
2. Fordítás
3. Linkelés

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
std::vector<int> v(10); //10 lesz a tárhyle
std::vector<int> v(10, 5); //10 elem lesz és az összes 5 értékkel
std::vector<int> v{1,2,3,4,5}; //adott értékkel feltöltés
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
Kapacitás: (0,1,2,4,8,16... tárolás)
```
v.capacity();
```
Kapacitás megadása: 
```
v.reserve(100);
```
Rendezés:
```
std::sort(v.begin(), v.end());
```
csak az első x elemet:
```
std::sort(v.begin(), v.begin()+4);
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

### For:
```
for (int item : lista)
{
}
```
Ezzel a lista elemek értékén lehet változtatni az alap listában.
```
for (int& item : lista)
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

## Iterátorok
### pl.:
```
std::vector<int> v{1,2,3,4,5,6,7};
std::vector<int>::iterator it = v.begin(); //Első eleme a V vectornak
std::vector<int>::iterator it = v.begin()+3; //Negyedik eleme a V vectornak
std::vector<int>::iterator it2 = v.end(); //Utolsó+1 eleme a V vectornak
```
### Ciklusban jól használható:
```
for (std::vector<int>::iterator it = v.begin(); it != v.end(); ++it)
{
//it-t lehet használni
}
```
```
for (std::vector<int>::iterator it = std::begin(v); it != std::end(v); ++it)
{
//it-t lehet használni
}
```
### Lehet konstansnak állítani, de akkor nem lehet léptetni:
```
const std::vector<int>::iterator it = v.end();
std::vector<int>::const_iterator it = v.end();
```
### Konstans ciklusban: (kiíratáshoz jól lehet használni)
```
for (std::vector<int>::const_iterator it = v.cbegin(); it != v.cend(); ++it)
{
  std::cout << *it << std::endl; 
}
```
### Keresés: 
(Ha nem talál akkor v.end lesz az értéke)
```
std::vector<int>::iterator it = std::find(v.begin(), v.end(), 12);
```

## Függvények
### értékkel vissza térő
Kb úgy működik mint c#-ban, de fontos, hogy mielőtt még hivatkoznánk rá, az előtt legyen a kódban, de ennek van egy megkerülése.
Példa egy int-re:
```
int valami(const int x)
{
  return x;
}
//meghívása: valami(9);
```
Hivatkozási megkerülés:
```
int fg(const int x)

int main()
{
  fg(9);
}

int fg(const int x)
{
  return x;
}
```
Konstans változó megadása:
```
int valami(const int x, const int n=2)
{
  return x;
}
```

## Névterek
Külön névtereket lehet létrehozni, amiben elemekre lehet hivatkozni. Lehet egy névtérben több névteret létrehozni.
```
namespace a
{
  void f()
  {
    //
  }
}
```
Havatkozás a fenti fg-re:
```
a::f();
```

## Véletlenszám generálás
Pl.:
```
#include <random>

int main()
{
  std::random_device rD;
  std::default_random_engine rE(rD());
  std::uniform_int_distribution<int> uniform_dist(1,10);

  int rnd = uniform_dist(rE);

  std::normal_distribution<double> normal_dist(0,1);

  double drnd = normal_dist(rE);
} 
```

## Inline függvények
Ahol meghívjük ezt a fg-t, oda bekerül a fg törzse, mert inline-ba történik. Fg kódja befordul az adott helyre.
pl.:
```
inline int fg(const int x)
{
  return x;
}
```

## OOP
Osztályok létrehozása és "meghívása" (include).
A "#include"-ot már többször is használtuk és az pont egy osztályt importál be, ami alapján tudunk a többi elemmel tovább foglalkozni.

### Rekord
Publikus adat tagjai vannak.
```
struct Student {
  std::string name; //Ehhez include-álni kell a <string> beépített osztályt.
  int age;

  std::string ToString()
  {
    std::string s = "";
    s += name;
    s += ", ";
    s += std::to_string(age);
    return s;
  }
};

int main()
{
  Student student01;
  student01.name = "Hallgato Huba";
  student01.age = 19;
  std::cout << student01.ToString() << std::endl;
}
```


### Szimpla osztály a main.cpp-ben:
```
class Name {
public:
  Name(const std::string& firstName, const std::string& lastName)
  {
    mFirstName = firstName;
    mLastName = lastName;
  }

  void SetFirstName(const std::string& firstName)
  {
    mFirstName = firstName;
  }

  void SetLastName(const std::string& lastName)
  {
    mLastName = lastName;
  }

  std::string ToString()
  {
    return mFirstName + " " + mLastname;
  }
private:
  std::string mFirstName; //Ehhez include-álni kell a <string> beépített osztályt.
  std::string mLastName;
}

class Student {
public:
  Student()
    : mName("Unknown", "Unknown")
    , mAge(std::numeric_limits<int>::max()) //használni kell: #include <limits>
  {}
  Student(const std::string& firstName, const std::string& lastName, const int age)
    : mName(firstName, lastName)
    , mAge(age)
  {
    //Ezek akkor voltak jók, ha szöveg volt a name: this->mName = name; (*this).mName = name; mName = name;
    //this->mAge = age;
  }

  ~Student() //Destructor
  {
  }

  Name GetName() const
  {
    return mName;
  }

  int GetAge() const
  {
    return mAge;
  }

  Student& SetName(const std::string& firstName, const std::string& lastName)
  {
    mName.SetFirstName(firstName);
    mName.SetLastName(lastName);
    return *this;
  }

  Student& SetAge(const int age)
  {
    mAge = age;
    return *this;
  }

  std::string ToString()
  {
    std::string s = "";
    s += mName;
    s += ", ";
    s += std::to_string(mAge);
    return s;
  }

private:
  Name mName;
  int mAge = 0;
};

int main()
{
  Student student01("Hallgato Huba", 19);
  std::cout << student01.ToString() << std::endl;
}
```

### Az előző felbontása fájlokra
2 fajta fájl lesz, a .h és a .cpp.

