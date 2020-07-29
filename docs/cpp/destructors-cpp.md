---
title: Destruktory (C++)
ms.date: 07/20/2019
helpviewer_keywords:
- objects [C++], destroying
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
ms.openlocfilehash: 5da7659d2d45bca9efba21be2cd0bf581d539780
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221669"
---
# <a name="destructors-c"></a>Destruktory (C++)

Destruktor to funkcja członkowska, która jest wywoływana automatycznie, gdy obiekt wykracza poza zakres lub został jawnie zniszczony przez wywołanie **`delete`** . Destruktor ma taką samą nazwę jak Klasa, poprzedzone znakiem tyldy ( `~` ). Na przykład, destruktor dla klasy `String` jest zadeklarowany: `~String()` .

Jeśli nie zdefiniujesz destruktora, kompilator poda wartość domyślną. dla wielu klas jest to wystarczające. Musisz zdefiniować niestandardowy destruktor, gdy klasa przechowuje uchwyty do zasobów systemowych, które muszą zostać wydane, lub wskaźniki, do których wskazuje pamięć.

Rozważmy następującą deklarację `String` klasy:

```cpp
// spec1_destructors.cpp
#include <string>

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
   delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

W poprzednim przykładzie destruktor `String::~String` używa **`delete`** operatora w celu cofnięcia alokacji miejsca przydzieloną dynamicznie na potrzeby przechowywania tekstu.

## <a name="declaring-destructors"></a>Deklarowanie destruktorów

Destruktory są funkcjami o tej samej nazwie co Klasa, ale poprzedzone znakiem tyldy ( `~` )

Kilka zasad podlega deklaracji destruktorów. Destruktory

- Nie Akceptuj argumentów.

- Nie zwracaj wartości (lub **`void`** ).

- Nie można zadeklarować jako **`const`** , **`volatile`** lub **`static`** . Jednak mogą być wywoływane w celu zniszczenia obiektów zadeklarowanych jako **`const`** , **`volatile`** , lub **`static`** .

- Może być zadeklarowany jako **`virtual`** . Korzystając z destruktorów wirtualnych, można zniszczyć obiekty bez znajomości ich typu — poprawny destruktor dla obiektu jest wywoływany przy użyciu mechanizmu funkcji wirtualnej. Należy zauważyć, że destruktory mogą być również deklarowane jako czyste funkcje wirtualne dla klas abstrakcyjnych.

## <a name="using-destructors"></a>Używanie destruktorów

Destruktory są wywoływane, gdy wystąpi jedno z następujących zdarzeń:

- Lokalny (automatyczny) obiekt z zakresu bloku wykracza poza zakres.

- Obiekt przydzielony przy użyciu **`new`** operatora jest jawnie cofnięty przy użyciu **`delete`** .

- Kończy się okres istnienia obiektów tymczasowych.

- Program jest kończony oraz zamykane są obiekty globalne lub statyczne.

- Destruktor zostanie jawnie wywołany przy użyciu funkcji destruktora w pełni kwalifikowanej nazwy.

Destruktory mogą swobodnie wywoływać funkcje składowe klasy i uzyskać dostęp do danych składowych klasy.

Istnieją dwa ograniczenia dotyczące korzystania z destruktorów:

- Nie można przyjąć swojego adresu.

- Klasy pochodne nie dziedziczą destruktora swojej klasy bazowej.

## <a name="order-of-destruction"></a>Kolejność niszczenia

Gdy obiekt wykracza poza zakres lub jest usuwany, sekwencja zdarzeń w odniesieniu do kompletnego zniszczenia jest następująca:

1. Wywoływana jest destruktor klasy i jest wykonywana treść destruktora.

1. Destruktory dla niestatycznych obiektów członkowskich są wywoływane w odwrotnej kolejności, w której pojawiają się w deklaracji klasy. Opcjonalna lista inicjowania składowej użyta w przygotowaniu tych elementów członkowskich nie ma wpływu na kolejność konstruowania ani niszczenia.

1. Destruktory dla niewirtualnych klas bazowych są wywoływane w odwrotnej kolejności deklaracji.

1. Destruktory dla wirtualnych klas bazowych są wywoływane w odwrotnej kolejności deklaracji.

```cpp
// order_of_destruction.cpp
#include <cstdio>

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

Destruktory dla wirtualnych klas bazowych są wywoływane w odwrotnej kolejności ich wyglądu w bezpośrednim wymiarze acykliczne (głębokość-pierwsza, od lewej do prawej, przechodzenie postorder). Poniższy rysunek przedstawia wykres dziedziczenia.

![Wykres dziedziczenia, który pokazuje wirtualne klasy bazowe](../cpp/media/vc392j1.gif "Wykres dziedziczenia, który pokazuje wirtualne klasy bazowe") <br/>
Wykres dziedziczenia, który pokazuje wirtualne klasy bazowe

Poniżej wymieniono listę głowic klas dla klas przedstawionych na rysunku.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Aby określić kolejność niszczenia wirtualnych klas bazowych obiektu typu `E` , kompilator tworzy listę, stosując następujący algorytm:

1. Przechodzenie wykresu od lewej, rozpoczynając od głębokiego punktu na wykresie (w tym przypadku `E` ).

1. Wykonaj przechodzenie leftward, dopóki nie zostaną odwiedzone wszystkie węzły. Zanotuj nazwę bieżącego węzła.

1. Ponownie odwiedzaj poprzedni węzeł (w dół i w prawo), aby dowiedzieć się, czy zapamiętany węzeł jest wirtualną klasą bazową.

1. Jeśli zapamiętany węzeł jest wirtualną klasą bazową, Zeskanuj listę, aby sprawdzić, czy została już wprowadzona. Jeśli nie jest wirtualną klasą bazową, zignoruj ją.

1. Jeśli zapamiętany węzeł nie znajduje się jeszcze na liście, Dodaj go na końcu listy.

1. Przechodzenie grafu do góry i wzdłuż następnej ścieżki po prawej stronie.

1. Przejdź do kroku 2.

1. Po wyczerpaniu ostatniej ścieżki w górę Zanotuj nazwę bieżącego węzła.

1. Przejdź do kroku 3.

1. Kontynuuj ten proces, dopóki dolny węzeł nie zostanie ponownie bieżącym węzłem.

W związku z tym, w przypadku klasy `E` , kolejność niszczenia:

1. Niewirtualna Klasa bazowa `E` .

1. Niewirtualna Klasa bazowa `D` .

1. Niewirtualna Klasa bazowa `C` .

1. Wirtualna Klasa bazowa `B` .

1. Wirtualna Klasa bazowa `A` .

Ten proces powoduje utworzenie uporządkowanej listy unikatowych wpisów. Nazwa klasy nie występuje dwa razy. Gdy lista zostanie skonstruowana, jest ona przeszukiwana w kolejności odwrotnej i destruktor dla każdej klasy z listy od ostatniego do pierwszego jest wywoływany.

Kolejność konstrukcji lub niszczenia jest głównie ważna, gdy konstruktory lub destruktory w jednej klasie opierają się na innym składniku, który jest tworzony najpierw lub ciągle dłużej — na przykład, jeśli destruktor dla `A` (na rysunku pokazany powyżej) jest `B` nadal obecny podczas wykonywania kodu lub na odwrót.

Takie współzależności między klasami w grafie dziedziczenia są z natury niebezpieczne, ponieważ klasy pochodne później mogą zmieniać, która jest pierwszą ścieżką, zmieniając kolejność tworzenia i niszczenia.

### <a name="non-virtual-base-classes"></a>Niewirtualne klasy podstawowe

Destruktory dla niewirtualnych klas bazowych są wywoływane w odwrotnej kolejności, w której są zadeklarowane nazwy klas bazowych. Rozważmy następującą deklarację klasy:

```cpp
class MultInherit : public Base1, public Base2
...
```

W poprzednim przykładzie destruktor dla `Base2` jest wywoływany przed destruktorem dla `Base1` .

## <a name="explicit-destructor-calls"></a>Jawne wywołania destruktora

Jawne wywołanie destruktora jest rzadko konieczne. Może jednak być przydatne do czyszczenia obiektów umieszczonych w adresach bezwzględnych. Te obiekty są często przydzielono przy użyciu zdefiniowanego przez użytkownika **`new`** operatora, który przyjmuje argument umieszczania. **`delete`** Operator nie może cofnąć alokacji tej pamięci, ponieważ nie jest przydzieloną z wolnego magazynu (Aby uzyskać więcej informacji, zobacz [Operatory New i DELETE](../cpp/new-and-delete-operators.md)). Wywołanie do destruktora może jednak wykonać odpowiednie czyszczenie. Aby jawnie wywołać destruktor dla obiektu, `s` klasy `String` , należy użyć jednej z następujących instrukcji:

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

Notacja dla jawnych wywołań destruktorów, pokazana w poprzednim, może być używana bez względu na to, czy typ definiuje destruktor. Pozwala to na wykonywanie takich jawnych wywołań bez znajomości tego, czy destruktor jest zdefiniowany dla tego typu. Jawne wywołanie destruktora, gdzie żaden nie jest zdefiniowany, nie ma żadnego wpływu.

## <a name="robust-programming"></a>Niezawodne programowanie

Klasa wymaga destruktora, jeśli uzyskuje zasób i bezpiecznie zarządza zasobem, prawdopodobnie musi implementować Konstruktor kopiujący i przypisanie kopii.

Jeśli te funkcje specjalne nie są zdefiniowane przez użytkownika, są one niejawnie definiowane przez kompilator. Niejawnie wygenerowane konstruktory i operatory przypisania wykonują płytki, składowych kopię, która niemal nie występuje, jeśli obiekt zarządza zasobem.

W następnym przykładzie niejawnie wygenerowany Konstruktor kopiujący wykona wskaźniki `str1.text` i `str2.text` odwołuje się do tej samej pamięci, a po powrocie z `copy_strings()` , pamięć zostanie usunięta dwa razy, co jest zachowaniem niezdefiniowanym:

```cpp
void copy_strings()
{
   String str1("I have a sense of impending disaster...");
   String str2 = str1; // str1.text and str2.text now refer to the same object
} // delete[] _text; deallocates the same memory twice
  // undefined behavior
```

Jawne zdefiniowanie destruktora, konstruktora kopiującego lub operatora przypisania kopiowania uniemożliwia niejawną definicję konstruktora przenoszącego i operatora przypisania przenoszenia. W tym przypadku niepowodzenie udostępniania operacji przenoszenia jest zwykle, jeśli kopiowanie jest kosztowne, pominięta szansa optymalizacji.

## <a name="see-also"></a>Zobacz także

[Kopiuj konstruktory i skopiuj operatory przypisania](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)</br>
[Przenieś konstruktory i operatory przypisania przenoszenia](../cpp/move-constructors-and-move-assignment-operators-cpp.md)
