---
title: Klasy magazynu (C++)
description: W języku C++ słowa kluczowe statyczne, extern i thread_local określają okres istnienia, powiązania i lokalizację pamięci zmiennej lub funkcji.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365345"
---
# <a name="storage-classes"></a>Klasy magazynu

*Klasa magazynu* w kontekście deklaracji zmiennych C++ jest specyfikatorem typu, który reguluje okres istnienia, powiązania i lokalizacji pamięci obiektów. Dany obiekt może mieć tylko jedną klasę magazynu. Zmienne zdefiniowane w bloku mają automatyczną pamięć masową, chyba że określono inaczej przy użyciu **specyfikatorów extern,** **static**lub **thread_local.** Automatyczne obiekty i zmienne nie mają powiązania; nie są one widoczne dla kodu poza blokiem. Pamięć jest przydzielana dla nich automatycznie, gdy wykonanie wchodzi do bloku i de-przydzielone po zamknięciu bloku.

**Uwagi**

1. [Modyfikowalne](../cpp/mutable-data-members-cpp.md) słowo kluczowe może być uznane za specyfikator klasy magazynu. Jednak jest ono dostępne tylko na liście składowych definicji klasy.

1. **Visual Studio 2010 i nowsze:** Auto **auto** słowo kluczowe nie jest już specyfikatorem klasy magazynu języka C++, a słowo kluczowe **register** jest przestarzałe. **Visual Studio 2017 w wersji 15.7 i nowszej:** (dostępne z [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Słowo kluczowe **register** jest usuwany z języka C++.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>Statyczne

**Statyczne** słowo kluczowe może służyć do deklarowania zmiennych i funkcji w zakresie globalnym, zakres obszaru nazw i zakres klasy. Zmienne statyczne można również zadeklarować w zakresie lokalnym.

Statyczny czas trwania oznacza, że obiekt lub zmienna jest przydzielana po uruchomieniu programu i jest przydzielana po zakończeniu programu. Powiązanie zewnętrzne oznacza, że nazwa zmiennej jest widoczna spoza pliku, w którym zmienna jest zadeklarowana. Z drugiej strony wewnętrzna powiązanie oznacza, że nazwa nie jest widoczna poza plikiem, w którym zmienna jest zadeklarowana. Domyślnie obiekt lub zmienna zdefiniowana w globalnej przestrzeni nazw ma statyczny czas trwania i powiązanie zewnętrzne. **Statyczne** słowo kluczowe może być używane w następujących sytuacjach.

1. Podczas deklarowania zmiennej lub funkcji w zakresie pliku (zakres globalny i/lub obszar nazw), **statyczne** słowo kluczowe określa, że zmienna lub funkcja ma wewnętrzne powiązanie. Podczas deklarowania zmiennej zmienna ma statyczny czas trwania, a kompilator inicjuje ją do 0, chyba że określisz inną wartość.

1. Podczas deklarowania zmiennej w funkcji **statyczne** słowo kluczowe określa, że zmienna zachowuje swój stan między wywołaniami tej funkcji.

1. Podczas deklarowania elementu członkowskiego danych w deklaracji klasy **statyczne** słowo kluczowe określa, że jedna kopia elementu członkowskiego jest współużytkowana przez wszystkie wystąpienia klasy. Element członkowski danych statycznych musi być zdefiniowany w zakresie pliku. Element członkowski danych integralną, który deklarujesz jako **konsty statyczne** może mieć inicjatora.

1. Podczas deklarowania funkcji elementu członkowskiego w deklaracji klasy **statyczne** słowo kluczowe określa, że funkcja jest współużytkowana przez wszystkie wystąpienia klasy. Funkcja statycznego elementu członkowskiego nie może uzyskać dostępu do elementu członkowskiego wystąpienia, ponieważ funkcja nie ma niejawnego **tego wskaźnika.** Aby uzyskać dostęp do elementu członkowskiego wystąpienia, zadeklaruj funkcję za pomocą parametru, który jest wskaźnikiem wystąpienia lub odwołaniem.

1. Nie można zadeklarować członków unii jako statyczne. Jednak globalnie zadeklarowana anonimowa unia musi być jawnie zadeklarowana **jako statyczna**.

W tym przykładzie pokazano, jak zmienna zadeklarowana **statyczna** w funkcji zachowuje swój stan między wywołaniami tej funkcji.

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

W tym przykładzie pokazano użycie **statyczne** w klasie.

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

W tym przykładzie pokazano zmienną lokalną zadeklarowaną **jako statyczną** w funkcji elementu członkowskiego. Zmienna statyczna jest dostępna dla całego programu; wszystkie wystąpienia typu współużytkują tę samą kopię zmiennej statycznej.

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

Począwszy od C ++ 11, statyczne inicjowanie zmiennej lokalnej jest gwarantowane jako bezpieczne dla wątków. Ta funkcja jest czasami nazywana *magiczną statykami.* Jednak w aplikacji wielowątkowej wszystkie kolejne przydziały muszą być zsynchronizowane. Funkcja inicjowania statycznego bezpieczeństwa wątków można wyłączyć za pomocą [/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) flagi, aby uniknąć podejmowania zależności od CRT.

## <a name="extern"></a><a name="extern"></a>Extern

Obiekty i zmienne zadeklarowane jako **extern** deklarują obiekt zdefiniowany w innej jednostce tłumaczenia lub w otaczającym go zakresie jako posiadający powiązania zewnętrzne. Aby uzyskać więcej informacji, zobacz [jednostki extern](extern-cpp.md) i [translation oraz powiązanie](program-and-linkage-cpp.md).

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C++11)

Zmienna zadeklarowana z **specyfikatorem thread_local** jest dostępna tylko w wątku, na którym jest tworzona. Zmienna jest tworzona podczas tworzenia wątku i niszczone, gdy wątek jest niszczony. Każdy wątek ma własną kopię zmiennej. W systemie Windows **thread_local** jest funkcjonalnie równoważne atrybutowi [__declspec(wątek)](../cpp/thread.md) specyficznym dla firmy Microsoft.

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

Co należy zwrócić uwagę na specyfikator **thread_local:**

- Dynamicznie inicjowane zmienne lokalne wątku w bibliotekach DLL mogą nie być poprawnie zainicjowane we wszystkich wątkach wywołujących. Aby uzyskać więcej informacji, zobacz [wątek](thread.md).

- Specyfikator **thread_local** może być łączony ze **statycznym** lub **extern**.

- Można zastosować **thread_local** tylko do deklaracji danych i definicji; **thread_local** nie można używać w deklaracjach funkcji lub definicjach.

- Można określić **thread_local** tylko na elementach danych o statycznym czasie przechowywania. Obejmuje to globalne obiekty danych (zarówno **statyczne,** jak i **extern),** lokalne obiekty statyczne i statyczne elementy członkowskie danych klas. Każda zmienna lokalna zadeklarowana **thread_local** jest niejawnie statyczna, jeśli nie podano żadnej innej klasy magazynu; innymi słowy, w zakresie bloku **thread_local** `thread_local static`jest odpowiednikiem .

- Należy określić **thread_local** dla deklaracji i definicji obiektu lokalnego wątku, czy deklaracja i definicja występują w tym samym pliku lub oddzielnych plików.

W systemie Windows **thread_local** jest funkcjonalnie równoważne [__declspec(thread),](../cpp/thread.md) z tą różnicą, że **__declspec(wątek)** mogą być stosowane do definicji typu i jest prawidłowy w kodzie C. Jeśli to możliwe, należy użyć **thread_local,** ponieważ jest częścią standardu C++ i dlatego jest bardziej przenośny.

## <a name="register"></a><a name="register"></a>Zarejestrować

**Visual Studio 2017 w wersji 15.3 i nowszej** (dostępne z [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Słowo kluczowe **register** nie jest już obsługiwaną klasą magazynu. Słowo kluczowe jest nadal zarezerwowane w standardzie do wykorzystania w przyszłości.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Przykład: automatyczne inicjowanie statyczne a statyczne

Lokalny obiekt automatyczny lub zmienna jest inicjowany za każdym razem, gdy przepływ kontroli osiągnie swoją definicję. Lokalny obiekt statyczny lub zmienna jest inicjowany po raz pierwszy przepływ kontroli osiągnie swoją definicję.

Rozważmy poniższy przykład, który definiuje klasę, która rejestruje inicjowanie i `I1` `I2`niszczenie `I3`obiektów, a następnie definiuje trzy obiekty, , i:

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

W tym przykładzie pokazano, `I1` `I2`jak `I3` i kiedy obiekty , i są inicjowane i kiedy są niszczone.

Istnieje kilka punktów, na które należy zwrócić uwagę na temat programu:

- Po `I1` pierwsze `I2` i są automatycznie niszczone, gdy przepływ kontroli wychodzi z bloku, w którym są zdefiniowane.

- Po drugie, w języku C++ nie jest konieczne deklarowanie obiektów lub zmiennych na początku bloku. Ponadto obiekty te są inicjowane tylko wtedy, gdy przepływ kontroli osiągnie ich definicje. `I2` (i `I3` są przykładami takich definicji).) Dane wyjściowe pokazuje dokładnie, kiedy są one inicjowane.

- Na koniec statyczne zmienne `I3` lokalne, takie jak zachować swoje wartości na czas trwania programu, ale są niszczone w miarę zakończenia programu.

## <a name="see-also"></a>Zobacz też

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)
