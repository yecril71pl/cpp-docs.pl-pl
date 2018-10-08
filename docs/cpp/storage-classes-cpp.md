---
title: Klasy magazynu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
- register_cpp
dev_langs:
- C++
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29e5b2783dda3c66736a7e668186d0645cdd4b84
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861320"
---
# <a name="storage-classes-c"></a>Klasy magazynu (C++)

A *klasę magazynu* w kontekście C++ deklaracje zmiennych jest specyfikatora typu, które regulują okres istnienia, powiązania i pamięć lokalizację obiektów. Dany obiekt może mieć tylko jedną klasę magazynu. Zmienne zdefiniowane w bloku mają automatycznego przechowywania, chyba że określono inaczej, za pomocą **extern**, **statyczne**, lub `thread_local` specyfikatorów. Obiekty automatyczne i zmienne mają bez połączenia; nie są one widoczne dla kodu poza blokiem.

**Uwagi**

1. [Mutable](../cpp/mutable-data-members-cpp.md) — słowo kluczowe może być uznane za Specyfikator klasy magazynowania. Jednak jest ono dostępne tylko na liście składowych definicji klasy.

1. **Visual C++ 2010 i nowszych wersji:** **automatycznie** — słowo kluczowe nie jest już specyfikatora klasy magazynowania C++ i **zarejestrować** — słowo kluczowe jest przestarzały. **Visual Studio 2017 w wersji 15.7 lub nowszej:** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **zarejestrować** — słowo kluczowe zostanie usunięty z języka C++.


```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>W tej sekcji:

- [static](#static)
- [extern](#extern)
- [Element thread_local](#thread_local)

## <a name="static"></a> Statyczne

**Statyczne** — słowo kluczowe może służyć do deklarowania zmiennych i funkcji w zakresie globalnym, zakresie przestrzeni nazw i zakres klasy. Zmienne statyczne mogą być także zadeklarowane w zakresie lokalnym.

Statyczne czasy trwania oznaczają, że obiekt lub zmienna jest przydzielany przy starcie programu i jest zwalniana, gdy program kończy pracę. Połączenie zewnętrzne oznacza, że nazwa zmiennej widoczne z poza plikiem, w którym zadeklarowana jest zmienna. Z drugiej strony wewnętrzne Łączenie oznacza, że nazwa nie jest widoczna poza plikiem w którym zadeklarowana jest zmienna. Domyślnie obiekt lub zmienna, która jest zdefiniowana w globalnej przestrzeni nazw ma statyczny czas trwania i powiązanie zewnętrzne. **Statyczne** — słowo kluczowe może służyć w następujących sytuacjach.

1. Kiedy Deklarujesz zmienną lub funkcję w zakresie pliku (globalne i/lub zakresie przestrzeni nazw), **statyczne** — słowo kluczowe Określa, że zmienna lub funkcja posiada wewnętrzne łączenie. Kiedy Deklarujesz zmienną, zmienna posiada stały czas trwania i kompilator inicjalizuje ją na wartość 0, chyba że określisz inną wartość.

1. Kiedy Deklarujesz zmienną w funkcji, **statyczne** — słowo kluczowe Określa, że zmienna zachowuje swój stan między wywołaniami tej funkcji.

1. Kiedy Deklarujesz element członkowski danych w deklaracji klasy, **statyczne** — słowo kluczowe Określa, że jedna kopia elementu członkowskiego jest udostępniania przez wszystkie wystąpienia klasy. Element członkowski danych statycznych musi być zdefiniowany w zakresie pliku. Element członkowski liczby całkowitej danych, który został zadeklarowany jako **const static** może mieć inicjatora.

1. Kiedy Deklarujesz element członkowski funkcji w deklaracji klasy, **statyczne** — słowo kluczowe Określa, że funkcja jest udostępniania przez wszystkie wystąpienia klasy. Statycznej funkcji członkowskiej nie może uzyskać dostępu do członka wystąpienia, ponieważ funkcja nie ma ukrytego **to** wskaźnika. Aby uzyskać dostęp do członka wystąpienia, Zadeklaruj funkcję z parametrem, który jest wskaźnikiem wystąpienia lub odwołania.

1. Nie można zadeklarować elementy członkowskie jako statyczne. Jednak globalnie zadeklarowane związki anonimowe muszą być jawnie zadeklarowane **statyczne**.

Ten przykład przedstawia, jak Zmienna zadeklarowana **statyczne** w funkcji zachowuje swój stan między wywołaniami tej funkcji.

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

W tym przykładzie przedstawiono użycie **statyczne** w klasie.

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

Zmienna lokalna zadeklarowana w tym przykładzie **statyczne** w funkcji składowej. Zmienna statyczna jest dostępna dla całego programu; wszystkie wystąpienia typu mają wspólną kopię zmiennej statycznej.

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

Począwszy od C ++ 11, lokalne statyczne inicjowanie zmiennej może być metodą o bezpiecznych wątkach. Ta funkcja jest czasami nazywana *Magiczna statyka*. Jednak w aplikacji wielowątkowych wszystkie kolejne przypisania musi być synchronizowane. Funkcję wątkowo inicjowanie statycznych można wyłączyć za pomocą [threadsafeinit](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) flagę, aby uniknąć tworzenia zależności na CRT.

## <a name="extern"></a> extern

Obiektów i zmiennych zadeklarowanych jako **extern** zadeklarować obiekt, który jest zdefiniowany w innej jednostce translacji, lub w zakresie otaczającym jako posiadające powiązania zewnętrzne.

Deklaracja **const** zmiennych o **extern** klasę magazynu wymusza zmienną mają powiązania zewnętrzne. Inicjowanie **extern const** zmiennej jest dozwolone w definiujące jednostce translacji. Inicjalizacje w jednostce translacji niż definiowanie jednostki translacji dać niezdefiniowane wyniki. Aby uzyskać więcej informacji, zobacz [użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) — opcja kompilatora powoduje, że kompilator zastosować [powiązania zewnętrzne]() do zmiennych zadeklarowanych za pomocą `extern constexpr`. We wcześniejszych wersjach programu Visual Studio i domyślnie lub jeśli **/Zc:externConstexpr-** jest określony, program Visual Studio stosuje zewnętrzne do **constexpr** nawet wtedy, gdy zmienne **extern** słowo kluczowe jest używane. **/Zc: externconstexpr** opcja jest dostępna, począwszy od wersji 15.6 programu Visual Studio 2017 Update. i jest domyślnie wyłączona. /Permissive-option nie włączać/Zc: externconstexpr.

W poniższym kodzie pokazano dwa **extern** deklaracji, `DefinedElsewhere` (która odnosi się do nazwy zdefiniowanej w innej jednostce translacji) i `DefinedHere` (która odnosi się do nazwy zdefiniowanej w zakresie otaczającym):

```cpp
// external.cpp
// DefinedElsewhere is defined in another translation unit
extern int DefinedElsewhere;
int main() {
   int DefinedHere;
   {
      // refers to DefinedHere in the enclosing scope
      extern int DefinedHere;
   }
}
```

## <a name="thread_local"></a> Element thread_local (C ++ 11)

Zmienna zadeklarowana ze `thread_local` specyfikator jest dostępna tylko w wątku, na której została utworzona. Zmienna jest tworzony podczas tworzenia wątku i niszczony, kiedy niszczony jest wątku. Każdy wątek ma własną kopię zmiennej. W Windows `thread_local` jest funkcjonalnym odpowiednikiem specyficzne dla firmy Microsoft [__declspec (wątek)](../cpp/thread.md) atrybutu.

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

Uwagi dotyczące `thread_local` specyfikator:

- Dynamicznie zainicjowany zmiennymi lokalnymi wątku w bibliotekach DLL nie może być poprawnie zainicjować we wszystkich wątkach wywoływania. Aby uzyskać więcej informacji, zobacz [wątku](thread.md).

- `thread_local` Specyfikator mogą być łączone z **statyczne** lub **extern**.

- Można zastosować `thread_local` tylko do danych, deklaracje i definicje; `thread_local` nie można używać w deklaracji lub definicji funkcji.

- Można określić `thread_local` tylko dla elementów danych ze statycznym okresem magazynu. Obejmuje to globalnych obiektów danych (zarówno **statyczne** i **extern**), lokalnych obiektów statycznych i statycznych składowych danych klas. Wszelkie zmienna lokalna zadeklarowana `thread_local` jest niejawnie statyczna, jeśli podano inną klasę magazynu; innymi słowy, w zakresie bloku `thread_local` jest odpowiednikiem `thread_local static`.

- Należy określić `thread_local` dla deklaracji i definicji lokalnego obiektu wątku, czy deklaracja i definicja występują w tym samym pliku lub osobnych plików.

W Windows `thread_local` jest funkcjonalnym odpowiednikiem [__declspec(thread)](../cpp/thread.md) z tą różnicą, że **__declspec(thread)** może odnosić się do definicji typu i jest prawidłowy w kodzie C. Możliwe, używaj `thread_local` ponieważ jest częścią standardu języka C++ i dlatego jest bardziej przenośny.

##  <a name="register"></a>  Zarejestruj się

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **zarejestrować** — słowo kluczowe nie jest już obsługiwaną klasą magazynu. Słowo kluczowe jest nadal zarezerwowane w standardzie do użytku w przyszłości.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Przykład: automatyczne i statyczne inicjowanie

Lokalny automatyczne obiekt lub zmienna jest inicjowana za każdym razem, gdy przepływ sterowania osiągnie jego definicji. Lokalnego obiektu statycznego lub zmienna jest inicjowana po raz pierwszy przepływ sterowania osiągnie jego definicji.

Rozważmy następujący przykład definiuje klasę, która rejestruje inicjowania i niszczenie obiektów, a następnie definiuje trzy obiekty, `I1`, `I2`, i `I3`:

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

W tym przykładzie pokazano, jak i kiedy obiekty `I1`, `I2`, i `I3` są inicjowane oraz gdy są niszczone.

Istnieje kilka punktów, które należy zwrócić uwagę na program:

- Po pierwsze, `I1` i `I2` automatycznie są niszczone, gdy przepływ sterowania opuszcza blok, w którym są zdefiniowane.

- Po drugie w języku C++, należy nie do deklarowania obiektów lub zmienne na początku bloku. Ponadto te obiekty są inicjowane tylko wtedy, gdy przepływ sterowania osiągnie ich definicje. (`I2` i `I3` są przykładami takich definicje.) Przedstawia dane wyjściowe, dokładnie tak, gdy są one inicjowane.

- Na koniec statyczne zmienne lokalne, takie jak `I3` zachowują swoje wartości czasu trwania programu, ale są niszczone, gdy program zakończy działanie.

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](../cpp/declarations-and-definitions-cpp.md)