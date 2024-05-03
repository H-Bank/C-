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

#### Name osztály
.h:
```
#pragma once
#include <string>

class Name {
public:
  Name(const std::string& firstName, const std::string& lastName);

  void SetFirstName(const std::string& firstName);
  void SetLastName(const std::string& lastName);

  std::string ToString() const;

private:
  std::string mFirstName; //Ehhez include-álni kell a <string> beépített osztályt.
  std::string mLastName;
}
```

.cpp:
```
#include "name.h"

Name::Name(const std::string& firstName, const std::string& lastName)
{
  mFirstName = firstName;
  mLastName = lastName;
}

Name& Name::SetFirstName(const std::string& firstName)
{
  mFirstName = firstName;
}

Name& Name::SetLastName(const std::string& lastName)
{
  mLastName = lastName;
}

std::string Name::ToString() const
{
  return mFirstName + " " + mLastname;
}
```

#### Student osztály
.h:
```
#pragma once

#include "name.h"

class Student {
public:
  Student();
  Student(const std::string& firstName, const std::string& lastName, const int age);

  ~Student(); //Destructor

  Name GetName() const;

  int GetAge() const;

  Student& SetName(const std::string& firstName, const std::string& lastName);

  Student& SetAge(const int age);

  std::string ToString();

private:
  Name mName;
  int mAge = 0;
};
```

.cpp:
```
#include "student.h"
#include <iostream>

Student::Student()
    : mName("Unknown", "Unknown")
    , mAge(std::numeric_limits<int>::max()) //használni kell: #include <limits>
  {}
Student::Student(const std::string& firstName, const std::string& lastName, const int age)
  : mName(firstName, lastName)
  , mAge(age)
{
  //Ezek akkor voltak jók, ha szöveg volt a name: this->mName = name; (*this).mName = name; mName = name;
  //this->mAge = age;
}

Student::~Student() //Destructor
{
}

Name Student::GetName() const
{
  return mName;
}

int Student::GetAge() const
{
  return mAge;
}

Student& Student::SetName(const std::string& firstName, const std::string& lastName)
{
  mName.SetFirstName(firstName);
  mName.SetLastName(lastName);
  return *this;
}

Student& Student::SetAge(const int age)
{
  mAge = age;
  return *this;
}

std::string Student::ToString()
{
  std::string s = "";
  s += mName;
  s += ", ";
  s += std::to_string(mAge);
  return s;
}
```

#### main
```
#include <iostream>
#include <limits>
#include <string>

#include "student.h"

int main()
{
  Student student01("Hallgato", "Huba", 19);
  std::cout << student01.ToString() << std::endl;
}
```

### Extra dolgok:

#### Optional visszatérés
pl.:
```
#include <optional>

class osztaly
{
public:
  std::optional<int> Top() const
  {
	  if (mTop == nullptr) return std::nullopt;
	  return mTop->GetData();
  }
}
```

#### Operator változtatás
Az összes operátorra külön lehet változtatást csinálni, hogy mit csináljon. Ezeknél is lehet használni a default és a delete kulcs szavakat:
```
class osztaly
{
public:
	osztaly& operator=(const osztaly& other) = default;

	osztaly& operator=(const osztaly& other) = delete;
}
```

##### Egyenlőség:
```
class osztaly
{
public:
  Stack& operator=(const osztaly& other)
  {
	  if (this == &other) return *this;

	  if (other.mHead == nullptr) return *this;

	  return *this;
  }
}
```

##### Összeadás:
```
class osztaly
{
public:
  	osztaly operator+(const osztaly& lhs, const osztaly&rhs)
	{
		osztaly result;
		result.a = lhs.a + lhs.b;
		return result;
	}

	osztaly operator+(const osztaly& other)
	{
		a += other.a;
		return *this;
	}

	osztaly operator+(const double other)
	{
		a += other;
		return *this;
	}

	friend osztaly operator+(const double lhs, const osztaly&rhs);
}

osztaly operator+8const double lhs, const osztaly&rhs)
{
	osztaly result;
	result.a = lhs + rehs.a;
	return result;
}
```

##### Többinél
Az összes többinél ugyan így lehet megcsinálni mint a kettő fentinél.
pl.: (+=)
```
class osztaly
{
public:
  	osztaly& operator+=(const osztaly& other)
	{
		a += other.a;
		return *this;
	}
}
```

pl.: (==)
```
class osztaly
{
public:
  	osztaly& operator==(const osztaly& other) const
	{
		return a==other.a;
	}
}
```

pl.: (<<)
```
class osztaly
{
public:
  	friend std::ostream& operator<<(std::ostream& os, const osztaly& other);
}
std::ostream& operator<<(std::ostream& os, const osztaly& other)
{
	os << "(" << other.a << ")";
	return os;
}
```

pl.: (>>)
```
class osztaly
{
public:
  	friend std::istream& operator>>(std::istream& ss, const osztaly& other);
}
std::istream& operator<<(std::istream& is, const osztaly& other)
{
	is >> other.a;
	return is;
}
```

#### Copy construktor
Az = jel is egy ilyenm, amit felül lehet írni.
```
class osztaly
{
public:
	osztaly(const osztaly& other) : mX(other.other) {}

	osztaly(const osztaly& other) = default; //alapértelmezetten működik

	osztaly(const osztaly& other) = delete; //nem lehet használni vagy ezt a konstrutort berakjuk a private hasonlót érünk el

	osztaly& operator=(const osztaly& other)
  	{
	  	if (this == &other) return *this;

	  	if (other.mHead == nullptr) return *this;
		//többi opció...

	  	return *this;
  	}
}
```
Érdemes fg paraméternél a memória helyet átadni, mert akkor, nem egy külön copy konstruktor fut le
pl.:
```
void f(osztaly& o)
{
//valami
}
```

## Generikus osztály létrehozása
A példában egy T tipusú tömb tárolót hozunk létre.
pl.:
### .cpp:
```
#include <algorithm>
#include <cstddef>
#include <initializer_list>

template<typename T>
class Osztaly
{
public:
	Osztaly() = default;
	Osztaly(const size_t size);
	Osztaly(const size_t size, const T& defaultValue);
	Osztaly(const std::initializer_list<T>& list); //{1, 3, 4 , 5} ez a lista
	Osztaly(const vector& other);
	~Osztaly();

	void operator=(const osztaly& other);
	T operator[](const size_t index) const;
	T& operator[](const size_t index);

	void push_back(const T& newValue);

private:
	T* mArray = nullptr;
	size_t mSize = 0; //Ehhez kell GET
	size_t mCapacity = 0; //Ehhez kell GET
}

template<typename T>
void Osztaly<T>::push_back(const T& newValue)
{
	if (mCapacity == mSize) {
		if (mCapacity == 0) {
			++mCapacity;
			mArray = new T[mCapacity];
		} else {
			mCapacity <<=1; // 2-vel szorzás
		}
	}
	mArray[mSize] = newValue;
	++mSize;
}

template<typename T>
void Osztaly<T>::operator=(const osztaly& other)
{
	if (this != &other)
	{
		delete[] mArray;
		
		mSize = other.mSize;
		mCapacity = other.mCapacity;

		mArray = new T[mSize];
		std::copay(other.mArray, other.mArray + mSize, mArray);
	}
}

template<typename T>
Osztaly<T>::Osztaly(const Osztaly& other)
	: mArray(new T[other.mSize])
	, mSize(other.mSize)
	, mCapacity(other.mCapacity)
{
	std::copay(other.mArray, other.mArray + mSize, mArray);
}

template<typename T>
Osztaly<T>::Osztaly(const std::initializer_list<T>& list);
	: mArray(new T[list.size()])
	, mSize(list.size())
	, mCapacity(mSize)
{
	std::copay(list.begin(), list.end(), mArray);
}

template<typename T>
Osztaly<T>::Osztaly(const size_t size)
	: mArray(new T[size])
	, mSize(size)
	, mCapacity(size)
{
}
template<typename T>
T Osztaly<T>::operator[](const size_t index)
{
	return mArrey[index];
}

template<typename T>
T Osztaly<T>::operator[](const size_t index) const
{
	return mArrey[index];
}

template<typename T>
Osztaly<T>::Osztaly(const size_t size, const T& defaultValue)
	: mArray(new T[size])
	, mSize(size)
	, mCapacity(size)
{
	std::fill(mArray, mArray + size, defaultValue);
}

template<typename T>
Osztaly<T>::~Osztaly()
{
	delete[] mArray;
}
```

## Iterátor kiegészítő osztály
pl.:
```
template<typename T>
class Osztaly
{
public:
	....
	
	class iterator
	{
	public:
		iterator(T* current);
		bool operator==(const iterator& other) const;
		bool operator!=(const iterator& other) const;
		iterator& operator++(); // prefix
		iterator operator++(int); // postfix
		T& operator*();
	private:
		t* mCurrent;
	};

	iterator begin();
	iterator end();

private:
	...
};

template<typename T>
osztaly<T>::iterator Osztaly<T>::iterator::operator++(int)
{
	T* temp = mCurrent;
	++mCurrent;
	return iterator(temp);
}

template<typename T>
T& Osztaly<T>::iterator::operator*()
{
	return *mCurrent;
}

template<typename T>
osztaly<T>::iterator& Osztaly<T>::iterator::operator++()
{
	++mCurrent;
	return *this;
}

template<typename T>
bool Osztaly<T>::iterator::operator!=(const iterator& other) const
{
	return !(*this == other);
}

template<typename T>
bool Osztaly<T>::iterator::operator!=(const iterator& other) const
{
	return !(*this == other);
}

template<typename T>
bool Osztaly<T>::iterator::operator==(const iterator& other) const
{
	return mCurrent == other.mCurrent;
}

template<typename T>
Osztaly<T>::iterator Osztaly<T>::begin()
{
	return iterator(mArray);
}

template<typename T>
Osztaly<T>::iterator Osztaly<T>::end()
{
	return iterator(mArray + mSize);
}

```

## Enum
pl.:
```
enum Color {
	Blue = 1,
	Red = 2,
	Green = 4,
	Yellow = 8
}

int main()
{
	Color c = Green;
}
```

Osztállyal:
.h:
```
#include <iostream>
#include <string>
#include <unordered_map>

class Color {
public:
	enum EColor {
		Blue,
		Red,
		Green,
		Yellow
	}

	Color(const EColor color);
	EColor get() const;
	operator std::string() const;
	friend std::istream& operator>>(std::istream& is, Color& rhs);
	bool operator==(const Color& rhs) const;

private:
	EColor mColor;
	static const std::unordered_map<EColor, std::string> eColorToString;
};

std::ostream& operator<<(std::ostream& os, const Color& rhs);
```

.cpp:
```
std::unordered_map<Color::EColor, std::string> Color::eColorToString = {
	{Blue, "Blue"}, //first, second
	{Red, "Red"},
	{Green, "Green"},
	{Yellow, "Yellow"}
};

Color::Color(const EColor color)
	: _color(color)
{
}

Color::EColor Color::get() const
{
	return _color;
}

bool Color::operator==(const Color& rhs) const
{
	return mColor == rhs;
}

Color::operator std::string() const
{
	/*switch (_color) {
		case Blue:
			return "Blue";
		case Red:
			return "Red";
		case Green:
			return "Green";
		case Yellow:
			return "Yellow";
	}*/

	std::undordered_map<Ecolor, std::string>::const_iterator it = eColorToString.find(_color);
	if (it != eColorToString.end()) //Van találat
	{
		return it->second;
	}
	return "";
}

std::istream& operator>>(std::istream& is, Color& rhs)
{
	std::string s;
	is >> s;
	for (std::undordered_map<Color::EColor, std::string>::const_iterator it = Color::eColorToString.begin(); it != Color::eColorToString.end(); ++it)
	{
		if (s == it->second)
		{
			rhs.mColor = it->first;
		}
	}
	return is;
}

std::ostream& operator<<(std::ostream& os, const Color& rhs)
{
	os << std::string(rhs);
	return os;
}
```

## Input/output stream-ek

### Egész double ki írása
```
#include <iostream>
#include <iomanip>

int main()
{
	double d = -123.456789;

	std::cout << std::setprecision(8) << d << std::endl; //8 hosszúságig kiírja
	std::cout << std::fixed << std::setprecision(15) << d << std::endl; //pontosan írja ki
	std::cout << std::scientific << std::setprecision(8) << d << std::endl; // tizedes pont mögött lesz minden és lesz majd 10-es szorzás
	std::cout << std::setw(20) << std::left << "Balra igazítva" << std::endl; //20 karakter és balra igazítva
	std::cout << std::setw(20) << std::right << "Jobbra igazítva" << std::endl;
	std::cout << std::setw(20) << std::internal << d << std::endl; //- és a szám külön van
	std::cout << std::setw(20) << std::internal << std::setfill('*') << d << std::endl; //csillaggal tölti ki a maradék helyet.

	std:: cout << std::hex << d << std::endl; //hexadecimálisan írja ki a számot
}
```

### Bekérés
```
#include <iostream>
#include <iomanip>

int main()
{
	std::string s;
	std::getline(std::cin, s);
	std::getline(std::cin, s, 'd'); //csak a d-ig olvassa be

	int a, b, c;
	std::cin >> a >> b >> c;
}
```

### kiírás fájlba
```
#include <iostream>
#include <iomanip>
#include <fstream>

int main()
{
	std::ofstream outputFile("output.txt", std::ios::app); //nem muszály az app-os, ezzel meg marad a régi is, ha van
	std::string s;
	std::getline(std::cin, s);
	while (s != "")
	{
		outputFile << s << std::endl;
		std::getline(std::cin, s);
	}
	outputFile.close();
}
```

Ide tartoznak az előzőkben nézett console-ra kiírások.
Pl.:
```
//Osztály

std::ostream& operator<<(std::ostream& os, const OsztalyNeve& rhs)
{
	os << std::string(rhs); //Osztály szerinti érték amit ki szeretnénk írni
	return os;
}
```

### Bekérés fájlból
pl.:
```
#include <iostream>
#include <iomanip>
#include <fstream>

int main()
{
	std::ifstream inputFile("input.txt");
	if (inputFile.is_open())
	{
		while (!inputFile.eof())
		{
			std::string s;
			std::getline(inputFile, s);
		}
	}

	inputFile.close();
}
```

### ostringstream
pl.:
```
#include <iostream>
#include <iomanip>
#include <fstream>
#include <sstream>

int main()
{
	std::ostringstream oss;
	oss << "hello" << 100 << std::fixed << 1e-6;

	std::string s = oss.str();
	std::cout << s << std::endl;

	std::istringstream iss("Ez egy mondat.");

	std::string s;
	iss>> s; //csak az első szó lesz ott.
}
```
## Stack/heap, változók a heap-en
### Stack
Amikor egy változót hozunk létre alapból a stacken vannak. A main beli változók a stack alján és a main feletti methodús változok pedig a stacken a main változói felett lesznek.

### Heap
Heap-en belül valahol létrejön a változó, de a hivatkozást úgy lehet megoldani, hogy a Stack-en létrehozunk egy pointer változót. Például:
```
int main()
{
	int* a = new int(5);
	delete a;
}
```
A "delete a"-val lehet a Heap-ről törölni az adatot, de az "a" Stack-en megmarad a mutatója.

```
int main()
{
	int* b = new int[10];
	delete b; //Ez csak az első elemet törli
	delete[] b; //Ez az összeset
}
```

## Smart pointerek
### Okos pointer:
```
int main()
{
	std::unique_ptr<int> p1 = std::make_unique<int>(4);

	std::unique_ptr<int> p2(std::move(p1));
}
```

### Megosztott pointer
Lelehet kérdenzi, hogy hányan mutatnak rá.
```
	std::shared_ptr<int> p1 = std::make_shared<int>(1);
	std::cout << p1.use_count() << std::endl; //kimenet: 1
	std::shared_ptr<int> p2(p1);
	std::cout << p2.use_count() << std::endl; //kimenet: 2
	std::cout << p1.use_count() << std::endl; //kimenet: 2

	{
		std::shared_ptr<int> p3(p1);
		std::cout << p1.use_count() << std::endl; //kimenet: 3
	} //p3 destructor

	std::cout << p1.use_count() << std::endl; //kimenet: 2
```

### Öröklődés
Ami class1-ben van, az class2-ben is lesz, de csak a publicus adatagok.
```
class class1
{
public:
	class1(const int a) : ma(a) {}
	virtual ~Employee() {}
	
	virtual std::string toString() const
	{
		return std::to_string(ma);
	}
private:
	int ma;
}

class class2 : public class1
{
public:
	class2(const int a) : class1(a) {}
	std::string toString() const override
	{
		return class1::toString() + "!";
	}
}

int main()
{
	class2 c2;
	class1 c1 = c2; //csak a class1 adatokat veszi át.

	class1* c3 = new class2;
	delete c3;

	class2* c4 = dynamic_cast<class2*>(c1.get());

	
}
```

### Interface
```
class IInterface
{
public:
	virtual ~IInterface() = default; //Fontos, hogy működjön a polimorfizmus
	virtual void method() = 0; //pure virtual
}

class Out : public IInterface
{
public:
	void method() override;
}
```

### Algoritmusok


