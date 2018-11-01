---
title: new i delete — operatory
ms.date: 11/04/2016
f1_keywords:
- delete_cpp
- new
helpviewer_keywords:
- new keyword [C++], dynamic allocation of objects
- nothrownew.obj
- delete keyword [C++], syntax
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: 1ac6282ecbf45f22e7dd66b94f8bccdbc4e505ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441304"
---
# <a name="new-and-delete-operators"></a>new i delete — operatory

Język C++ obsługuje dynamicznej alokacji i dezalokacji obiektów przy użyciu [nowe](../cpp/new-operator-cpp.md) i [Usuń](../cpp/delete-operator-cpp.md) operatorów. Te operatory przydzielają pamięć dla obiektów z puli, o nazwie wolny magazyn. **Nowe** operatora wywołania funkcji specjalnej [nowy operator](../cpp/new-operator-cpp.md)i **Usuń** operatora wywołania funkcji specjalnej [operatora delete](../cpp/delete-operator-cpp.md).

**Nowe** funkcji w standardowej biblioteki języka C++ obsługuje zachowanie, które określono w standardzie C++, który jest zgłosić wyjątek std::bad_alloc, jeśli Alokacja pamięci nie powiedzie się. Jeśli nadal chcesz niezgłaszające wersję **nowe**, Połącz program jest połączony z nothrownew.obj. Jednakże, jeśli łączysz się z nothrownew.obj, wartość domyślna **nowy operator** w standardowej bibliotece C++ nie będzie działać.

Aby uzyskać listę plików bibliotek, wchodzące w skład Biblioteka uruchomieniowa C i standardową bibliotekę języka C++, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"> </a> New — operator

W przypadku instrukcji takich jak następujące w programie tłumaczy je na wywołanie funkcji **nowy operator**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Jeśli żądanie wymaga zero bajtów magazynu, **nowy operator** zwraca wskaźnik do różnego obiektu (czyli wielokrotne wywołania **nowy operator** zwracają różne wskaźniki). Jeśli pamięć jest niewystarczająca dla żądania alokacji **nowy operator** zgłasza wyjątek std::bad_alloc lub zwraca **nullptr** jeśli zostały połączone w niezgłaszające **nowy operator** pomocy technicznej.

Można napisać procedurę, która spróbuje zwolnić pamięć i ponowić próbę alokacji; zobacz [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Aby uzyskać więcej informacji. Aby uzyskać szczegółowe informacje na temat schematu odzyskiwania Zobacz sekcję obsługi niewystarczającej ilości pamięci w tym temacie.

Dwa zakresy dla **nowy operator** funkcje są opisane w poniższej tabeli.

### <a name="scope-for-operator-new-functions"></a>Zakres dla funkcji operator new

|Operator|Zakres|
|--------------|-----------|
|**:: nowy operator**|Global|
|*Nazwa klasy* **:: nowy operator**|Class|

Pierwszy argument **nowy operator** musi być typu `size_t` (typ zdefiniowany w \<stddef.h >), a typ zwracany to zawsze **void** <strong>\*</strong>.

Globalna **nowy operator** funkcja jest wywoływana, gdy **nowe** operator jest używany do alokowania obiektów typów wbudowanych, obiektów typu klasy, które nie zawierają zdefiniowanych przez użytkownika **nowy operator** funkcje i tablic dowolnego typu. Gdy **nowe** operator jest używany do alokowania obiektów typu klasy gdzie **nowy operator** jest zdefiniowany, tej klasy **nowy operator** jest wywoływana.

**Nowy operator** funkcję zdefiniowaną dla klasy jest statyczną funkcją składową (która zatem nie mogą być wirtualna), która ukrywa globalną **nowy operator** funkcji dla obiektów typu klasy. Należy rozważyć sytuację której **nowe** służy do przydzielania i ustawienia pamięci dla danej wartości:

```cpp
// spec1_the_operator_new_function1.cpp
#include <malloc.h>
#include <memory.h>

class Blanks
{
public:
    Blanks(){}
    void *operator new( size_t stAllocateBlock, char chInit );
};
void *Blanks::operator new( size_t stAllocateBlock, char chInit )
{
    void *pvTemp = malloc( stAllocateBlock );
    if( pvTemp != 0 )
        memset( pvTemp, chInit, stAllocateBlock );
    return pvTemp;
}
// For discrete objects of type Blanks, the global operator new function
// is hidden. Therefore, the following code allocates an object of type
// Blanks and initializes it to 0xa5
int main()
{
   Blanks *a5 = new(0xa5) Blanks;
   return a5 != 0;
}
```

Argument podany w nawiasach dla **nowe** jest przekazywany do `Blanks::operator new` jako `chInit` argumentu. Jednak globalnego **nowy operator** funkcja jest ukryta, powodując kodu takiego jak następujących czynności, aby wygenerować błąd:

```cpp
Blanks *SomeBlanks = new Blanks;
```

W typach nieklasowych 5.0 i starszych wersjach Visual C++ i wszystkie tablice (niezależnie od tego, czy były typu **klasy** typu) przydzielone za pomocą **nowe** operator zawsze używały globalnej **nowy operator** funkcji.

Począwszy od Visual C++ 5.0, kompilator obsługuje tablicy elementów członkowskich **nowe** i **Usuń** operatorów w deklaracji klasy. Na przykład:

```cpp
// spec1_the_operator_new_function2.cpp
class MyClass
{
public:
   void * operator new[] (size_t)
   {
      return 0;
   }
   void   operator delete[] (void*)
   {
   }
};

int main()
{
   MyClass *pMyClass = new MyClass[5];
   delete [] pMyClass;
}
```

### <a name="handling-insufficient-memory"></a>Obsługa za mało pamięci

Testowanie pod kątem błędy alokacji pamięci może odbywać się przy użyciu kodu, takie jak następujące:

```cpp
// insufficient_memory_conditions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
#define BIG_NUMBER 100000000
int main() {
   int *pI = new int[BIG_NUMBER];
   if( pI == 0x0 ) {
      cout << "Insufficient memory" << endl;
      return -1;
   }
}
```

Istnieje inny sposób do obsługi żądań alokacji pamięci nie powiodło się: napisać procedurę odzyskiwanie niestandardowe do obsługi awarii, a następnie zarejestrować swoją funkcję, wywołując [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) funkcji czasu wykonywania.

##  <a id="delete_operator"> </a> Delete operator

Pamięć, która jest przydzielany dynamicznie przy użyciu **nowe** operator może zostać uwolniona za pomocą **Usuń** operatora. Wywołuje operator delete **operatora delete** funkcji, która powoduje zwolnienie dostępnej puli pamięci. Za pomocą **Usuń** operator również powoduje, że destruktor klasy (jeśli istnieje) ma zostać wywołana.

Istnieją globalne i zakres klasy **operatora delete** funkcji. Tylko jeden **operatora delete** funkcji mogą być definiowane dla danej klasy; Jeśli zdefiniowane, ukrywa globalną **operatora delete** funkcji. Globalna **operatora delete** funkcja zawsze jest wywoływana dla tablic dowolnego typu.

Globalna **operatora delete** funkcji. Dwie formy istnieje dla globalnych **operatora delete** i elementów członkowskich klasy **operatora delete** funkcje:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Tylko jeden z poprzednich dwóch formach mogą być obecne dla danej klasy. Pierwszy formularz przyjmuje pojedynczy argument typu `void *`, który zawiera wskaźnik do obiektu można cofnąć alokacji. Druga forma — rozmiar dezalokacji — przyjmuje dwa argumenty, pierwszy z nich jest wskaźnik do bloku pamięci, które można cofnąć alokacji, a drugi z nich jest liczba bajtów, które można cofnąć alokacji. Zwracany typ obie formy jest **void** (**operatora delete** nie może zwracać wartości).

Celem drugi formularz jest przyspieszenie wyszukiwania dla kategorii właściwy rozmiar obiektu, który ma zostać usunięte, co często nie jest przechowywane w pobliżu alokacji, sama i prawdopodobnie niebuforowanych; Druga forma jest szczególnie przydatne, gdy **operatora delete** funkcja z klasy bazowej służy do usuwania obiektu klasy pochodnej.

**Operatora delete** funkcja jest statyczna; dlatego nie może być wirtualny. **Operatora delete** funkcja przestrzegają kontroli dostępu, zgodnie z opisem w [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md).

W poniższym przykładzie pokazano zdefiniowane przez użytkownika **nowy operator** i **operatora delete** funkcje przeznaczone do rejestrowania alokacji i cofnięcia alokacji pamięci:

```cpp
// spec1_the_operator_delete_function1.cpp
// compile with: /EHsc
// arguments: 3
#include <iostream>
using namespace std;

int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?
int cBlocksAllocated = 0;  // Count of blocks allocated.

// User-defined operator new.
void *operator new( size_t stAllocateBlock ) {
   static int fInOpNew = 0;   // Guard flag.

   if ( fLogMemory && !fInOpNew ) {
      fInOpNew = 1;
      clog << "Memory block " << ++cBlocksAllocated
          << " allocated for " << stAllocateBlock
          << " bytes\n";
      fInOpNew = 0;
   }
   return malloc( stAllocateBlock );
}

// User-defined operator delete.
void operator delete( void *pvMem ) {
   static int fInOpDelete = 0;   // Guard flag.
   if ( fLogMemory && !fInOpDelete ) {
      fInOpDelete = 1;
      clog << "Memory block " << cBlocksAllocated--
          << " deallocated\n";
      fInOpDelete = 0;
   }

   free( pvMem );
}

int main( int argc, char *argv[] ) {
   fLogMemory = 1;   // Turn logging on
   if( argc > 1 )
      for( int i = 0; i < atoi( argv[1] ); ++i ) {
         char *pMem = new char[10];
         delete[] pMem;
      }
   fLogMemory = 0;  // Turn logging off.
   return cBlocksAllocated;
}
```

Powyższy kod może służyć do wykrywania "wyciek pamięci" — oznacza to, pamięci, który jest przydzielone w wolnym magazynie, ale nigdy nie jest zwalniana. Do wykonania wykrywanie, globalnej **nowe** i **Usuń** operatory definiowane są liczby alokacji i dezalokacji pamięci.

Począwszy od Visual C++ 5.0, kompilator obsługuje tablicy elementów członkowskich **nowe** i **Usuń** operatorów w deklaracji klasy. Na przykład:

```cpp
// spec1_the_operator_delete_function2.cpp
// compile with: /c
class X  {
public:
   void * operator new[] (size_t) {
      return 0;
   }
   void operator delete[] (void*) {}
};

void f() {
   X *pX = new X[5];
   delete [] pX;
}
```