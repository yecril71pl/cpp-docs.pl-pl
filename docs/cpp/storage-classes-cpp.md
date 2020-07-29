---
title: Klasy magazynu (C++)
description: W języku C++ słowa kluczowe static, extern i thread_local określają okres istnienia, powiązania i lokalizację pamięci dla zmiennej lub funkcji.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: c3fc87980d1fd0af5b803a8e590855f6429c847e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213167"
---
# <a name="storage-classes"></a>Klasy magazynu

*Klasa magazynu* w kontekście deklaracji zmiennych C++ jest specyfikatorem typu, który zarządza okresem istnienia, powiązaniem i lokalizacją pamięci obiektów. Dany obiekt może mieć tylko jedną klasę magazynu. Zmienne zdefiniowane w bloku mają automatyczny magazyn, chyba że określono inaczej przy **`extern`** użyciu **`static`** **`thread_local`** specyfikatorów, lub. Automatyczne obiekty i zmienne nie mają powiązania; nie są one widoczne w kodzie poza blokiem. Pamięć jest przydzielono automatycznie, gdy wykonanie przejdzie do bloku i zostanie cofnięta alokacja, gdy blok zostanie zakończony.

**Uwagi**

1. Słowo kluczowe [mutable](../cpp/mutable-data-members-cpp.md) może być uznawane za specyfikator klasy magazynu. Jednak jest ono dostępne tylko na liście składowych definicji klasy.

1. **Program Visual Studio 2010 lub nowszy:** **`auto`** Słowo kluczowe nie jest już specyfikatorem klasy magazynu C++ i **`register`** słowo kluczowe jest przestarzałe. **Visual Studio 2017 w wersji 15,7 lub nowszej:** (dostępne z [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): **`register`** słowo kluczowe jest usuwane z języka C++.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a> `static`

**`static`** Słowo kluczowe może służyć do deklarowania zmiennych i funkcji w zakresie globalnym, zakresie przestrzeni nazw i zakresu klasy. Zmienne statyczne mogą być również deklarowane w zakresie lokalnym.

Statyczny czas trwania oznacza, że obiekt lub zmienna są przydzielenia podczas uruchamiania programu i zostaje cofnięta alokacja po zakończeniu programu. Połączenie zewnętrzne oznacza, że nazwa zmiennej jest widoczna spoza pliku, w którym jest zadeklarowana zmienna. Z drugiej strony połączenie wewnętrzne oznacza, że nazwa nie jest widoczna poza plikiem, w którym zmienna jest zadeklarowana. Domyślnie obiekt lub zmienna zdefiniowana w globalnej przestrzeni nazw ma statyczny czas trwania i zewnętrzne powiązania. **`static`** Słowo kluczowe może być używane w następujących sytuacjach.

1. Gdy deklarujesz zmienną lub funkcję w zakresie pliku (zakres globalny i/lub przestrzeń nazw), **`static`** słowo kluczowe Określa, że zmienna lub funkcja ma wewnętrzny związek. Kiedy deklarujesz zmienną, zmienna ma statyczny czas trwania i kompilator inicjuje ją wartością 0, chyba że określisz inną wartość.

1. Po zadeklarowaniu zmiennej w funkcji **`static`** słowo kluczowe Określa, że zmienna zachowuje swój stan między wywołaniami tej funkcji.

1. Kiedy deklarujesz element członkowski danych w deklaracji klasy, **`static`** słowo kluczowe Określa, że jedna kopia składowej jest współdzielona przez wszystkie wystąpienia klasy. Statyczna składowa danych musi być zdefiniowana w zakresie pliku. Integralna składowa danych zadeklarowana jako **`const static`** może mieć inicjator.

1. Kiedy deklarujesz funkcję członkowską w deklaracji klasy, **`static`** słowo kluczowe Określa, że funkcja jest współużytkowana przez wszystkie wystąpienia klasy. Statyczna funkcja członkowska nie może uzyskać dostępu do składowej wystąpienia, ponieważ funkcja nie ma niejawnego **`this`** wskaźnika. Aby uzyskać dostęp do elementu członkowskiego wystąpienia, zadeklaruj funkcję za pomocą parametru, który jest wskaźnikiem wystąpienia lub odwołaniem.

1. Nie można zadeklarować elementów członkowskich Unii jako static. Jednak globalnie zadeklarowana Unia anonimowa musi być jawnie zadeklarowana **`static`** .

Ten przykład pokazuje, jak zmienna zadeklarowana **`static`** w funkcji zachowuje swój stan między wywołaniami tej funkcji.

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

Ten przykład pokazuje użycie **`static`** w klasie.

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

Ten przykład pokazuje zmienną lokalną zadeklarowaną **`static`** w funkcji składowej. **`static`** Zmienna jest dostępna dla całego programu; wszystkie wystąpienia typu mają tę samą kopię **`static`** zmiennej.

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

Począwszy od języka C++ 11, **`static`** zagwarantowanie zainicjowania zmiennej lokalnej jest bezpieczne wątkowo. Ta funkcja jest czasami nazywana *Magic statics*. Jednak w aplikacji wielowątkowej wszystkie kolejne przypisania muszą zostać zsynchronizowane. Funkcję inicjalizacji statycznej bezpiecznie wątku można wyłączyć za pomocą flagi, [`/Zc:threadSafeInit-`](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) Aby uniknąć tworzenia zależności na CRT.

## <a name="extern"></a><a name="extern"></a> `extern`

Obiekty i zmienne zadeklarowane jako **`extern`** deklarują obiekt, który jest zdefiniowany w innej jednostce translacji lub w otaczającym zakresie jako mający połączenie zewnętrzne. Aby uzyskać więcej informacji, zobacz [`extern`](extern-cpp.md) i [jednostki tłumaczenia i powiązania](program-and-linkage-cpp.md).

## <a name="thread_local-c11"></a><a name="thread_local"></a>`thread_local`(C++ 11)

Zmienna zadeklarowana ze **`thread_local`** specyfikatorem jest dostępna tylko w wątku, w którym został utworzony. Zmienna jest tworzona podczas tworzenia wątku i niszczona, gdy wątek zostanie zniszczony. Każdy wątek ma własną kopię zmiennej. W systemie Windows **`thread_local`** jest funkcjonalnie równoważny z atrybutem specyficznym dla firmy Microsoft [`__declspec( thread )`](../cpp/thread.md) .

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

Rzeczy, na które należy zwrócić uwagę na temat **`thread_local`** specyfikatora:

- Dynamicznie inicjowane zmienne lokalne wątku w bibliotekach DLL mogą nie być poprawnie zainicjowane we wszystkich wątkach wywołań. Aby uzyskać więcej informacji, zobacz [`thread`](thread.md).

- **`thread_local`** Specyfikator może być połączony z **`static`** lub **`extern`** .

- Można stosować **`thread_local`** tylko do deklaracji i definicji danych; **`thread_local`** nie można używać w deklaracjach lub definicjach funkcji.

- Można określić **`thread_local`** tylko dla elementów danych ze statycznym okresem przechowywania. Obejmuje to globalne obiekty danych (zarówno **`static`** i **`extern`** ), lokalne obiekty statyczne i statyczne elementy członkowskie danych klas. Każda zadeklarowana zmienna lokalna **`thread_local`** jest niejawnie statyczna, jeśli nie podano innej klasy magazynu; innymi słowy, w zakresie bloku **`thread_local`** jest równoważne **`thread_local static`** .

- Należy określić **`thread_local`** zarówno dla deklaracji, jak i definicji obiektu lokalnego wątku, niezależnie od tego, czy deklaracja i definicja występują w tym samym pliku, czy w oddzielnych plikach.

W systemie Windows **`thread_local`** jest funkcjonalnie równoważne z [`__declspec(thread)`](../cpp/thread.md) wyjątkiem, że *`*__declspec(thread)`* * można zastosować do definicji typu i jest prawidłowy w kodzie C. Jeśli to możliwe, należy użyć, **`thread_local`** ponieważ jest częścią standardu C++ i dlatego jest bardziej przenośne.

## <a name="register"></a><a name="register"></a>zarejestrować

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępne z [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ): **`register`** słowo kluczowe nie jest już obsługiwaną klasą magazynu. Słowo kluczowe jest nadal zarezerwowane w standardzie do użytku w przyszłości.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Przykład: automatyczne i statyczne inicjowanie

Lokalny automatyczny obiekt lub zmienna jest inicjowana za każdym razem, gdy przepływ sterowania osiągnie swoją definicję. Zostanie zainicjowany lokalny obiekt statyczny lub zmienna, gdy przepływ sterowania osiągnie swoją definicję.

Rozważmy poniższy przykład, który definiuje klasę, która rejestruje inicjalizację i zniszczenie obiektów, a następnie definiuje trzy obiekty,, `I1` `I2` i `I3` :

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

W tym przykładzie pokazano, jak i kiedy obiekty `I1` , `I2` i `I3` są inicjowane oraz kiedy są niszczone.

Istnieje kilka punktów, dla których należy pamiętać o programie:

- Najpierw `I1` i `I2` są automatycznie niszczone, gdy przepływ sterowania opuszcza blok, w którym są zdefiniowane.

- Sekunda w języku C++ nie jest konieczne deklarowanie obiektów lub zmiennych na początku bloku. Ponadto te obiekty są inicjowane tylko wtedy, gdy przepływ sterowania osiągnie swoje definicje. ( `I2` i `I3` są przykładami takich definicji). Dane wyjściowe są wyświetlane dokładnie po zainicjowaniu.

- Na koniec statyczne zmienne lokalne, takie jak `I3` zachowywanie ich wartości przez czas trwania programu, są niszczone podczas kończenia działania programu.

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)
