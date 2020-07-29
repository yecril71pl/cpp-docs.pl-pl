---
title: Aliasy i definicje typów (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 6054b7119614d9325bd099dd39b8aa1365d97ed7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227676"
---
# <a name="aliases-and-typedefs-c"></a>Aliasy i definicje typów (C++)

Można użyć *deklaracji aliasu* , aby zadeklarować nazwę do użycia jako synonim dla poprzednio zadeklarowanego typu. (Ten mechanizm jest również określany jako *alias typu*). Za pomocą tego mechanizmu można także utworzyć *szablon aliasu*, który może być szczególnie przydatny w przypadku niestandardowych przypisywania.

## <a name="syntax"></a>Składnia

```
using identifier = type;
```

## <a name="remarks"></a>Uwagi

*identyfikatora*<br/>
Nazwa aliasu.

*Wprowadź*<br/>
Identyfikator typu, dla którego tworzysz alias.

Alias nie wprowadza nowego typu i nie może zmienić znaczenia istniejącej nazwy typu.

Najprostsza forma aliasu jest równoważna **`typedef`** z mechanizmem z c++ 03:

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

Oba te metody umożliwiają tworzenie zmiennych typu "Counter". Coś bardziej przydatnego będzie alias typu podobny do tego `std::ios_base::fmtflags` :

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

Aliasy współdziałają także ze wskaźnikami funkcji, ale są znacznie bardziej czytelne niż równoważny element typedef:

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

Ograniczenie **`typedef`** mechanizmu polega na tym, że nie działa z szablonami. Jednak składnia aliasu typu w języku C++ 11 umożliwia tworzenie szablonów aliasów:

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia szablonu aliasu z alokatorem niestandardowym — w tym przypadku typu wektora liczb całkowitych. Można zastąpić dowolny typ dla **`int`** , aby utworzyć wygodny alias do ukrycia złożonych list parametrów w głównym kodzie funkcjonalnym. Korzystając z niestandardowego alokatora w całym kodzie, można zwiększyć czytelność i zmniejszyć ryzyko wprowadzenia usterek spowodowanych literówkami.

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>Typedefs

**`typedef`** Deklaracja wprowadza nazwę, która w swoim zakresie jest synonimem dla typu wskazanego przez część deklaracji *typu* deklaracji.

Deklaracji typedef można używać do tworzenia krótszych, bardziej znaczących nazw typów już zdefiniowanych przez język lub zdefiniowanych ręcznie. Nazwy zdefiniowane przez typedef pozwalają na hermetyzację szczegółów implementacji, które mogą się zmieniać.

W przeciwieństwie do **`class`** **`struct`** deklaracji,, **`union`** i **`enum`** , **`typedef`** deklaracje nie wprowadzają nowych typów — wprowadzają nowe nazwy dla istniejących typów.

Nazwy zadeklarowane przy użyciu **`typedef`** zajmują tę samą przestrzeń nazw co inne identyfikatory (oprócz etykiet instrukcji). W związku z tym, nie mogą używać tego samego identyfikatora jako nazwy zadeklarowanej wcześniej, z wyjątkiem deklaracji typu klasy. Rozpatrzmy następujący przykład:

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

Reguły ukrywania nazw, które odnoszą się do innych identyfikatorów, również określają widoczność nazw zadeklarowanych za pomocą **`typedef`** . W związku z tym Poniższy przykład jest dozwolony w języku C++:

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

Podczas deklarowania identyfikatora o zakresie lokalnym o tej samej nazwie co element typedef lub podczas deklarowania elementu struktury lub unii w tym samym zakresie lub w zakresie wewnętrznym, należy określić specyfikator typu. Na przykład:

```cpp
typedef char FlagType;
const FlagType x;
```

Aby ponownie użyć nazwy `FlagType` dla identyfikatora, elementu struktury lub unii musi zostać dostarczony typ:

```cpp
const int FlagType;  // Type specifier required
```

Nie wystarczy powiedzieć

```cpp
const FlagType;      // Incomplete specification
```

ponieważ `FlagType` uważa się za część typu, a nie identyfikatora, który jest ponownie deklarowany. Taką deklarację uważa się za niedozwoloną, tak jak

```cpp
int;  // Illegal declaration
```

Można zadeklarować dowolny typ z typedef, w tym wskaźnik, funkcję i typy tablic. Można zadeklarować nazwę typedef wskaźnika na strukturę lub unię przed zdefiniowaniem struktury lub unii, tak długo jak definicja ma taką samą widoczność jak deklaracja.

### <a name="examples"></a>Przykłady

Jednym z nich **`typedef`** jest użycie deklaracji do ujednolicenia i kompaktowania deklaracji. Na przykład:

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

Aby użyć **`typedef`** do określenia typów podstawowych i pochodnych w tej samej deklaracji, można oddzielić Deklaratory przecinkami. Na przykład:

```cpp
typedef char CHAR, *PSTR;
```

W następującym przykładzie podano typ `DRAWF` dla funkcji niezwracającej wartości i przyjmującej dwa argumenty typu int:

```cpp
typedef void DRAWF( int, int );
```

Po powyższej **`typedef`** instrukcji deklaracja

```cpp
DRAWF box;
```

byłaby równoważna z deklaracją

```cpp
void box( int, int );
```

**`typedef`** jest często połączony z **`struct`** do deklarowania i nazwy typów zdefiniowanych przez użytkownika:

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>Ponowna deklaracja elementów typedef

Deklaracja może służyć do ponownej deklaracji tej **`typedef`** samej nazwy, aby odwołać się do tego samego typu. Na przykład:

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

Program *. CPP* zawiera dwa pliki nagłówkowe, które zawierają **`typedef`** deklaracje dla nazwy `CHAR` . Tak długo, jak obie deklaracje odwołują się do tego samego typu, taka ponowna deklaracja jest akceptowalna.

**`typedef`** Nie można ponownie zdefiniować nazwy, która została wcześniej zadeklarowana jako inny typ. W związku z tym, jeśli *plik2. H* zawiera

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

Kompilator zgłasza błąd, ponieważ próbuje ponownie zadeklarować nazwę, `CHAR` Aby odwołać się do innego typu. Rozszerza to konstrukcje, takie jak:

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>definicje typów w języku C++ a C

Użycie **`typedef`** specyfikatora z typami klas jest w dużym stopniu obsługiwane ze względu na to, że metoda ANSI C deklaruje nienazwane struktury w **`typedef`** deklaracjach. Na przykład wielu programistów języka C korzysta z następujących czynności:

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

Zaletą takich deklaracji jest umożliwienie deklaracji takich jak:

```cpp
POINT ptOrigin;
```

Zamiast:

```cpp
struct point_t ptOrigin;
```

W języku C++ różnica między **`typedef`** nazwami i typami rzeczywistymi (zadeklarowane za pomocą **`class`** **`struct`** **`union`** **`enum`** słowa kluczowego,, i) jest bardziej odrębna. Mimo że zwyczajowa Metoda deklarująca strukturę pustego w **`typedef`** instrukcji nadal działa, nie zapewnia żadnych korzyści z notacji, tak jak w C.

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

Powyższy przykład deklaruje klasę o nazwie `POINT` przy użyciu nienazwanej **`typedef`** składni klasy. `POINT`jest traktowany jako nazwa klasy; jednak następujące ograniczenia dotyczą nazw wprowadzonych w ten sposób:

- Nazwa (synonim) nie może występować po **`class`** **`struct`** prefiksie,, ani **`union`** .

- Nazwy nie można użyć jako nazwy konstruktora lub destruktora w deklaracji klasy.

Podsumowując, ta składnia nie zapewnia żadnego mechanizmu dziedziczenia, konstruowania lub niszczenia.
