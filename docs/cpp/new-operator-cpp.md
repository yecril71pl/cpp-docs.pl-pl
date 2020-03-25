---
title: new — Operator (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 21e67f8d44673a15e5d3a5994597caae4cc01a2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161129"
---
# <a name="new-operator-c"></a>new — Operator (C++)

Przydziela pamięć dla obiektu lub tablicy obiektów *typu-Name* z wolnego sklepu i zwraca odpowiednio wpisany wskaźnik o wartości niezerowej do obiektu.

> [!NOTE]
>  Rozszerzenia C++ składników firmy Microsoft zapewniają obsługę **nowego** słowa kluczowego w celu dodania wpisów w gnieździe tablic wirtualnych. Aby uzyskać więcej informacji, zobacz [Nowość (nowe miejsce w tabeli metod wirtualnych)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Składnia

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Uwagi

W przypadku niepowodzenia funkcja **New** zwraca wartość zero lub zgłasza wyjątek. Aby uzyskać więcej informacji [, zobacz Operatory New i DELETE](../cpp/new-and-delete-operators.md) . To zachowanie domyślne można zmienić, pisząc procedurę niestandardowej obsługi wyjątków i wywołując [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) funkcję biblioteki wykonawczej z nazwą funkcji jako argumentem.

Aby uzyskać informacje na temat sposobu tworzenia obiektu na zarządzanym stosie, zobacz [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Gdy **Nowa** jest używana do przydzielania pamięci dla C++ obiektu klasy, Konstruktor obiektu jest wywoływany po przydzieleniu pamięci.

Użyj operatora [delete](../cpp/delete-operator-cpp.md) , aby cofnąć alokację pamięci przydzieloną za pomocą operatora **New** .

Poniższy przykład przydziela, a następnie zwalnia dwuwymiarową tablicę znaków o wielkości `dim` przez 10. Podczas alokowania tablicy wielowymiarowej wszystkie wymiary oprócz pierwszej muszą być wyrażeniami stałymi, które obliczają wartości dodatnie; wymiar tablicy z lewej strony może być dowolnym wyrażeniem, które daje w wyniku wartość dodatnią. Podczas alokowania tablicy przy użyciu operatora **New** pierwszy wymiar może mieć wartość zero — operator **New** zwraca unikatowy wskaźnik.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*Nazwa typu* nie może zawierać deklaracji **const**, **volatile**, Class lub Enumeration. W związku z tym następujące wyrażenie jest niedozwolone:

```cpp
volatile char *vch = new volatile char[20];
```

Operator **New** nie przydziela typów referencyjnych, ponieważ nie są obiektami.

Operatora **New** nie można użyć do przydzielenia funkcji, ale może służyć do przydzielania wskaźników do funkcji. Poniższy przykład przydziela i następnie zwalnia tablicę siedmiu wskaźników do funkcji, które zwracają liczby całkowite.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

W przypadku użycia operatora **New** bez żadnych dodatkowych argumentów i kompilowania przy użyciu opcji [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)lub [/EHS](../build/reference/eh-exception-handling-model.md) kompilator generuje kod, aby wywołać operator **delete** , jeśli Konstruktor zgłosi wyjątek.

Na poniższej liście opisano elementy gramatyki **nowych**:

*jęcia*<br/>
Zapewnia sposób przekazywania dodatkowych argumentów w przypadku przeciążenia **nowych**.

*Nazwa typu*<br/>
Określa typ do przydzielenia; może to być typ wbudowany lub zdefiniowany przez użytkownika. Jeśli specyfikacja typu jest skomplikowana, może być otoczona nawiasami, aby wymusić kolejność powiązań.

*skład*<br/>
Udostępnia wartość dla zainicjowanego obiektu. Nie można określić inicjatorów dla tablic. Operator **New** utworzy tablice obiektów tylko wtedy, gdy Klasa ma Konstruktor domyślny.

## <a name="example"></a>Przykład

Poniższy przykład kodu przydziela tablicę znaków i obiekt klasy `CName` a następnie zwalnia je.

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

Jeśli używasz nowej postaci rozmieszczenia operatora **New** , formularz z argumentami oprócz rozmiaru alokacji, kompilator nie obsługuje formy umieszczania operatora **delete** , jeśli Konstruktor zgłosi wyjątek. Na przykład:

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

Opcjonalne pole *inicjatora* jest zawarte w gramatyce dla operatora **New** . Dzięki temu nowe obiekty mogą zostać zainicjowane z konstruktorów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji na temat sposobu inicjowania, zobacz [inicjatory](../cpp/initializers.md). Poniższy przykład ilustruje sposób użycia wyrażenia inicjującego z operatorem **New** :

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

W tym przykładzie obiekt `CheckingAcct` jest przydzielony przy użyciu operatora **New** , ale nie określono domyślnej inicjalizacji. W związku z tym, wywoływany jest domyślny konstruktor dla klasy `Acct()`. Następnie obiekt `SavingsAcct` jest przydzielany ten sam sposób, chyba że wyraźnie jest zainicjowany na 34.98. Ponieważ 34,98 jest typu **Double**, Konstruktor, który przyjmuje argument tego typu, jest wywoływany do obsługi inicjalizacji. Wreszcie, typ nonclass `HowMuch` jest zainicjowany na 43.0.

Jeśli obiekt jest typu klasy i Klasa ma konstruktory (jak w poprzednim przykładzie), obiekt może zostać zainicjowany przez operatora **New** tylko w przypadku spełnienia jednego z następujących warunków:

- Argumenty dostarczone w inicjatorze zgadzają się z tymi z konstruktora.

- Klasa ma domyślny konstruktor (konstruktor, który można wywołać bez argumentów).

Podczas alokowania tablic przy użyciu operatora **New** nie można przeprowadzić jawnej inicjalizacji dla elementu. tylko Konstruktor domyślny, jeśli jest obecny, jest wywoływany. Aby uzyskać więcej informacji, zobacz [argumenty domyślne](../cpp/default-arguments.md) .

Jeśli alokacja pamięci nie powiedzie się (**operator new** zwraca wartość 0), inicjowanie nie jest wykonywane. Chroni to przed próbami inicjalizacji danych, które nie istnieją.

Podobnie jak w przypadku wywołań funkcji, kolejność oceny inicjowanych wyrażeń nie jest zdefiniowana. Ponadto, nie należy zakładać, że te wyrażenia zostaną całkowicie ocenione przed wykonaniem alokacji pamięci. Jeśli alokacja pamięci nie powiedzie się, a operator **New** zwróci wartość zero, niektóre wyrażenia w inicjatorze mogą nie być całkowicie oceniane.

## <a name="lifetime-of-objects-allocated-with-new"></a>Okres istnienia obiektów przyznanych przez nowe

Obiekty przyłączone za pomocą operatora **New** nie są niszczone, gdy zakres, w którym są zdefiniowane, zostało zakończone. Ponieważ operator **New** zwraca wskaźnik do obiektów, które są przydzielane, program musi zdefiniować wskaźnik z odpowiednim zakresem, aby uzyskać dostęp do tych obiektów. Na przykład:

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

*Wyrażenie alokacji* — wyrażenie zawierające operator **New** — ma trzy rzeczy:

- Lokalizuje i rezerwuje pamięć dla obiektu lub obiektów, które mają zostać przydzielone. Po ukończeniu tego etapu, poprawna ilość pamięci jest przydzielana, ale nie jest jeszcze obiektem.

- Inicjalizuje obiekt(y). Po zakończeniu inicjalizacji, wystarczająca ilość informacji jest obecna dla przydzielenia pamięci, która ma być obiektem.

- Zwraca wskaźnik do obiektów typu wskaźnika pochodzącego od *nowej nazwy typu* lub *nazwy typu*. Program używa tego wskaźnika do dostępu do nowo przydzielonego obiektu.

Operator **New** wywołuje **operator funkcji New**. W przypadku tablic dowolnego typu, a dla obiektów, które nie są typami **klas**, **struktur**lub **Unii** , funkcja globalna **:: operator new**jest wywoływana w celu przydzielenia magazynu. Obiekty typu klasy mogą definiować własne, **nowe** statyczne funkcje członkowskie dla poszczególnych klas.

Gdy kompilator napotka operator **New** do przydzielenia **obiektu typu typu,** wystawia wywołanie `type` **:: operator new (sizeof (** `type` **))** lub, jeśli nie zdefiniowano żadnego **operatora** zdefiniowanego przez użytkownika, **:: operator new (sizeof (** `type` **))** . W związku z tym operator **New** może przydzielić poprawną ilość pamięci dla obiektu.

> [!NOTE]
>  Argument dla **operatora new** jest typu `size_t`. Ten typ jest zdefiniowany w \<Direct. h >, \<malloc. h >, \<Memory. h >, \<Search. h >, \<STDDEF. h >, \<stdio. h >, \<STDLIB. h >, \<ciąg. h > i \<Time. h >.

Opcja gramatyki umożliwia określenie *położenia* (patrz Gramatyka dla [operatora new](../cpp/new-operator-cpp.md)). Parametru *umieszczania* można używać tylko dla implementacji **operatora new**zdefiniowanego przez użytkownika; umożliwia przekazywanie dodatkowych informacji do **operatora new**. Wyrażenie zawierające pole *umieszczania* , takie jak `T *TObject = new ( 0x0040 ) T;` jest tłumaczone na `T *TObject = T::operator new( sizeof( T ), 0x0040 );`, jeśli Klasa t ma operator członkowski New, w przeciwnym razie `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.

Pierwotny zamiar pola *położenie* polega na przydzieleniu obiektów zależnych od sprzętu w adresach określonych przez użytkownika.

> [!NOTE]
>  Mimo że w poprzednim przykładzie pokazano tylko jeden argument w polu *umieszczania* , nie ma żadnych ograniczeń dotyczących liczby dodatkowych argumentów, które można przekazywać do **operatora** w ten sposób.

Nawet jeśli **operator new** został zdefiniowany dla typu klasy, operatora globalnego można używać przy użyciu formy tego przykładu:

```cpp
T *TObject =::new TObject;
```

Operator rozpoznawania zakresu (`::`) wymusza użycie globalnego operatora **New** .

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[New i DELETE — operatory](../cpp/new-and-delete-operators.md)
