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
ms.openlocfilehash: 64d75946d3ae9c1de1d59d74100de68a3b27dcc8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704805"
---
# <a name="destructors-c"></a>Destruktory (C++)

Destruktora jest funkcją członkowską, która jest wywoływana automatycznie, gdy obiekt wykracza poza zakres lub jawnie zostanie zniszczony przez wywołanie do `delete`. Destruktor ma taką samą nazwę jak klasa poprzedzone tyldy (`~`). Na przykład destruktora dla klasy `String` zadeklarowano: `~String()`.

Jeśli nie zostanie zdefiniowana destruktor, kompilator zapewni domyślny; wiele klas są wystarczające. Konieczne jest zdefiniowanie destruktora niestandardowych, jeśli klasa przechowuje dojść do zasobów systemowych, które muszą zostać zwolniony, lub wskaźników, które posiadają pamięć one wskazywać.

Należy wziąć pod uwagę następujące deklaracja `String` klasy:

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

W powyższym przykładzie destruktor `String::~String` używa `delete` operatora, aby zwolnić miejsce dynamicznie przydzielonego do przechowywania tekstu.

## <a name="declaring-destructors"></a>Deklarowanie destruktorów

Destruktory są funkcje z taką samą nazwę jak klasy, ale poprzedzającą tyldy (`~`)

Kilka reguł określają deklaracji destruktorów. Destruktory:

- Nie akceptuje argumentów.

- Nie zwraca wartości (lub `void`).

- Nie można zadeklarować jako **const**, **volatile**, lub **statycznych**. Jednak ich może być wywoływana dla niszczenie obiektów zadeklarowany jako **const**, **volatile**, lub **statycznych**.

- Mogą być deklarowane jako **wirtualnego**. Używanie destruktorów wirtualnego, można zniszczyć obiektów bez uprzedniego uzyskania informacji o ich typ — destruktor poprawne dla obiekt jest wywoływana przy użyciu mechanizmu funkcji wirtualnej. Należy pamiętać, że destruktory mogą również być deklarowane jako czystych funkcji wirtualnych dla klasy abstrakcyjnej.

## <a name="using-destructors"></a>Używanie destruktorów

Destruktory są wywoływane, gdy wystąpi jedno z następujących zdarzeń:

- Lokalny (automatyczny) obiekt z zakresu bloku wykracza poza zakres.

- Obiekt przydzielony przy użyciu **nowe** operator jawnie cofnięciu przydziału przy użyciu **usunąć**.

- Kończy się okres istnienia obiektów tymczasowych.

- Program jest kończony oraz zamykane są obiekty globalne lub statyczne.

- Destruktor zostanie jawnie wywołany przy użyciu funkcji destruktora w pełni kwalifikowanej nazwy.

Destruktory mogą swobodnie wywoływać funkcje składowe klasy i uzyskać dostęp do danych składowych klasy.

Istnieją dwa ograniczenia na używanie destruktorów:

- Nie można przyjąć adresu.

- klasy pochodne nie dziedziczą destruktor klasy podstawowej.

## <a name="order-of-destruction"></a>Kolejność likwidacji

Gdy obiekt wykracza poza zakres lub zostanie usunięta, kolejność zdarzeń w jego całkowite zniszczenie następująco:

1. Destruktor klasy jest wywoływany i treści funkcji destruktora jest wykonywana.

1. W odwrotnej kolejności, w jakiej występują w deklaracji klasy zostaną wywołane destruktory dla obiektów niestatycznego elementu członkowskiego. Opcjonalny element członkowski listy inicjowania używany w konstrukcji tych elementów członkowskich nie ma wpływu na kolejność utworzenia lub zniszczenia.

1. W odwrotnej kolejności deklaracji zostaną wywołane destruktory dla niewirtualnych klas podstawowych.

1. W odwrotnej kolejności deklaracji zostaną wywołane destruktory dla wirtualnych klas podstawowych.

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

### <a name="virtual-base-classes"></a>Wirtualne klasy podstawowe

W odwrotnej kolejności ich wyglądu w ukierunkowanego wykresu acyklicznego (pierwszy głębokość, od lewej do prawej, postorder przechodzenie) zostaną wywołane destruktory dla wirtualnych klas podstawowych. Poniższa ilustracja przedstawia Wykres dziedziczenia.

![Wykres dziedziczenia, który pokazuje wirtualne klasy podstawowe](../cpp/media/vc392j1.gif "vc392J1")

Wykres dziedziczenia przedstawiający wirtualne klasy podstawowe

Poniższa lista zawiera głowic klasy dla klasy pokazano na rysunku.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Aby określić kolejność likwidacji wirtualne klasy podstawowe obiektu typu `E`, kompilator tworzy listę, stosując następującego algorytmu:

1. Przechodzenie przez wykres w lewo, zaczynając od najgłębszym punktów na wykresie (w tym przypadku `E`).

1. Wykonywać leftward traversals, dopóki wszystkie węzły zostały odwiedzone. Zanotuj nazwę bieżącego węzła.

1. Kontroluj poprzedniego węzła (w dół i w prawo), aby sprawdzić, czy węzeł są zapamiętywane wirtualnej klasy podstawowej.

1. Jeśli węzeł zapamiętanych jest wirtualna klasa podstawowa, skanowania listy, aby zobaczyć, czy jego został już wprowadzony. Jeśli nie jest wirtualna klasa podstawowa, można je zignorować.

1. Jeśli zapamiętanych węzeł nie jest jeszcze na liście, dodaj go do dolnej części listy.

1. Przechodzenie przez wykres w górę i w ścieżce dalej z prawej strony.

1. Przejdź do kroku 2.

1. Podczas ostatniego ścieżki górę odbywa się częściej, zanotuj nazwę bieżącego węzła.

1. Przejdź do kroku 3.

1. Kontynuacja ten proces dla węzła dolnej jest ponownie bieżącego węzła.

W związku z tym dla klasy `E`, kolejność likwidacji jest:

1. -Wirtualna klasa podstawowa `E`.

1. -Wirtualna klasa podstawowa `D`.

1. -Wirtualna klasa podstawowa `C`.

1. Wirtualna klasa podstawowa `B`.

1. Wirtualna klasa podstawowa `A`.

Ten proces tworzy uporządkowaną listę unikatowych wpisów. Brak nazwy klasy występuje dwa razy. Po liście jest tworzony, jest udał w odwrotnej kolejności i nosi nazwę destruktor dla każdej z klas na liście w ciągu ostatnich jako pierwszy.

Kolejność utworzenia lub zniszczenia jest szczególnie ważne w przypadku konstruktorów ani destruktorów w jednej klasie zależą od innych składników tworzona pierwszy lub trwałych już — na przykład, jeśli destruktor dla elementu `A` (na ilustracji przedstawionych powyżej) stosowane na `B` nadal jest obecny podczas jego kod wykonywany, albo na odwrót.

Takie współzależności między klasami wykresie dziedziczenia są z założenia niebezpieczne, ponieważ klasy pochodne później można zmienić, czyli ścieżkę po lewej stronie, zmieniając kolejność konstruowania i zniszczenia.

### <a name="non-virtual-base-classes"></a>Niewirtualne klasy podstawowe

Destruktory dla niewirtualnych klas podstawowych są nazywane w odwrotnej kolejności, w którym są deklarowane jako nazwy klasy podstawowej. Należy wziąć pod uwagę następujące deklaracji klasy:

```cpp
class MultInherit : public Base1, public Base2
...
```

W powyższym przykładzie destruktor dla elementu `Base2` jest wywoływana przed destruktor dla elementu `Base1`.

## <a name="explicit-destructor-calls"></a>Jawne wywołania destruktora

Jawne wywołania destruktora jest rzadko niezbędne. Jednak może być przydatne do wykonania oczyszczania obiektów w adresów bezwzględnych. Te obiekty najczęściej są przydzielane za pomocą zdefiniowane przez użytkownika **nowe** operator, który przyjmuje argument umieszczania. **Usunąć** operator nie deallocate tej pamięci, ponieważ nie jest przydzielona w sklepie wolnego (Aby uzyskać więcej informacji, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md)). Wywołanie destruktora, można jednak wykonać odpowiednie oczyszczania. Aby jawnie wywołać destruktor dla obiekt `s`, klasy `String`, użyj jednej z następujących instrukcji:

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

Notacja dla jawnego wywołania destruktory wyświetlany w poprzednim, można niezależnie od tego, czy typ definiuje destruktor. Dzięki temu można spowodować takie jawnego wywołania bez wiedzy o Jeśli destruktora jest zdefiniowany dla typu. Jawne wywołania destruktora, w którym zdefiniowana jest brak nie ma znaczenia.
