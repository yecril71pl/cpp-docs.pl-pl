---
title: Klasy magazynu (C++)
description: W C++, słowa kluczowe static, extern i thread_local określają okres istnienia, powiązania i lokalizację pamięci dla zmiennej lub funkcji.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: d4fe1e7f14ef2a11e5e7ac32b4ffb0247aab3c84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178551"
---
# <a name="storage-classes"></a>Klasy magazynu

*Klasa magazynu* w kontekście deklaracji C++ zmiennych jest specyfikatorem typu, który zarządza okresem istnienia, powiązaniem i lokalizacją pamięci obiektów. Dany obiekt może mieć tylko jedną klasę magazynu. Zmienne zdefiniowane w bloku mają automatyczny magazyn, chyba że określono inaczej przy użyciu specyfikatorów **extern**, **static**lub **thread_local** . Automatyczne obiekty i zmienne nie mają powiązania; nie są one widoczne w kodzie poza blokiem. Pamięć jest przydzielono automatycznie, gdy wykonanie przejdzie do bloku i zostanie cofnięta alokacja, gdy blok zostanie zakończony.

**Uwagi**

1. Słowo kluczowe [mutable](../cpp/mutable-data-members-cpp.md) może być uznawane za specyfikator klasy magazynu. Jednak jest ono dostępne tylko na liście składowych definicji klasy.

1. **Program Visual Studio 2010 lub nowszy:** Słowo **kluczowe** autonie jest już specyfikatorem klasy C++ magazynu, a słowo kluczowe **register** jest przestarzałe. **Visual Studio 2017 w wersji 15,7 lub nowszej:** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): słowo kluczowe **register** jest usuwane z C++ języka.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>ruchom

**Statycznego** słowa kluczowego można użyć do deklarowania zmiennych i funkcji w zakresie globalnym, zakresie przestrzeni nazw i zakresu klasy. Zmienne statyczne mogą być również deklarowane w zakresie lokalnym.

Statyczny czas trwania oznacza, że obiekt lub zmienna są przydzielenia podczas uruchamiania programu i zostaje cofnięta alokacja po zakończeniu programu. Połączenie zewnętrzne oznacza, że nazwa zmiennej jest widoczna spoza pliku, w którym jest zadeklarowana zmienna. Z drugiej strony połączenie wewnętrzne oznacza, że nazwa nie jest widoczna poza plikiem, w którym zmienna jest zadeklarowana. Domyślnie obiekt lub zmienna zdefiniowana w globalnej przestrzeni nazw ma statyczny czas trwania i zewnętrzne powiązania. **Statycznego** słowa kluczowego można użyć w poniższych sytuacjach.

1. Po zadeklarowaniu zmiennej lub funkcji w zakresie plików (globalnym i/lub zakresie przestrzeni nazw) **static** słowo kluczowe Określa, że zmienna lub funkcja ma wewnętrzny związek. Kiedy deklarujesz zmienną, zmienna ma statyczny czas trwania i kompilator inicjuje ją wartością 0, chyba że określisz inną wartość.

1. Po zadeklarowaniu zmiennej w funkcji, **statyczne** słowo kluczowe Określa, że zmienna zachowuje swój stan między wywołaniami tej funkcji.

1. W przypadku deklarowania elementu członkowskiego danych w deklaracji klasy **static** słowo kluczowe Określa, że jedna kopia składowej jest współdzielona przez wszystkie wystąpienia klasy. Statyczna składowa danych musi być zdefiniowana w zakresie pliku. Integralna składowa danych zadeklarowana jako **stała statyczna** może mieć inicjator.

1. Gdy deklarujesz funkcję członkowską w deklaracji klasy, słowo kluczowe **static** określa, że funkcja jest współużytkowana przez wszystkie wystąpienia klasy. Statyczna funkcja członkowska nie może uzyskać dostępu do składowej wystąpienia, ponieważ funkcja nie ma **niejawnego** wskaźnika. Aby uzyskać dostęp do elementu członkowskiego wystąpienia, zadeklaruj funkcję za pomocą parametru, który jest wskaźnikiem wystąpienia lub odwołaniem.

1. Nie można zadeklarować elementów członkowskich Unii jako static. Jednak globalnie zadeklarowana Unia anonimowa musi być jawnie zadeklarowana jako **statyczna**.

Ten przykład pokazuje, jak zmienna zadeklarowana **statycznie** w funkcji zachowuje swój stan między wywołaniami tej funkcji.

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

Ten przykład pokazuje użycie **static** w klasie.

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

Ten przykład pokazuje zmienną lokalną zadeklarowaną jako **statyczną** w funkcji składowej. Zmienna statyczna jest dostępna dla całego programu; wszystkie wystąpienia typu mają tę samą kopię zmiennej statycznej.

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

Począwszy od języka C++ 11, inicjowanie statycznej zmiennej lokalnej jest zagwarantowane bezpieczny wątkowo. Ta funkcja jest czasami nazywana *Magic statics*. Jednak w aplikacji wielowątkowej wszystkie kolejne przypisania muszą zostać zsynchronizowane. Funkcję inicjalizacji statycznej z bezpiecznym wątkiem można wyłączyć za pomocą flagi [/Zc: threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) , aby uniknąć tworzenia zależności na CRT.

## <a name="extern"></a><a name="extern"></a>modyfikator

Obiekty i zmienne zadeklarowane jako **extern** deklarują obiekt, który jest zdefiniowany w innej jednostce translacji lub w otaczającym zakresie jako mający połączenie zewnętrzne. Aby uzyskać więcej informacji, [Zobacz](extern-cpp.md) zewnętrzne [jednostki i powiązania](program-and-linkage-cpp.md).

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C++ 11)

Zmienna zadeklarowana ze specyfikatorem **thread_local** jest dostępna tylko w wątku, w którym został utworzony. Zmienna jest tworzona podczas tworzenia wątku i niszczona, gdy wątek zostanie zniszczony. Każdy wątek ma własną kopię zmiennej. W systemie Windows **thread_local** jest funkcjonalnie równoważny z atrybutem [__declspec (wątek)](../cpp/thread.md) specyficznym dla firmy Microsoft.

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

Rzeczy do zanotowania dotyczące specyfikatora **thread_local** :

- Dynamicznie inicjowane zmienne lokalne wątku w bibliotekach DLL mogą nie być poprawnie zainicjowane we wszystkich wątkach wywołań. Aby uzyskać więcej informacji, zobacz [wątek](thread.md).

- Specyfikator **thread_local** może być połączony ze **statycznym** lub **extern**.

- **Thread_local** można stosować tylko do deklaracji i definicji danych. **thread_local** nie można używać w deklaracjach lub definicjach funkcji.

- Możesz określić **thread_local** tylko dla elementów danych ze statycznym okresem przechowywania. Obejmuje to globalne obiekty danych (zarówno **statyczne** , jak i zewnętrzne), lokalne obiekty **statyczne i statyczne**elementy członkowskie danych klas. Każda zmienna lokalna zadeklarowana **thread_local** jest niejawnie statyczna, jeśli nie podano innej klasy magazynu; Innymi słowy, w zakresie bloku **thread_local** jest równoważne `thread_local static`.

- Należy określić **thread_local** dla deklaracji i definicji obiektu lokalnego wątku, niezależnie od tego, czy deklaracja i definicja występują w tym samym pliku lub oddzielnych plikach.

W systemie Windows **thread_local** jest funkcjonalnie odpowiednikiem [__declspec (thread)](../cpp/thread.md) , z wyjątkiem tego, że **__declspec (thread)** można zastosować do definicji typu i jest on prawidłowy w kodzie C. Jeśli to możliwe, użyj **thread_local** , ponieważ jest częścią C++ standardu i dlatego jest bardziej przenośne.

##  <a name="register"></a><a name="register"></a>zarejestrować

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): słowo kluczowe **register** nie jest już obsługiwaną klasą magazynu. Słowo kluczowe jest nadal zarezerwowane w standardzie do użytku w przyszłości.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Przykład: automatyczne i statyczne inicjowanie

Lokalny automatyczny obiekt lub zmienna jest inicjowana za każdym razem, gdy przepływ sterowania osiągnie swoją definicję. Zostanie zainicjowany lokalny obiekt statyczny lub zmienna, gdy przepływ sterowania osiągnie swoją definicję.

Rozważmy poniższy przykład, który definiuje klasę, która rejestruje inicjalizację i zniszczenie obiektów, a następnie definiuje trzy obiekty, `I1`, `I2`i `I3`:

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

W tym przykładzie pokazano, jak i kiedy obiekty `I1`, `I2`i `I3` są inicjowane i gdy są niszczone.

Istnieje kilka punktów, dla których należy pamiętać o programie:

- Najpierw `I1` i `I2` są automatycznie niszczone, gdy przepływ sterowania opuszcza blok, w którym są zdefiniowane.

- Po drugie, C++w, nie jest konieczne deklarowanie obiektów lub zmiennych na początku bloku. Ponadto te obiekty są inicjowane tylko wtedy, gdy przepływ sterowania osiągnie swoje definicje. (`I2` i `I3` są przykładami takich definicji). Dane wyjściowe są wyświetlane dokładnie po zainicjowaniu.

- Na koniec statyczne zmienne lokalne, takie jak `I3`, zachowują swoje wartości na czas trwania programu, ale są niszczone podczas kończenia działania programu.

## <a name="see-also"></a>Zobacz też

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)
