---
title: "Aliasy i definicje typów (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: typedef_cpp
dev_langs: C++
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8946c87c18e1781f95df7a91e8cc4fa0eba02158
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="aliases-and-typedefs-c"></a>Aliasy i definicje typów (C++)
Można użyć *Deklaracja aliasu* Aby zadeklarować nazwa ma być używana jako synonim wcześniej zadeklarowanego typu. (Ten mechanizm jest również nazywany nieformalnego *alias typu*). Ten mechanizm również służy do tworzenia *szablonu aliasu*, które mogą być szczególnie przydatne w przypadku niestandardowych allocators —.  
  
## <a name="syntax"></a>Składnia  
  
```  
using identifier = type;  
```  
  
## <a name="remarks"></a>Uwagi  
 `identifier`  
 Nazwa aliasu.  
  
 `type`  
 Identyfikator typu tworzonego alias.  
  
 Alias nie wprowadza nowych typów i nie może zmienić znaczenie istniejącej nazwy typu.  
  
 Najprostsza forma alias jest odpowiednikiem `typedef` mechanizmu z języka C ++ 03:  
  
```cpp  
// C++11  
using counter = long;  
  
// C++03 equivalent:  
// typedef long counter;  
```  
  
 Oba te umożliwiają tworzenie zmiennych typu "licznika". Coś lepszym rozwiązaniem byłoby alias typu podobny do tego dla `std::ios_base::fmtflags`:  
  
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
  
 Aliasy również współpracować z wskaźników funkcji, ale są bardziej czytelny niż równoważne typedef:  
  
```cpp  
// C++11  
using func = void(*)(int);  
  
// C++03 equivalent:  
// typedef void (*func)(int);  
  
// func can be assigned to a function pointer value  
void actual_function(int arg) { /* some code */ }  
func fptr = &actual_function;  
  
```  
  
 Ograniczenie `typedef` mechanizm jest, że ta funkcja nie działa z szablonami. Jednak składni typu aliasu w języku C ++ 11 umożliwia tworzenie szablonów alias:  
  
```cpp  
template<typename T> using ptr = T*;   
  
// the name 'ptr<T>' is now an alias for pointer to T  
ptr<int> ptr_int;  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać szablonu aliasu z niestandardowego zarządcę — w takim przypadku całkowitą wektorów typu. Można użyć dowolnego typu dla `int` Aby utworzyć alias wygodny spowoduje ukrycie parametru złożonych wymieniono w kodzie funkcjonalności głównych. Używając programu przydzielania niestandardowych w całym kodzie można poprawić czytelność i zmniejszyć ryzyko wprowadzenia błędy spowodowane literówki.  
  
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
 A `typedef` deklaracji wprowadza nazwę zakresu, staje się synonim dla typu określonego przez *deklaracji typu* część deklaracji.  
  
 Deklaracji typedef można używać do tworzenia krótszych, bardziej znaczących nazw typów już zdefiniowanych przez język lub zdefiniowanych ręcznie. Nazwy zdefiniowane przez typedef pozwalają na hermetyzację szczegółów implementacji, które mogą się zmieniać.  
  
 Contrast do **klasy**, `struct`, **Unii**, i `enum` deklaracje, `typedef` deklaracje nie znajdą się nowe typy — one wprowadzenia nowych nazw istniejących typów.  
  
 Zadeklarowane za pomocą nazwy `typedef` zajmować tego samego obszaru nazw jako innych identyfikatorów (z wyjątkiem etykiety instrukcji). W związku z tym nie mogą używać tego samego identyfikatora jako nazwę poprzednio zadeklarowana z wyjątkiem w deklaracji typu klasy. Rozważmy następujący przykład:  
  
```  
// typedef_names1.cpp  
// C2377 expected  
typedef unsigned long UL;   // Declare a typedef name, UL.  
int UL;                     // C2377: redefined.  
```  
  
 Reguły ukrywanie nazwy, które odnoszą się do innych identyfikatorów również decydować widoczność deklarowany przy użyciu nazwy `typedef`. W związku z tym przykładzie jest dozwolony w języku C++:  
  
```  
// typedef_names2.cpp  
typedef unsigned long UL;   // Declare a typedef name, UL  
int main()  
{  
   unsigned int UL;   // Redeclaration hides typedef name  
}  
  
// typedef UL back in scope  
```  
 
  
```  
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
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Aby ponownie użyć nazwy `FlagType` dla identyfikatora, elementu struktury lub unii musi zostać dostarczony typ:  
  
```  
const int FlagType;  // Type specifier required  
```  
  
 Nie wystarczy powiedzieć  
  
```  
const FlagType;      // Incomplete specification  
```  
  
 ponieważ `FlagType` uważa się za część typu, a nie identyfikatora, który jest ponownie deklarowany. Taką deklarację uważa się za niedozwoloną, tak jak  
  
```  
int;  // Illegal declaration   
```  
  
 Można zadeklarować dowolny typ z typedef, w tym wskaźnik, funkcję i typy tablic. Można zadeklarować nazwę typedef wskaźnika na strukturę lub unię przed zdefiniowaniem struktury lub unii, tak długo jak definicja ma taką samą widoczność jak deklaracja.  
  
### <a name="examples"></a>Przykłady  
 Jednym z zastosowań deklaracji `typedef` jest sprawienie, że deklaracje staną się bardziej jednolite i zwarte. Na przykład:  
  
```cpp  
typedef char CHAR;          // Character type.  
typedef CHAR * PSTR;        // Pointer to a string (char *).  
PSTR strchr( PSTR source, CHAR target );  
typedef unsigned long ulong;  
ulong ul;     // Equivalent to "unsigned long ul;"  
```  
  
 Aby użyć `typedef` do określania typów podstawowych i pochodnych w tej samej deklaracji, można rozdzielić deklaratory przecinkami. Na przykład:  
  
```  
typedef char CHAR, *PSTR;  
```  
  
 W następującym przykładzie podano typ `DRAWF` dla funkcji niezwracającej wartości i przyjmującej dwa argumenty typu int:  
  
```  
typedef void DRAWF( int, int );  
```  
  
 Po powyższym wyrażeniu `typedef`, deklaracja  
  
```  
DRAWF box;   
```  
  
 byłaby równoważna z deklaracją  
  
```  
void box( int, int );  
```  
  
 `typedef` często łączy się z `struct` aby zadeklarować i nazwać typy zdefiniowane przez użytkownika:  
  
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
 `typedef` Deklaracji można ponownie zadeklarować tej samej nazwie, aby odwołać się do tego samego typu. Na przykład:  
  
```cpp  
// FILE1.H  
typedef char CHAR;  
  
// FILE2.H  
typedef char CHAR;  
  
// PROG.CPP  
#include "file1.h"  
#include "file2.h"   // OK  
```  
  
 Program programu. CPP zawiera dwa pliki nagłówkowe, które zawierają `typedef` deklaracje dla nazwy `CHAR`. Tak długo, jak obie deklaracje odwołują się do tego samego typu, takiego ponowna deklaracja jest dopuszczalne.  
  
 A `typedef` nie można ponownie zdefiniować nazwę, który został wcześniej zadeklarowany jako innego typu. W związku z tym jeśli Plik2. Zawiera H  
  
```cpp  
// FILE2.H  
typedef int CHAR;     // Error  
```  
  
 Kompilator generuje błąd z powodu próby ponownie zadeklarować nazwę `CHAR` do odwoływania się do innego typu. Spowoduje to rozszerzenie do konstrukcji takich jak:  
  
```cpp  
typedef char CHAR;  
typedef CHAR CHAR;      // OK: redeclared as same type  
  
typedef union REGS      // OK: name REGS redeclared  
{                       //  by typedef name with the  
    struct wordregs x;  //  same meaning.  
    struct byteregs h;  
} REGS;  
```  
  
### <a name="typedefs-in-c-vs-c"></a>definicje typów w programie C++ vs. C  
 Użycie `typedef` specyfikator z typami klasy jest obsługiwany w dużej mierze z powodu deklarowanie struktury bez nazwy w praktyce ANSI C `typedef` deklaracji. Na przykład wielu programistów C należy użyć następujących czynności:  
  
```cpp  
// typedef_with_class_types1.cpp  
// compile with: /c  
typedef struct {   // Declare an unnamed structure and give it the  
                   // typedef name POINT.  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 Zaletą takiego oświadczenia jest możliwość deklaracje, takich jak:  
  
```  
POINT ptOrigin;  
```  
  
 Zamiast:  
  
```  
struct point_t ptOrigin;  
```  
  
 W języku C++ różnica między `typedef` nazwy i typy rzeczywistych (zadeklarowana z **klasy**, `struct`, **Unii**, i `enum` słowa kluczowe) różni się więcej. Mimo że deklarowanie bez struktury w praktyce C `typedef` instrukcji nadal działa, zapewnia nie korzyści notational co w C.  
  
```cpp  
// typedef_with_class_types2.cpp  
// compile with: /c /W1  
typedef struct {  
   int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 Powyższy przykład deklaruje klasę o nazwie `POINT` za pomocą nazwy klasy `typedef` składni. `POINT`jest traktowany jako nazwy klasy; jednak następujące ograniczenia dotyczące nazw wprowadzonych w ten sposób:  
  
-   Nazwa (synonim) nie może występować po **klasy**, `struct`, lub **Unii** prefiks.  
  
-   Nazwa nie może służyć jako nazwy konstruktora lub destruktora wewnątrz deklaracji klasy.  
  
 Podsumowując ta składnia nie zapewnia mechanizm dziedziczenia, utworzenia lub zniszczenia.  
