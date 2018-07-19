---
title: Destruktory (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], destroying
- Visual C++, destructors
- destroying objects, destructors
- ~ operator [C++], specifying destructors
- destructors, about destructors
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bbe849f8ec9d47c73b7d909734df600957f3afd
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941788"
---
# <a name="destructors-c"></a>Destruktory (C++)

Destruktor jest funkcją składową, która jest wywoływana automatycznie, gdy obiekt wykracza poza zakres lub jest wyraźnie zniszczone przez wywołanie **Usuń**. Destruktor ma taką samą nazwę jak klasa, poprzedzony tyldy (`~`). Na przykład, destruktor klasy `String` jest zadeklarowana: `~String()`.

Jeżeli nie zdefiniujesz destruktora, kompilator zapewnia domyślny; wiele klas jest to wystarczające. Musisz zdefiniować niestandardowe destruktor, jeśli klasa przechowuje dojścia do zasobów systemowych, które muszą zostać zwolnione lub wskaźników, które są właścicielami pamięć wskazują na.

Rozważmy następującą deklarację elementu `String` klasy:

```cpp
// spec1_destructors.cpp
#include <string.h>

class String {
public:
   String( char *ch );  // Declare constructor
   ~String();           //  and destructor.
private:
   char    *_text;
   size_t  sizeOfText;
};

// Define the constructor.
String::String( char *ch ) {
   sizeOfText = strlen( ch ) + 1;

   // Dynamically allocate the correct amount of memory.
   _text = new char[ sizeOfText ];

   // If the allocation succeeds, copy the initialization string.
   if( _text )
      strcpy_s( _text, sizeOfText, ch );
}

// Define the destructor.
String::~String() {
   // Deallocate the memory that was previously reserved
   //  for this string.
   if (_text)
      delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

W poprzednim przykładzie, destruktor `String::~String` używa **Usuń** operator można cofnąć alokacji miejsca, przydzielany dynamicznie do przechowywania tekstu.

## <a name="declaring-destructors"></a>Deklarowanie destruktorów

Destruktory są funkcje z taką samą nazwę jak klasa, ale poprzedzającą tyldy (`~`)

Kilka decydującymi o deklaracji destruktorów. Destruktory:

- Nie akceptuje argumentów.

- Nie zwraca wartości (lub **void**).

- Nie można zadeklarować jako **const**, **volatile**, lub **statyczne**. Jednak ich może być wywołana dla zniszczenie obiektów zadeklarowane jako **const**, **volatile**, lub **statyczne**.

- Mogą być deklarowane jako **wirtualnego**. Używanie destruktorów wirtualnych, nie wiedząc o tym ich typ może zniszczyć obiektów — poprawne destruktor obiektu jest wywoływana przy użyciu mechanizmu funkcję wirtualną. Należy pamiętać, że destruktory mogą być także zadeklarowane jako czystych funkcji wirtualnych dla klasy abstrakcyjnej.

## <a name="using-destructors"></a>Używanie destruktorów

Destruktory są wywoływane, gdy wystąpi jedno z następujących zdarzeń:

- Lokalny (automatyczny) obiekt z zakresu bloku wykracza poza zakres.

- Obiekt przydzielony za pomocą **nowe** operator jest jawnie dealokowany za pomocą **Usuń**.

- Kończy się okres istnienia obiektów tymczasowych.

- Program jest kończony oraz zamykane są obiekty globalne lub statyczne.

- Destruktor zostanie jawnie wywołany przy użyciu funkcji destruktora w pełni kwalifikowanej nazwy.

Destruktory mogą swobodnie wywoływać funkcje składowe klasy i uzyskać dostęp do danych składowych klasy.

Istnieją dwa ograniczenia dotyczące stosowania destruktorów:

- Nie można przyjąć adresu.

- Klasy pochodne nie dziedziczą destruktor klasy podstawowej.

## <a name="order-of-destruction"></a>Kolejność likwidacji

Gdy obiekt wykracza poza zakres lub został usunięty, sekwencję zdarzeń zachodzących w jego całkowite zniszczenie jest następująca:

1. Destruktor klasy jest wywoływany i treści funkcji — destruktor jest wykonywany.

1. Destruktory dla obiektów niestatycznej składowej są wywoływane w odwrotnej kolejności, w jakiej występują w deklaracji klasy. Listy inicjowania opcjonalny element członkowski, które są używane w konstrukcji te elementy członkowskie nie ma wpływu na kolejność utworzenia lub zniszczenia.

1. Destruktory — wirtualne klasy bazowe są wywoływane w odwrotnej kolejności deklaracji.

1. Destruktory dla wirtualnych klas bazowych są wywoływane w odwrotnej kolejności deklaracji.

```cpp
// order_of_destruction.cpp
#include <stdio.h>

struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };

struct B1      { ~B1() { printf("B1 dtor\n"); } };
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };

int main() {
   A1 * a = new A3;
   delete a;
   printf("\n");

   B1 * b = new B3;
   delete b;
   printf("\n");

   B3 * b2 = new B3;
   delete b2;
}

Output: A3 dtor
A2 dtor
A1 dtor

B1 dtor

B3 dtor
B2 dtor
B1 dtor

```

### <a name="virtual-base-classes"></a>Wirtualne klasy bazowe

Destruktory dla wirtualnych klas bazowych są wywoływane w odwrotnej kolejności ich występowania w skierowanym grafie acyklicznym (pierwszy głębi, od lewej do prawej, postorder przechodzenia). Poniższa ilustracja przedstawia Wykres dziedziczenia.

![Wykres dziedziczenia, który pokazuje wirtualne klasy bazowe](../cpp/media/vc392j1.gif "vc392J1")

Wirtualne klasy bazowe Wykres dziedziczenia

Poniższa lista zawiera głowic klasy dla klasy pokazano na rysunku.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Aby określić kolejność niszczenia wirtualne klasy bazowe obiektu typu `E`, kompilator tworzy listę, stosując następującego algorytmu:

1. Graf w lewo, począwszy od najniższej punkt na wykresie (w tym przypadku `E`).

1. Leftward przejścia należy wykonać, aż wszystkie węzły odwiedzających. Zanotuj nazwę bieżącego węzła.

1. Ponownie poprzedniego węzła (w dół i w prawo), aby sprawdzić, czy węzeł są zapamiętywane wirtualnej klasy bazowej.

1. Jeśli zapamiętanych węzeł jest wirtualnej klasy bazowej, skanowania na liście, aby zobaczyć, czy jego został już wprowadzony. Jeśli nie jest wirtualną klasę bazową, należy go zignorować.

1. Jeśli węzeł zapamiętanych, nie jest jeszcze na liście, należy dodać go do dolnej części listy.

1. Graf w górę i w ścieżce dalej z prawej strony.

1. Przejdź do kroku 2.

1. Po wyczerpaniu ścieżkę górę ostatni Zanotuj nazwę bieżącego węzła.

1. Przejdź do kroku 3.

1. Kontynuacja ten proces dla węzła dolnej jest ponownie bieżącego węzła.

W związku z tym, dla klasy `E`, kolejność zniszczenia jest:

1. Wirtualnej klasy bazowej `E`.

1. Wirtualnej klasy bazowej `D`.

1. Wirtualnej klasy bazowej `C`.

1. Wirtualna klasa bazowa `B`.

1. Wirtualna klasa bazowa `A`.

Ten proces tworzy uporządkowaną listę unikatowych wpisów. Brak nazwy klasy pojawia się dwukrotnie. Gdy lista jest konstruowany, zostaje przeprowadzony w odwrotnej kolejności i destruktor dla każdej klasy na liście w ciągu ostatnich do pierwszego jest wywoływany.

Kolejność utworzenia lub zniszczenia jest szczególnie ważne w przypadku, gdy konstruktorów i destruktorów na jednych zajęciach zależą od innych składników tworzona pierwszy lub utrwalanie już — na przykład, jeśli destruktor dla `A` opiera się (w ilustracji pokazano powyżej) na `B` nadal jest obecna, gdy jego kod jest wykonywany, lub na odwrót.

Takie współzależności między klasami w programie graph dziedziczenia są założenia niebezpieczne, ponieważ klasy pochodne później można zmienić, czyli ścieżkę skrajnie po lewej stronie, zmieniając kolejność konstrukcje i zniszczenie ruchu.

### <a name="non-virtual-base-classes"></a>Niewirtualne klasy bazowe

Destruktory — wirtualne klasy bazowe są wywoływane w odwrotnej kolejności, w której nazwy klasy bazowej są deklarowane. Rozważmy następującą deklarację klasy:

```cpp
class MultInherit : public Base1, public Base2
...
```

W poprzednim przykładzie, destruktor dla `Base2` jest wywoływana przed destruktor dla `Base1`.

## <a name="explicit-destructor-calls"></a>Jawne wywołania destruktora

Jawne wywołania destruktora rzadko jest niezbędne. Jednak może być przydatne do wykonywania oczyszczania obiektów umiejscowiony adresów bezwzględnych. Te obiekty są często są przydzielane przy użyciu zdefiniowanej przez użytkownika **nowe** operator, który przyjmuje argument umieszczania. **Usuń** operator nie cofnięcie przydziału tej pamięci, ponieważ nie jest on przydzielany z wolnym magazynie (Aby uzyskać więcej informacji, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md)). Po wywołaniu destruktora, można jednak wykonać odpowiednie oczyszczania. Aby jawnie wywołać destruktor obiektu `s`, klasy `String`, użyj jednej z następujących instrukcji:

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

Notacja do jawnych wywołań destruktory, pokazano w poprzednim, należy używać niezależnie od tego, czy typ Określa destruktor. Dzięki temu można wykonywać takich jawnych wywołań nie wiedząc o tym, jeśli destruktor jest zdefiniowany dla typu. Jawne wywołania destruktora, w którym definiowany jest none nie ma znaczenia.
