---
title: Aliasy i definicje typów (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 155f1868123514dfec89ab448ef22f2da225c4d3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521475"
---
# <a name="aliases-and-typedefs-c"></a>Aliasy i definicje typów (C++)

Możesz użyć *Deklaracja aliasu* do deklarowania Nazwa do użycia jako synonim wcześniej zadeklarowanym typem. (Ten mechanizm jest również nazywane nieformalnie *alias typu*). Ten mechanizm również służy do tworzenia *szablonu aliasu*, które mogą być szczególnie przydatne dla niestandardowych alokatorów.

## <a name="syntax"></a>Składnia

```
using identifier = type;
```

## <a name="remarks"></a>Uwagi

*Identyfikator*<br/>
Nazwa aliasu.

*Typ*<br/>
Identyfikator typu tworzonej alias.

Alias nie wprowadza nowy typ i nie może zmienić znaczenie istniejącej nazwy typu.

Najprostsza forma aliasu jest odpowiednikiem **typedef** mechanizm z C ++ 03:

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

Oba te umożliwiają tworzenie zmiennych typu "counter". Coś, co jest bardziej użyteczny, byłoby alias typu, podobny do tego dla `std::ios_base::fmtflags`:

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

Aliasy również pracować ze wskaźnikami funkcji, ale są bardziej czytelne niż równoważna typedef:

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

To ograniczenie **typedef** mechanizm jest, to nie zadziała za pomocą szablonów. Jednak w składni aliasu typu C ++ 11 umożliwia tworzenie szablony alias:

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób używania szablonu aliasu za pomocą niestandardowego zarządcy — w tym przypadku całkowitą vector typu. Można użyć dowolnego typu dla **int** Aby utworzyć alias wygodne do ukrywania złożonych parametru wyświetla w kodzie funkcjonalności głównych. Za pomocą niestandardowego zarządcy w całym kodzie można zwiększyć czytelność i zmniejszyć ryzyko wprowadzenia błędy spowodowane przez błędy pisowni.

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

A **typedef** deklaracji wprowadza nazwę, która w swoim zakresie staje się synonimem typu podanego przez *deklaracji typu* część deklaracji.

Deklaracji typedef można używać do tworzenia krótszych, bardziej znaczących nazw typów już zdefiniowanych przez język lub zdefiniowanych ręcznie. Nazwy zdefiniowane przez typedef pozwalają na hermetyzację szczegółów implementacji, które mogą się zmieniać.

W przeciwieństwie do **klasy**, **struktury**, **Unii**, i **wyliczenia** deklaracji, **typedef** nie wprowadzają nowych typów-wprowadzają one nowe nazwy istniejących typów.

Nazwy zadeklarowane za pomocą **typedef** zajmować tej samej przestrzeni nazw jako inne identyfikatory (z wyjątkiem etykiet instrukcji). W związku z tym nie używają tego samego identyfikatora, jak poprzednio zadeklarowany nazwa, z wyjątkiem w deklaracji typu klasy. Rozważmy następujący przykład:

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

Reguły ukrywaniem nazwy, które odnoszą się do innych identyfikatorów również decydować o widoczności nazwy zadeklarowane za pomocą **typedef**. W związku z tym poniższy przykład jest niedozwolony w języku C++:

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

Jednym z zastosowań **typedef** oświadczeń jest, że deklaracje staną się bardziej jednolite i zwarte. Na przykład:

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

Aby użyć **typedef** do określania typów podstawowych i pochodnych w tej samej deklaracji, można rozdzielić deklaratory przecinkami. Na przykład:

```cpp
typedef char CHAR, *PSTR;
```

W następującym przykładzie podano typ `DRAWF` dla funkcji niezwracającej wartości i przyjmującej dwa argumenty typu int:

```cpp
typedef void DRAWF( int, int );
```

Po powyższym wyrażeniu **typedef** , deklaracja

```cpp
DRAWF box;
```

byłaby równoważna z deklaracją

```cpp
void box( int, int );
```

**Element TypeDef** często łączy się z **struktury** Aby zadeklarować i nazwać typy zdefiniowane przez użytkownika:

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

### <a name="re-declaration-of-typedefs"></a>Ponowna deklaracja definicje typów

**Typedef** deklaracja może służyć do ponownego zadeklarowania takiej samej nazwie, aby odwołać się do tego samego typu. Na przykład:

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

Program *programu. CPP* zawiera dwa pliki nagłówkowe, które zawierają **typedef** deklaracje dla nazwy `CHAR`. Tak długo, jak obie deklaracje odwoływać się do tego samego typu, takiego ponowna deklaracja jest dopuszczalne.

A **typedef** nie można ponownie zdefiniować nazwę, który został wcześniej zadeklarowany jako innego typu. W związku z tym jeśli *Plik2. H* zawiera

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

Kompilator generuje błąd z powodu można ponownie zadeklarować nazwy `CHAR` do odwoływania się do innego typu. Spowoduje to rozszerzenie do konstrukcji takich jak:

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>definicje typów w programie vs języka C++. C

Korzystanie z **typedef** specyfikator z typami klasy jest obsługiwany w dużej mierze ze względu na ANSI C praktyką deklarowanie struktury nienazwane w **typedef** deklaracji. Na przykład wielu programistów C, użyj następujących czynności:

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

Zaletą takiego oświadczenia jest umożliwienie deklaracji, takich jak:

```cpp
POINT ptOrigin;
```

Zamiast:

```cpp
struct point_t ptOrigin;
```

W języku C++, różnica między **typedef** nazwy i typy rzeczywiste (zadeklarowane za pomocą **klasy**, **struktury**, **Unii**i **wyliczenia** słowa kluczowe) różni się więcej. Mimo że C praktyką deklarowanie pustego struktury w **typedef** instrukcji nadal działa, zapewnia nie korzyści notational co w C.

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

Poprzedni przykład deklaruje klasę o nazwie `POINT` przy użyciu nazwy klasy **typedef** składni. `POINT` jest traktowany jako nazwy klasy; jednak następujące ograniczenia dotyczą nazwy wprowadzone w ten sposób:

- Nazwa (synonim) nie może występować po **klasy**, **struktury**, lub **Unii** prefiks.

- Nazwa nie może służyć jako konstruktor lub destruktor nazwy w obrębie deklaracji klasy.

Podsumowując ta składnia nie zapewnia mechanizm dziedziczenia, utworzenia lub zniszczenia.