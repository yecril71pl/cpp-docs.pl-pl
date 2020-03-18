---
title: new i delete — operatory
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: 2fd665ce2570bbe7750684057cdf7f517f6f64f3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445449"
---
# <a name="new-and-delete-operators"></a>new i delete, operatory

C++obsługuje dynamiczne przydzielanie i cofanie alokacji obiektów przy użyciu operatorów [New](new-operator-cpp.md) i [delete](delete-operator-cpp.md) . Te operatory przydzielają pamięć dla obiektów z puli o nazwie Free Store. Operator **New** wywołuje operator funkcji specjalnych [New](new-operator-cpp.md), a operator **delete** wywołuje operator specjalnej funkcji [delete](delete-operator-cpp.md).

**Nowa** funkcja w C++ standardowej bibliotece obsługuje zachowanie określone w C++ standardzie, które ma zgłosić wyjątek std:: bad_alloc, jeśli alokacja pamięci nie powiedzie się. Jeśli nadal chcesz mieć niezgłaszaną wersję **nowego**, Połącz program z nothrownew. obj. Jednak podczas łączenia z nothrownew. obj domyślny **operator new** w bibliotece C++ standardowej nie będzie już działać.

Aby zapoznać się z listą plików biblioteki wchodzących w skład biblioteki środowiska uruchomieniowego C C++ i biblioteki standardowej, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"> </a> Operator new

Gdy w programie napotkana jest instrukcja, taka jak w programie, przekształci się w wywołaniu **operatora funkcji New**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Jeśli żądanie dotyczy 0 bajtów magazynu, **operator new** zwraca wskaźnik do unikatowego obiektu (to jest, powtórzone wywołania **operatora new** zwracają różne wskaźniki). W przypadku braku wystarczającej ilości pamięci dla żądania alokacji **operator new** zgłosi wyjątek `std::bad_alloc` lub zwraca **nullptr** , jeśli masz połączenie z niezgłaszanym **operatorem** .

Można napisać procedurę, która próbuje zwolnić pamięć, i ponowić próbę alokacji; Aby uzyskać więcej informacji, zobacz [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) . Więcej informacji o schemacie odzyskiwania znajduje się w sekcji Obsługa niewystarczającej ilości pamięci w tym temacie.

Dwa zakresy dla **operatora nowe** funkcje są opisane w poniższej tabeli.

### <a name="scope-for-operator-new-functions"></a>Zakres dla nowych funkcji operatora

|Operator|Zakres|
|--------------|-----------|
|**:: operator new**|Globalny|
|*class-name* **:: operator new**|Klasa|

Pierwszy argument **operatora new** musi być typu `size_t` (typ zdefiniowany w \<STDDEF. h >), a zwracany typ to zawsze **void** <strong>\*</strong>.

Nowa funkcja **operatora** globalnego jest wywoływana, gdy operator **New** jest używany do alokowania obiektów wbudowanych typów, obiektów typu klasy, które nie zawierają zdefiniowanego przez użytkownika **operatora new** i tablic dowolnego typu. Gdy operator **New** jest używany do alokowania obiektów typu klasy, w którym zdefiniowano **operator new** , wywoływana jest **Nowa operator** klasy.

Funkcja **operatora new** zdefiniowana dla klasy jest statyczną funkcją członkowską (która w związku z tym nie może być wirtualna), która ukrywa globalny **operator new** dla obiektów tego typu klasy. Rozważ przypadek, w którym **Nowy** jest używany do przydzielania i ustawiania pamięci dla danej wartości:

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

Argument podany w nawiasach do **New** jest przekazywany do `Blanks::operator new` jako argument `chInit`. Jednak globalna funkcja **New** jest ukryta, powodując, że Poniższy kod generuje błąd:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Kompilator obsługuje operatory **New** i **delete** tablicy składowej w deklaracji klasy. Na przykład:

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

Istnieje inny sposób obsługi nieudanych żądań alokacji pamięci. Napisz niestandardową procedurę odzyskiwania, aby obsłużyć taką awarię, a następnie zarejestrować funkcję przez wywołanie funkcji [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Run-Time.

##  <a id="delete_operator"> </a> Operator delete

Pamięć, która jest przydzielana dynamicznie przy użyciu operatora **New** , może zostać zwolniona przy użyciu operatora **delete** . Operator delete wywołuje funkcję **delete operatora** , która zwalnia pamięć z powrotem do dostępnej puli. Użycie operatora **delete** powoduje również, że destruktor klasy (jeśli istnieje) do wywołania.

Istnieją funkcje **usuwania operatorów** globalnych i zakresów klas. Dla danej klasy można zdefiniować tylko jedną funkcję **delete operatora** . Jeśli jest zdefiniowany, ukrywa funkcję **delete operatora** globalnego. Funkcja **usuwania operatora** globalnego jest zawsze wywoływana dla tablic dowolnego typu.

Funkcja **usuwania operatora** globalnego. Istnieją dwa formularze dla globalnego **operatora delete** oraz funkcje **delete operatora** składowej klasy:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Dla danej klasy może być obecny tylko jeden z powyższych dwóch formularzy. Pierwszy formularz przyjmuje jeden argument typu `void *`, który zawiera wskaźnik do obiektu do cofnięcia przydziału. Druga forma — cofanie alokacji — pobiera dwa argumenty, z których pierwszy jest wskaźnikiem do bloku pamięci do alokacji, a drugi jest liczbą bajtów do cofnięcia. Zwracany typ obu formularzy to **void** (**operator delete** nie może zwrócić wartości).

Celem drugiego formularza jest przyspieszenie wyszukiwania poprawnej kategorii rozmiaru obiektu, który ma zostać usunięty, co często nie jest przechowywane blisko alokacji i prawdopodobnie nie jest w pamięci podręcznej. Drugi formularz jest przydatny, gdy funkcja **usuwania operatora** z klasy bazowej jest używana do usuwania obiektu klasy pochodnej.

Funkcja **usuwania operatora** jest statyczna; w związku z tym nie może być wirtualny. Funkcja **delete operatora** przestrzega kontroli dostępu, zgodnie z opisem w [Access Control członkowskich](member-access-control-cpp.md).

Poniższy przykład przedstawia zdefiniowane przez użytkownika **Operatory New** i **operator delete** , które zaprojektowano w celu rejestrowania alokacji i cofnięcia przydziału pamięci:

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

Poprzedni kod może służyć do wykrywania "wycieku pamięci", czyli pamięci, która jest alokowana w wolnym magazynie, ale nigdy nie jest zwolniona. Aby przeprowadzić to wykrywanie, globalne operatory **New** i **delete** zostaną ponownie zdefiniowane w celu zliczenia alokacji i cofnięcia przydziału pamięci.

Kompilator obsługuje operatory **New** i **delete** tablicy składowej w deklaracji klasy. Na przykład:

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
