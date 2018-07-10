---
title: nowe i delete — operatory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
- new
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++], dynamic allocation of objects
- nothrownew.obj
- delete keyword [C++], syntax
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7f411d05491294421202ae6d8a1b7cbbb4e1d47
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423958"
---
# <a name="new-and-delete-operators"></a>new i delete — operatory

C++ obsługuje dynamicznej alokacji i dezalokacji obiektów przy użyciu [nowe](../cpp/new-operator-cpp.md) i [usunąć](../cpp/delete-operator-cpp.md) operatorów. Tych operatorów przydzielić pamięci dla obiektów z puli o nazwie wolnego magazynu. `new` Operator wywołania funkcji specjalnej [nowy operator](../cpp/new-operator-cpp.md)i `delete` operator wywołania funkcji specjalnej [operatora delete](../cpp/delete-operator-cpp.md).  
  
 `new` Funkcji w standardowej bibliotece C++ obsługuje zachowanie określone w standard C++, czyli zgłoszenia wyjątku std::bad_alloc, jeśli Alokacja pamięci nie powiodło się. Jeśli nadal chcesz wersja zgłaszanie `new`, Połącz program z nothrownew.obj. Jednakże, gdy należy połączyć z nothrownew.obj, domyślnie `operator new` w standardowej bibliotece C++ nie będzie działać.  
  
 Aby uzyskać listę plików bibliotek, które obejmują biblioteki wykonawczej C i standardowa biblioteka C++, zobacz [Biblioteka CRT — funkcje](../c-runtime-library/crt-library-features.md).  
  
##  <a id="new_operator"> </a> New — operator  
 Po napotkaniu w programie następujących instrukcji, program tłumaczy je na wywołanie funkcji `operator new`:  
  
```cpp  
char *pch = new char[BUFFER_SIZE];  
```  
  
Jeśli żądanie dotyczy zero bajtów pamięci masowej, **nowy operator** zwraca wskaźnik do różnych obiektów (czyli powtarzane wywołania **nowy operator** zwracać różnych wskaźników). Jeśli jest za mało pamięci dla żądania alokacji **nowy operator** wyjątek std::bad_alloc lub zwraca **nullptr** Jeśli istnieje łącze w z systemem innym niż zgłaszanie `operator new` obsługuje.  
  
Można zapisać procedury, która próbuje zwolnić pamięć, a następnie spróbuj ponownie alokacji; zobacz [_set_new_handler —](../c-runtime-library/reference/set-new-handler.md) Aby uzyskać więcej informacji. Więcej szczegółów na schemacie odzyskiwania Zobacz sekcję Obsługa za mało pamięci w tym temacie.  

  
Dwa zakresy dla funkcji `operator new` opisano w poniższej tabeli.  
  
### <a name="scope-for-operator-new-functions"></a>Zakres dla funkcji operator new  
  
|Operator|Zakres|  
|--------------|-----------|  
|**:: nowy operator**|Global|  
|*Nazwa klasy* **:: nowy operator**|Class|  
  
 Pierwszy argument **nowy operator** musi być typu **size_t** (typ zdefiniowany w \<stddef.h >), a typem zwracanym jest zawsze **void \***  .  
  
 Globalny **nowy operator** funkcja wywoływana, gdy **nowe** operator jest używana do alokowania obiektów wbudowanych typów, obiekty typu klasy, które nie zawierają zdefiniowane przez użytkownika **nowy operator** funkcje i tablice dowolnego typu. Podczas **nowe** operator jest używana do alokowania obiektów typu klasy gdzie **nowy operator** jest zdefiniowany tej klasy **nowy operator** jest wywoływana.  
  
 **Nowy operator** funkcji zdefiniowanej dla klasy to funkcja statycznego elementu członkowskiego (co w związku z tym nie może być wirtualna), która ukrywa globalną **nowy operator** funkcji w przypadku obiektów tego typu klasy. Rozważmy przypadek gdzie **nowe** służy do przydzielenia i ustawić pamięć do danej wartości:  
  
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
  
 Podany w nawiasy, aby argument **nowe** jest przekazywana do `Blanks::operator new` jako `chInit` argumentu. Jednak globalnej **nowy operator** funkcji jest ukryty, powodując kodu podobne do poniższych generuje błąd:  
  
```cpp  
Blanks *SomeBlanks = new Blanks;  
```  
  
 Visual C++ 5.0 lub starszym nonclass typów i wszystkie tablice (niezależnie od tego, czy zostały one z **klasy** typu) przydzielony przy użyciu **nowe** zawsze używać operatora globalnej **nowy operator** funkcji.  
  
 Począwszy od programu Visual C++ 5.0, kompilator obsługuje elementu członkowskiego tablicy **nowe** i **usunąć** operatory w deklaracji klasy. Na przykład:  
  
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
 Testowanie pod kątem błędy alokacji pamięci może odbywać się z kodem, takie jak następujące:  
  
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
  
 Istnieje inny sposób do obsługi żądań alokacji pamięci nie powiodło się: zapisu procedury odzyskiwania niestandardowego do obsługi tych błędów, a następnie zarejestrować przez wywołanie funkcji [_set_new_handler —](../c-runtime-library/reference/set-new-handler.md) funkcji środowiska wykonawczego.  
  
##  <a id="delete_operator"> </a> Delete — operator  
 Pamięci przydzielanej dynamicznie za pomocą **nowe** operator może zostać zwolniony za pomocą **usunąć** operatora. Wywołania operatora delete **operatora delete** funkcji, dzięki czemu dostępnej puli pamięci. Przy użyciu **usunąć** operatora powoduje także, że destruktora klasy (jeśli istnieje) do wywołania.  
  
 Istnieją globalne i zakres klasy **operatora delete** funkcji. Tylko jeden **operatora delete** funkcji mogą być definiowane dla danej klasy; Jeśli zdefiniowane, ukrywa globalną klasę **operatora delete** funkcji. Globalny **operatora delete** funkcja zawsze jest wywoływana dla tablic dowolnego typu.  
  
 Globalny **operatora delete** funkcji. Istnieją dwie formy dla globalnej **operatora delete** i element członkowski klasy **operatora delete** funkcje:  
  
```cpp  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 Tylko jeden z poprzednich dwóch formach mogą być obecne dla danej klasy. Pierwszy formularz pobiera jeden argument typu **void \*** , który zawiera wskaźnik do obiektu można cofnąć alokacji. Drugi formularz — o rozmiarze dezalokacji — przyjmuje dwa argumenty, z których pierwszy jest wskaźnik do bloku pamięci można cofnąć alokacji i drugi z nich jest liczba bajtów, które można cofnąć alokacji. Zwracany typ zarówno formularzy jest `void` (**operatora delete** nie może zwracać wartości).  
  
 Drugi formularz zamierzeniu przyspieszyć wyszukiwanie kategorii właściwego rozmiaru obiektu do usunięcia, które często nie są przechowywane w pobliżu alokacji, sama i prawdopodobnie niebuforowanych; drugi formularz jest szczególnie przydatne, gdy **operatora delete** funkcji z klasy podstawowej służy do usuwania obiektu klasy pochodnej.  
  
 **Operatora delete** funkcji jest statyczny; w związku z tym nie może być wirtualny. `operator delete` Funkcja przestrzega kontroli dostępu, zgodnie z opisem w [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md).  
  
 W poniższym przykładzie pokazano, zdefiniowane przez użytkownika **nowy operator** i **operatora delete** funkcje przeznaczone do rejestrowania alokacji i dezalokacji pamięci:  
  
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
  
 Poprzedni kod może służyć do wykrywania "wyciek pamięci" — to znaczy, pamięci, która jest przydzielona w magazynie bezpłatne, ale nigdy nie został zwolniony. Do wykonania tego wykrycia globalnej **nowe** i **usunąć** operatory definiowane są liczba alokacji i cofania alokacji pamięci.  
  
 Począwszy od programu Visual C++ 5.0, kompilator obsługuje elementu członkowskiego tablicy **nowe** i **usunąć** operatory w deklaracji klasy. Na przykład:  
  
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

