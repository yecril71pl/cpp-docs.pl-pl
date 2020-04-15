---
title: new i delete — operatory
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367888"
---
# <a name="new-and-delete-operators"></a>new i delete, operatory

C++ obsługuje alokacji dynamicznej i alokacji transakcji obiektów przy użyciu [nowych](new-operator-cpp.md) i [delete](delete-operator-cpp.md) operatorów. Te operatory przydzielić pamięć dla obiektów z puli o nazwie magazynu wolnego. **Nowy** operator wywołuje nowy [operator](new-operator-cpp.md)funkcji specjalnych, a operator **delete** wywołuje usunięcie operatora funkcji [specjalnej](delete-operator-cpp.md).

**Nowa** funkcja w bibliotece standardowej języka C++ obsługuje zachowanie określone w standardzie C++, który ma zgłosić wyjątek std::bad_alloc, jeśli alokacja pamięci nie powiedzie się. Jeśli nadal chcesz nierzucanie wersji **nowego**, link programu z nothrownew.obj. Jednak po połączeniu z nothrownew.obj, domyślny **operator nowy** w bibliotece standardowej języka C++ nie działa już.

Aby uzyskać listę plików biblioteki składających się na bibliotekę środowiska wykonawczego C i standardową bibliotekę języka C++, zobacz [Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> Nowy operator

Gdy w programie napotkana zostanie następująca instrukcja, przekłada się na wywołanie operatora funkcji **nowego:**

```cpp
char *pch = new char[BUFFER_SIZE];
```

Jeśli żądanie jest dla zero bajtów magazynu, **operator nowy** zwraca wskaźnik do odrębnego obiektu (oznacza to, że powtarzające się wywołania **operatora nowe** zwracają różne wskaźniki). Jeśli nie ma wystarczającej ilości pamięci dla `std::bad_alloc` żądania alokacji, operator **new** zgłasza wyjątek lub zwraca **nullptr,** jeśli masz połączone w **operatorze** niezwiązanym z wyrzucaniem nowej obsługi.

Można napisać procedurę, która próbuje zwolnić pamięć i ponowić próbę alokacji; zobacz [_set_new_handler,](../c-runtime-library/reference/set-new-handler.md) aby uzyskać więcej informacji. Aby uzyskać więcej informacji na temat schematu odzyskiwania, zobacz obsługa niewystarczające pamięci sekcji tego tematu.

Dwa zakresy dla nowych funkcji **operatora** są opisane w poniższej tabeli.

### <a name="scope-for-operator-new-functions"></a>Zakres nowych funkcji operatora

|Operator|Zakres|
|--------------|-----------|
|**::operator nowy**|Globalny|
|*nazwa klasy* **::operator nowy**|Klasa|

Pierwszy argument **do operatora nowy** `size_t` musi być typu \<(typ zdefiniowany w stddef.h>), a typ zwracany jest zawsze **nieważne** <strong>\*</strong>.

Operator globalny **nowa** funkcja jest wywoływana, gdy **nowy** operator jest używany do przydzielania obiektów typów wbudowanych, obiektów typu klasy, które nie zawierają **zdefiniowanych** przez użytkownika nowych funkcji operatora i tablic dowolnego typu. Gdy **nowy** operator jest używany do przydzielania obiektów typu klasy, w którym **zdefiniowano nowy operator,** wywoływany jest **nowy operator** tej klasy.

**Operator nowa** funkcja zdefiniowana dla klasy jest funkcją statycznego elementu członkowskiego (która nie może być wirtualna), która ukrywa nową funkcję **operatora** globalnego dla obiektów tego typu klasy. Należy wziąć pod uwagę przypadek, w którym **nowy** jest używany do przydzielenia i ustawić pamięć do danej wartości:

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

Argument podany w nawiasach do **nowego** `Blanks::operator new` jest `chInit` przekazywany jako argument. Jednak operator globalny **nowa** funkcja jest ukryta, powodując kod, takich jak następujące do generowania błędu:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Kompilator obsługuje tablicy elementów członkowskich **nowych** i **usuń** operatorów w deklaracji klasy. Przykład:

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

Testowanie alokacji pamięci nie powiodło się można wykonać, jak pokazano poniżej:

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

Istnieje inny sposób obsługi żądań alokacji pamięci nie powiodło się. Napisz niestandardową procedurę odzyskiwania do obsługi takiego błędu, a następnie zarejestruj funkcję, wywołując [funkcję _set_new_handler](../c-runtime-library/reference/set-new-handler.md) wykonywania.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> Operator usuwania

Pamięć, która jest dynamicznie przydzielana przy użyciu **nowego** operatora, może zostać zwolniona za pomocą operatora **usuwania.** Operator delete wywołuje funkcję **usuwania operatora,** która zwalnia pamięć z powrotem do dostępnej puli. Za pomocą **delete** operator powoduje również destruktor klasy (jeśli istnieje) do wywołania.

Istnieją funkcje **usuwania operatora** o zasięgu globalnym i klasy. Tylko jedna funkcja **usuwania operatora** może być zdefiniowana dla danej klasy; jeśli zdefiniowano, ukrywa funkcję **usuwania operatora** globalnego. Funkcja **usuwania operatora** globalnego jest zawsze wywoływana dla tablic dowolnego typu.

Funkcja **usuwania operatora** globalnego. Istnieją dwa formularze dla funkcji **usuwania operatora** globalnego i **usuwania operatora** klasy:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Tylko jeden z dwóch poprzednich formularzy może być obecny dla danej klasy. Pierwszy formularz przyjmuje pojedynczy argument `void *`typu , który zawiera wskaźnik do obiektu do cofniętego przydziału. Drugi formularz — rozmiar rozmieszczenia — przyjmuje dwa argumenty, z których pierwszy jest wskaźnikiem do bloku pamięci do przydzielenia, a drugi to liczba bajtów do przydzielenia. Typ zwracany obu formularzy jest **nieważny** **(usunięcie operatora** nie może zwrócić wartości).

Celem drugiego formularza jest przyspieszenie wyszukiwania dla kategorii prawidłowego rozmiaru obiektu, który ma zostać usunięty, który często nie jest przechowywany w pobliżu samej alokacji i prawdopodobnie nie jest buforowany. Drugi formularz jest przydatny, gdy funkcja **usuwania operatora** z klasy podstawowej jest używana do usuwania obiektu klasy pochodnej.

Funkcja **usuwania operatora** jest statyczna; w związku z tym nie może być wirtualny. Funkcja **usuwania operatora** jest przestrzegana kontroli dostępu, zgodnie z opisem w [kontrolce dostępu do członka](member-access-control-cpp.md).

W poniższym przykładzie przedstawiono zdefiniowane przez użytkownika **operator nowe** i **operator usunąć** funkcje przeznaczone do rejestrowania alokacji i alokacji pamięci:

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

Poprzedni kod może służyć do wykrywania "wyciek pamięci" — to znaczy pamięci, która jest przydzielana w wolnym magazynie, ale nigdy nie jest zwalniana. Aby wykonać to wykrywanie, globalne **nowe** i **delete** operatory są ponownie zdefiniowane do zliczania alokacji i alokacji pamięci.

Kompilator obsługuje tablicy elementów członkowskich **nowych** i **usuń** operatorów w deklaracji klasy. Przykład:

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
