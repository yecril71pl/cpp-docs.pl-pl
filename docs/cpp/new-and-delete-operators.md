---
title: new i delete, operatory
description: Operatory New i DELETE języka C++ umożliwiają kontrolę nad alokacją.
ms.date: 07/07/2020
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.openlocfilehash: e609d1fdbd4f945ab8709c554d1396100027c4c1
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127842"
---
# <a name="new-and-delete-operators"></a>`new``delete`Operatory i

Język C++ obsługuje dynamiczne przydzielanie i cofanie alokacji obiektów przy użyciu [`new`](new-operator-cpp.md) [`delete`](delete-operator-cpp.md) operatorów i. Te operatory przydzielają pamięć dla obiektów z puli o nazwie Free Store. **`new`** Operator wywołuje funkcję specjalną [`operator new`](new-operator-cpp.md) , a **`delete`** operator wywołuje funkcję specjalną [`operator delete`](delete-operator-cpp.md) .

**`new`** Funkcja w standardowej bibliotece języka c++ obsługuje zachowanie określone w standardzie c++, który jest zgłasza `std::bad_alloc` wyjątek, jeśli alokacja pamięci nie powiedzie się. Jeśli nadal chcesz uzyskać niezgłaszaną wersję programu **`new`** , Połącz program z usługą *`nothrownew.obj`* . Jednak w przypadku połączenia z programem *`nothrownew.obj`* wartość domyślna **`operator new`** w standardowej bibliotece języka C++ nie jest już działać.

Aby zapoznać się z listą plików biblioteki w bibliotece środowiska uruchomieniowego C i standardowej biblioteki języka C++, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> `new` Operator

Kompilator tłumaczy instrukcję, taką jak ta, w wywołaniu funkcji **`operator new`** :

```cpp
char *pch = new char[BUFFER_SIZE];
```

Jeśli żądanie dotyczy 0 bajtów magazynu, **`operator new`** zwraca wskaźnik do odrębnego obiektu. Oznacza to, że powtórzone wywołania **`operator new`** zwracające różne wskaźniki. Jeśli jest za mało pamięci dla żądania alokacji, program **`operator new`** zgłosi `std::bad_alloc` wyjątek. Lub zwraca wartość, **`nullptr`** Jeśli masz połączenie z niezgłaszanym **`operator new`** wsparciem.

Można napisać procedurę, która próbuje zwolnić pamięć, i ponowić próbę alokacji. Aby uzyskać więcej informacji, zobacz [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md). Aby uzyskać szczegółowe informacje na temat schematu odzyskiwania, zobacz sekcję [Obsługa niewystarczającej ilości pamięci](#handling-insufficient-memory) .

Dwa zakresy dla **`operator new`** funkcji są opisane w poniższej tabeli.

### <a name="scope-for-operator-new-functions"></a>Zakres `operator new` funkcji

| Operator | Zakres |
|--|--|
| **`::operator new`** | Globalnie |
| *Nazwa klasy***`::operator new`** | Klasa |

Pierwszy argument **`operator new`** musi być typu `size_t` , zdefiniowany w \<stddef.h> , a typem zwracanym jest zawsze **`void*`** .

Funkcja globalna **`operator new`** jest wywoływana, gdy **`new`** operator jest używany do alokowania obiektów typów wbudowanych, obiektów typu klasy, które nie zawierają funkcji zdefiniowanych przez użytkownika **`operator new`** i tablic dowolnego typu. Gdy **`new`** operator jest używany do alokowania obiektów typu klasy **`operator new`** , gdzie jest zdefiniowana, Klasa **`operator new`** jest wywoływana.

**`operator new`** Funkcja zdefiniowana dla klasy jest statyczną funkcją członkowską (która nie może być wirtualna), która ukrywa funkcję globalną **`operator new`** dla obiektów tego typu klasy. Rozważ przypadek, w którym **`new`** jest używany do przydzielania i ustawiania pamięci dla danej wartości:

```cpp
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

Argument podany w nawiasach **`new`** jest przekazywany `Blanks::operator new` jako `chInit` argument. Jednak funkcja globalna **`operator new`** jest ukryta, powodując, że Poniższy kod generuje błąd:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Kompilator obsługuje tablicę składową **`new`** i **`delete`** operatory w deklaracji klasy. Przykład:

```cpp
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

### <a name="handling-insufficient-memory"></a>Obsługa niewystarczającej ilości pamięci

Testowanie niepowodzenia alokacji pamięci można wykonać, jak pokazano poniżej:

```cpp
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

Istnieje inny sposób obsługi nieudanych żądań alokacji pamięci. Napisz niestandardową procedurę odzyskiwania, aby obsłużyć taką awarię, a następnie zarejestrować funkcję przez wywołanie [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md) funkcji run-time.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> `delete` Operator

Pamięć, która jest przydzielana dynamicznie przy użyciu **`new`** operatora, może zostać zwolniona przy użyciu **`delete`** operatora. Operator delete wywołuje **`operator delete`** funkcję, która zwalnia pamięć z powrotem do dostępnej puli. Użycie **`delete`** operatora powoduje również, że destruktor klasy (jeśli taki istnieje) ma zostać wywołany.

Istnieją funkcje globalne i o zakresie klas **`operator delete`** . Tylko jedna **`operator delete`** Funkcja może być zdefiniowana dla danej klasy; jeśli została zdefiniowana, ukrywa funkcję globalną **`operator delete`** . Funkcja globalna **`operator delete`** jest zawsze wywoływana dla tablic dowolnego typu.

Funkcja Global **`operator delete`** . Istnieją dwa formularze dla funkcji globalnych **`operator delete`** i składowych klasy **`operator delete`** :

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Dla danej klasy może być obecny tylko jeden z powyższych dwóch formularzy. Pierwszy formularz przyjmuje jeden argument typu **`void *`** , który zawiera wskaźnik do obiektu do cofnięcia alokacji. Druga forma, cofanie alokacji, przyjmuje dwa argumenty: pierwszy jest wskaźnikiem do bloku pamięci do alokacji, a sekunda jest liczbą bajtów do cofnięcia. Typem zwracanym obu formularzy jest **`void`** ( **`operator delete`** nie można zwrócić wartości).

Celem drugiego formularza jest przyspieszenie wyszukiwania poprawnej kategorii rozmiaru obiektu do usunięcia. Te informacje często nie są przechowywane w najbliższym przydziale i prawdopodobnie nie są buforowane. Drugi formularz jest przydatny, gdy **`operator delete`** Funkcja z klasy bazowej jest używana do usuwania obiektu klasy pochodnej.

**`operator delete`** Funkcja jest statyczna, dlatego nie może być wirtualna. **`operator delete`** Funkcja przestrzega kontroli dostępu, zgodnie z opisem w [Access Control członkowskich](member-access-control-cpp.md).

W poniższym przykładzie przedstawiono zdefiniowane przez użytkownika **`operator new`** i **`operator delete`** funkcje, które zaprojektowano w celu rejestrowania alokacji i cofnięcia przydziału pamięci:

```cpp
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

Poprzedni kod może służyć do wykrywania "wycieku pamięci", czyli pamięci, która jest przypisana w wolnym magazynie, ale nigdy nie została zwolniona. W celu wykrycia wycieków **`new`** Operatory globalne i **`delete`** są ponownie zdefiniowane w celu zliczenia alokacji i cofnięcia przydziału pamięci.

Kompilator obsługuje tablicę składową **`new`** i **`delete`** operatory w deklaracji klasy. Przykład:

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
