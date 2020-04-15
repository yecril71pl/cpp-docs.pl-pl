---
title: new — Operator (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367874"
---
# <a name="new-operator-c"></a>new — Operator (C++)

Przydziela pamięć dla obiektu lub tablicy obiektów o *nazwie typu* z magazynu wolnego i zwraca odpowiednio wpisany wskaźnik różny od zera do obiektu.

> [!NOTE]
> Rozszerzenia składników języka Microsoft C++ zapewniają obsługę **nowego** słowa kluczowego, aby dodać wpisy gniazda vtable. Aby uzyskać więcej informacji, zobacz [nowy (nowe gniazdo w vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Składnia

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Uwagi

Jeśli nie powiedzie się, **nowy** zwraca zero lub zgłasza wyjątek; Zobacz [Nowe i usuń operatorów, aby](../cpp/new-and-delete-operators.md) uzyskać więcej informacji. To domyślne zachowanie można zmienić, zapisując niestandardową procedurę obsługi wyjątków i wywołując _set_new_handler funkcję biblioteki [wykonywania](../c-runtime-library/reference/set-new-handler.md) z nazwą funkcji jako argumentem.

Aby uzyskać informacje na temat tworzenia obiektu na zarządzanym stosie, zobacz [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Gdy **nowy** jest używany do przydzielenia pamięci dla obiektu klasy C++, konstruktor obiektu jest wywoływana po przydzieleniu pamięci.

Operator [usuwania](../cpp/delete-operator-cpp.md) służy do usuwania alokacji pamięci przydzielonej **nowemu** operatorowi.

Poniższy przykład przydziela, a następnie zwalnia dwuwymiarową `dim` tablicę znaków o rozmiarze przez 10. Podczas przydzielania tablicy wielowymiarowej wszystkie wymiary z wyjątkiem pierwszego muszą być wyrażeniami stałymi, które są obliczane do wartości dodatnich; wymiar tablicy po lewej stronie może być dowolnym wyrażeniem, które ma wartość dodatnią. Podczas przydzielania tablicy przy użyciu **nowego** operatora pierwszy wymiar może być zerowy — **nowy** operator zwraca unikatowy wskaźnik.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*Nazwa typu* nie może zawierać **const,** **volatile,** deklaracji klas ani deklaracji wyliczenia. W związku z tym następujące wyrażenie jest niezgodne z prawem:

```cpp
volatile char *vch = new volatile char[20];
```

**Nowy** operator nie przydziela typów odwołań, ponieważ nie są one obiektami.

**Nowy** operator nie może służyć do przydzielenia funkcji, ale może służyć do przydzielania wskaźników do funkcji. Poniższy przykład przydziela, a następnie zwalnia tablicę siedmiu wskaźników do funkcji, które zwracają liczby całkowite.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Jeśli operator **jest nowy** bez żadnych dodatkowych argumentów i skompilować z [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), lub [/EHs](../build/reference/eh-exception-handling-model.md) opcji, kompilator wygeneruje kod do wywołania operator **delete,** jeśli konstruktor zgłasza wyjątek.

Na poniższej liście opisano elementy gramatyczne **nowych:**

*Umieszczenie*<br/>
Zapewnia sposób przekazywania dodatkowych argumentów w przypadku przeciążenia **nowego**.

*nazwa typu*<br/>
Określa typ do przydzielenia; może to być typ wbudowany lub zdefiniowany przez użytkownika. Jeśli specyfikacja typu jest skomplikowana, może być otoczona nawiasami, aby wymusić kolejność wiązania.

*Inicjatora*<br/>
Zapewnia wartość zainicjowanego obiektu. Nie można określić inicjatorów dla tablic. **Nowy** operator utworzy tablice obiektów tylko wtedy, gdy klasa ma domyślny konstruktor.

## <a name="example"></a>Przykład

Poniższy przykład kodu przydziela tablicę znaków `CName` i obiekt klasy, a następnie zwalnia je.

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

Jeśli używasz umieszczania nowy formularz **nowego** operatora, formularz z argumentami oprócz rozmiaru alokacji, kompilator nie obsługuje formę umieszczania **delete** operatora, jeśli konstruktor zgłasza wyjątek. Przykład:

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

## <a name="initializing-object-allocated-with-new"></a>Inicjowanie obiektu przydzielonego za pomocą nowego

Opcjonalne pole *inicjatora* jest zawarte w gramatyki dla **nowego** operatora. Dzięki temu nowe obiekty mogą zostać zainicjowane z konstruktorów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji na temat sposobu inicjowania, zobacz [Inicjatorzy](../cpp/initializers.md). Poniższy przykład ilustruje sposób używania wyrażenia inicjowania z **nowym** operatorem:

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

W tym przykładzie `CheckingAcct` obiekt jest przydzielany przy użyciu **nowego** operatora, ale nie określono domyślnej inicjalizacji. W związku z tym, wywoływany jest domyślny konstruktor dla klasy `Acct()`. Następnie obiekt `SavingsAcct` jest przydzielany ten sam sposób, chyba że wyraźnie jest zainicjowany na 34.98. Ponieważ 34.98 jest typu **double**, konstruktor, który przyjmuje argument tego typu jest wywoływana do obsługi inicjowania. Wreszcie, typ nonclass `HowMuch` jest zainicjowany na 43.0.

Jeśli obiekt jest typu klasy i tej klasy ma konstruktorów (jak w poprzednim przykładzie), obiekt może być zainicjowany przez **nowy** operator tylko wtedy, gdy jeden z tych warunków jest spełniony:

- Argumenty dostarczone w inicjatorze zgadzają się z tymi z konstruktora.

- Klasa ma domyślny konstruktor (konstruktor, który można wywołać bez argumentów).

Nie jawne inicjowanie na element można wykonać podczas przydzielania tablic przy użyciu **nowego** operatora; wywoływany jest tylko domyślny konstruktor, jeśli jest obecny. Aby uzyskać więcej informacji, zobacz [Domyślne argumenty.](../cpp/default-arguments.md)

Jeśli alokacja pamięci nie powiedzie się **(operator nowy** zwraca wartość 0), nie jest wykonywana inicjalizacja. Chroni to przed próbami inicjalizacji danych, które nie istnieją.

Podobnie jak w przypadku wywołań funkcji, kolejność oceny inicjowanych wyrażeń nie jest zdefiniowana. Ponadto, nie należy zakładać, że te wyrażenia zostaną całkowicie ocenione przed wykonaniem alokacji pamięci. Jeśli alokacja pamięci nie powiedzie się, a **nowy** operator zwraca zero, niektóre wyrażenia w inicjatorze mogą nie zostać całkowicie ocenione.

## <a name="lifetime-of-objects-allocated-with-new"></a>Okres istnienia obiektów przydzielonych z nowymi

Obiekty przydzielone z **nowym** operatorem nie są niszczone po zamknięciu zakresu, w którym są zdefiniowane. Ponieważ **nowy** operator zwraca wskaźnik do obiektów, które przydziela, program musi zdefiniować wskaźnik z odpowiednim zakresem, aby uzyskać dostęp do tych obiektów. Przykład:

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

Gdy wskaźnik `AnotherArray` wykracza poza zakres w przykładzie, obiekt nie można już usunąć.

## <a name="how-new-works"></a>Jak działają nowe

Wyrażenie *alokacji* — wyrażenie zawierające **nowy** operator — wykonuje trzy czynności:

- Lokalizuje i rezerwuje pamięć dla obiektu lub obiektów, które mają zostać przydzielone. Po ukończeniu tego etapu, poprawna ilość pamięci jest przydzielana, ale nie jest jeszcze obiektem.

- Inicjalizuje obiekt(y). Po zakończeniu inicjalizacji, wystarczająca ilość informacji jest obecna dla przydzielenia pamięci, która ma być obiektem.

- Zwraca wskaźnik do obiektów typu wskaźnika uzyskanego od *nazwy typu lub* nazwy *typu*. Program używa tego wskaźnika do dostępu do nowo przydzielonego obiektu.

**Nowy** operator wywołuje operator funkcji **nowy**. Dla tablic dowolnego typu i dla obiektów, które nie są **klasy**, **struct**lub **typów unii,** funkcja globalna, **::operator nowy**, jest wywoływana do alokacji magazynu. Obiekty typu klasy można zdefiniować własne **operator nowej** funkcji statycznego elementu członkowskiego na podstawie dla klasy.

Gdy kompilator napotka **nowy** operator do **type**przydzielenia obiektu `type`typu , generuje wywołanie **::operator new( sizeof(** `type` **) lub,** jeśli nie zdefiniowano **nowego operatora** zdefiniowanego przez użytkownika, **::operator new( sizeof(** `type` **) .** W związku z tym **nowy** operator może przydzielić odpowiednią ilość pamięci dla obiektu.

> [!NOTE]
> Argument do **operatora nowy** `size_t`jest typu . Ten typ jest \<definiowany w \<direct.h>, malloc.h>, \<memory.h>, \<search.h>, \<stddef.h \<>, stdio.h \<>, stdlib.h \<>, string.h> \<i time.h>.

Opcja w gramatyki umożliwia specyfikację *rozmieszczenia* (patrz Gramatyka dla [nowego operatora](../cpp/new-operator-cpp.md)). Parametr *umieszczania* może być używany tylko dla zdefiniowanych przez użytkownika implementacji **operatora new;** pozwala na przekazywanie dodatkowych informacji **operatorowi .** Wyrażenie z polem *umieszczania,* na przykład, `T *TObject = new ( 0x0040 ) T;` jest tłumaczone, `T *TObject = T::operator new( sizeof( T ), 0x0040 );` `T *TObject = ::operator new( sizeof( T ), 0x0040 );`jeśli klasa T ma nowy operator elementu członkowskiego, w przeciwnym razie na .

Pierwotną intencją pola *umieszczania* było zezwolenie na przydzielanie obiektów zależnych od sprzętu pod adresami określonymi przez użytkownika.

> [!NOTE]
> Chociaż w poprzednim przykładzie pokazano tylko jeden argument w polu *umieszczania,* nie ma żadnych ograniczeń co do liczby dodatkowych argumentów mogą być przekazywane do **operatora nowy** w ten sposób.

Nawet wtedy, gdy **operator nowy** został zdefiniowany dla typu klasy, operator globalny może służyć przy użyciu formularza w tym przykładzie:

```cpp
T *TObject =::new TObject;
```

Operator rozpoznawania zakresu`::`( ) wymusza użycie **globalnego nowego** operatora.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[nowe i usuwaj operatory](../cpp/new-and-delete-operators.md)
