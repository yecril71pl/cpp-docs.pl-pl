---
title: new — Operator (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 81dd7483c49a699ac53ea53d33481fa6539d484c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223658"
---
# <a name="new-operator-c"></a>new — Operator (C++)

Przydziela pamięć dla obiektu lub tablicy obiektów *typu-Name* z wolnego sklepu i zwraca odpowiednio wpisany wskaźnik o wartości niezerowej do obiektu.

> [!NOTE]
> Rozszerzenia składników języka Microsoft C++ zapewniają obsługę **`new`** słowa kluczowego w celu dodawania wpisów w gnieździe tablic wirtualnych. Aby uzyskać więcej informacji, zobacz [Nowość (nowe miejsce w tabeli metod wirtualnych)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Składnia

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Uwagi

Jeśli nie powiedzie się, **`new`** zwraca zero lub zgłasza wyjątek; Aby uzyskać więcej informacji [, zobacz Operatory New i DELETE](../cpp/new-and-delete-operators.md) . To zachowanie domyślne można zmienić, pisząc procedurę niestandardowej obsługi wyjątków i wywołując [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) funkcję biblioteki wykonawczej z nazwą funkcji jako argumentem.

Aby uzyskać informacje na temat sposobu tworzenia obiektu na zarządzanym stosie, zobacz [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Gdy **`new`** jest używany do przydzielania pamięci dla obiektu klasy języka C++, Konstruktor obiektu jest wywoływany po przydzieleniu pamięci.

Użyj operatora [delete](../cpp/delete-operator-cpp.md) , aby cofnąć alokację pamięci przydzieloną z **`new`** operatorem.

Poniższy przykład przydziela i następnie zwalnia dwuwymiarową tablicę znaków o wielkości `dim` o 10. Podczas alokowania tablicy wielowymiarowej wszystkie wymiary oprócz pierwszej muszą być wyrażeniami stałymi, które obliczają wartości dodatnie; wymiar tablicy z lewej strony może być dowolnym wyrażeniem, które daje w wyniku wartość dodatnią. Podczas alokowania tablicy przy użyciu **`new`** operatora pierwszy wymiar może mieć wartość zero — **`new`** operator zwraca unikatowy wskaźnik.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*Nazwa typu* nie może zawierać **`const`** , **`volatile`** , deklaracji klasy ani deklaracji wyliczenia. W związku z tym następujące wyrażenie jest niedozwolone:

```cpp
volatile char *vch = new volatile char[20];
```

**`new`** Operator nie przypisuje typów referencyjnych, ponieważ nie są obiektami.

**`new`** Operatora nie można użyć do przydzielenia funkcji, ale może służyć do przydzielania wskaźników do funkcji. Poniższy przykład przydziela i następnie zwalnia tablicę siedmiu wskaźników do funkcji, które zwracają liczby całkowite.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

W przypadku użycia operatora **`new`** bez dodatkowych argumentów i kompilowania przy użyciu opcji [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)lub [/EHS](../build/reference/eh-exception-handling-model.md) kompilator generuje kod do operatora wywołania, **`delete`** Jeśli Konstruktor zgłosi wyjątek.

Na poniższej liście opisano elementy gramatyczne programu **`new`** :

*jęcia*<br/>
Zapewnia sposób przekazywania dodatkowych argumentów w przypadku przeciążenia **`new`** .

*Nazwa typu*<br/>
Określa typ do przydzielenia; może to być typ wbudowany lub zdefiniowany przez użytkownika. Jeśli specyfikacja typu jest skomplikowana, może być otoczona nawiasami, aby wymusić kolejność powiązań.

*skład*<br/>
Udostępnia wartość dla zainicjowanego obiektu. Nie można określić inicjatorów dla tablic. **`new`** Operator utworzy tablice obiektów tylko wtedy, gdy Klasa ma Konstruktor domyślny.

## <a name="example"></a>Przykład

Poniższy przykład kodu przydziela tablicę znaków i obiekt klasy `CName` , a następnie zwalnia je.

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example"></a>Przykład

Jeśli używasz nowej postaci rozmieszczenia **`new`** operatora, formularz z argumentami oprócz rozmiaru alokacji, kompilator nie obsługuje formy umieszczania **`delete`** operatora, jeśli Konstruktor zgłosi wyjątek. Na przykład:

```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>Inicjowanie obiektu przydzielono z nowym

Opcjonalne pole *inicjatora* jest zawarte w gramatyce dla **`new`** operatora. Dzięki temu nowe obiekty mogą zostać zainicjowane z konstruktorów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji na temat sposobu inicjowania, zobacz [inicjatory](../cpp/initializers.md). Poniższy przykład ilustruje sposób użycia wyrażenia inicjującego z **`new`** operatorem:

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

W tym przykładzie obiekt `CheckingAcct` jest przydzielony przy użyciu **`new`** operatora, ale nie określono domyślnej inicjalizacji. W związku z tym, wywoływany jest domyślny konstruktor dla klasy `Acct()`. Następnie obiekt `SavingsAcct` jest przydzielany ten sam sposób, chyba że wyraźnie jest zainicjowany na 34.98. Ponieważ 34,98 jest typu **`double`** , Konstruktor, który przyjmuje argument tego typu, jest wywoływany do obsługi inicjalizacji. Wreszcie, typ nonclass `HowMuch` jest zainicjowany na 43.0.

Jeśli obiekt jest typu klasy i Klasa ma konstruktory (jak w poprzednim przykładzie), obiekt może zostać zainicjowany przez **`new`** operatora tylko wtedy, gdy spełniony jest jeden z następujących warunków:

- Argumenty dostarczone w inicjatorze zgadzają się z tymi z konstruktora.

- Klasa ma domyślny konstruktor (konstruktor, który można wywołać bez argumentów).

Nie można wykonać jawnej inicjalizacji dla elementu podczas alokowania tablic przy użyciu **`new`** operatora; wywoływana jest tylko Konstruktor domyślny, jeśli jest obecny. Aby uzyskać więcej informacji, zobacz [argumenty domyślne](../cpp/default-arguments.md) .

Jeśli alokacja pamięci nie powiedzie się (**operator new** zwraca wartość 0), inicjowanie nie jest wykonywane. Chroni to przed próbami inicjalizacji danych, które nie istnieją.

Podobnie jak w przypadku wywołań funkcji, kolejność oceny inicjowanych wyrażeń nie jest zdefiniowana. Ponadto, nie należy zakładać, że te wyrażenia zostaną całkowicie ocenione przed wykonaniem alokacji pamięci. Jeśli alokacja pamięci nie powiedzie się **`new`** , a operator zwróci wartość zero, niektóre wyrażenia w inicjatorze mogą nie być całkowicie oceniane.

## <a name="lifetime-of-objects-allocated-with-new"></a>Okres istnienia obiektów przyznanych przez nowe

Obiekty przyłączone do **`new`** operatora nie są niszczone, gdy zakres, w którym są zdefiniowane, zostało zakończone. Ponieważ **`new`** operator zwraca wskaźnik do obiektów, które są przydzielane, program musi zdefiniować wskaźnik z odpowiednim zakresem, aby uzyskać dostęp do tych obiektów. Na przykład:

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

Gdy wskaźnik `AnotherArray` wykracza poza zakres w tym przykładzie, nie można już usunąć obiektu.

## <a name="how-new-works"></a>Jak działa nowy

*Wyrażenie alokacji* — wyrażenie zawierające **`new`** operator — wykonuje trzy czynności:

- Lokalizuje i rezerwuje pamięć dla obiektu lub obiektów, które mają zostać przydzielone. Po ukończeniu tego etapu, poprawna ilość pamięci jest przydzielana, ale nie jest jeszcze obiektem.

- Inicjalizuje obiekt(y). Po zakończeniu inicjalizacji, wystarczająca ilość informacji jest obecna dla przydzielenia pamięci, która ma być obiektem.

- Zwraca wskaźnik do obiektów typu wskaźnika pochodzącego od *nowej nazwy typu* lub *nazwy typu*. Program używa tego wskaźnika do dostępu do nowo przydzielonego obiektu.

**`new`** Operator wywołuje **operator funkcji New**. W przypadku tablic dowolnego typu, a w przypadku obiektów, które nie **`class`** są **`struct`** typu,, lub **`union`** , funkcja globalna **:: operator new**jest wywoływana w celu przydzielenia magazynu. Obiekty typu klasy mogą definiować własne, **nowe** statyczne funkcje członkowskie dla poszczególnych klas.

Gdy kompilator napotka **`new`** operator do przydzielenia obiektu **typu typu**, wystawia wywołanie `type` **:: operator new (sizeof (** `type` **))** lub, jeśli nie zdefiniowano **operatora** zdefiniowanego przez użytkownika, **:: operator new (sizeof (** `type` **))**. W związku z tym **`new`** operator może przydzielić poprawną ilość pamięci dla obiektu.

> [!NOTE]
> Argumentem **operatora new** jest typ `size_t` . Ten typ jest zdefiniowany w,,,,,,, \<direct.h> \<malloc.h> \<memory.h> \<search.h> \<stddef.h> \<stdio.h> \<stdlib.h> \<string.h> , i \<time.h> .

Opcja gramatyki umożliwia określenie *położenia* (patrz Gramatyka dla [operatora new](../cpp/new-operator-cpp.md)). Parametru *umieszczania* można używać tylko dla implementacji **operatora new**zdefiniowanego przez użytkownika; umożliwia przekazywanie dodatkowych informacji do **operatora new**. Wyrażenie zawierające pole *umieszczania* , takie jak, `T *TObject = new ( 0x0040 ) T;` jest tłumaczone na `T *TObject = T::operator new( sizeof( T ), 0x0040 );` , jeśli Klasa T ma operator członkowski New, w przeciwnym razie `T *TObject = ::operator new( sizeof( T ), 0x0040 );` .

Pierwotny zamiar pola *położenie* polega na przydzieleniu obiektów zależnych od sprzętu w adresach określonych przez użytkownika.

> [!NOTE]
> Mimo że w poprzednim przykładzie pokazano tylko jeden argument w polu *umieszczania* , nie ma żadnych ograniczeń dotyczących liczby dodatkowych argumentów, które można przekazywać do **operatora** w ten sposób.

Nawet jeśli **operator new** został zdefiniowany dla typu klasy, operatora globalnego można używać przy użyciu formy tego przykładu:

```cpp
T *TObject =::new TObject;
```

Operator rozpoznawania zakresu ( `::` ) wymusza użycie **`new`** operatora globalnego.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[new i delete, operatory](../cpp/new-and-delete-operators.md)
