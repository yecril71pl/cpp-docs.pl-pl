---
title: Typy trywialne, standardowe, pod i literałowe
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 6fe237386e63fcdd96621edabf2b0b66ce72e4f8
ms.sourcegitcommit: 435133128b18cdd02d33d929b16c33e7ec40e9eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81664135"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Typy trywialne, standardowe, pod i literałowe

Termin *układ* odnosi się do sposobu, w jaki elementy członkowskie obiektu klasy, struktury lub typu unii są rozmieszczone w pamięci. W niektórych przypadkach układ jest dobrze zdefiniowany przez specyfikację języka. Ale gdy klasa lub struktura zawiera niektóre funkcje języka C++, takie jak wirtualne klasy podstawowe, funkcje wirtualne, elementy członkowskie z inną kontrolą dostępu, kompilator może wybrać układ. Ten układ może się różnić w zależności od tego, jakie optymalizacje są wykonywane i w wielu przypadkach obiekt może nawet nie zajmować ciągłego obszaru pamięci. Na przykład jeśli klasa ma funkcje wirtualne, wszystkie wystąpienia tej klasy mogą współużytkować jedną tabelę funkcji wirtualnych. Takie typy są bardzo przydatne, ale mają również ograniczenia. Ponieważ układ jest niezdefiniowany, nie można go przekazać do programów napisanych w innych językach, takich jak C, a ponieważ mogą one `memcopy`być niesąsądowe, nie mogą być niezawodnie kopiowane za pomocą szybkich funkcji niskiego poziomu, takich jak , lub serializacji za pośrednictwem sieci.

Aby włączyć kompilatory, a także programy C++ i metaprogramy, aby rozsądek o przydatności danego typu dla operacji, które zależą od określonego układu pamięci, C ++ 14 wprowadził trzy kategorie prostych klas i struktur: *trywialne*, *standardowy układ*i *POD* lub Zwykły stary dane. Biblioteka standardowa zawiera `is_trivial<T>`szablony `is_pod<T>` funkcji, które określają, `is_standard_layout<T>` czy dany typ należy do danej kategorii.

## <a name="trivial-types"></a>Trywialne typy

Gdy klasa lub struktura w języku C++ ma kompilatora dostarczone lub jawnie domyślne funkcje elementów specjalnych elementów członkowskich, a następnie jest typu trywialnego. Zajmuje ciągły obszar pamięci. Może mieć członków z różnych specyfikatorów dostępu. W języku C++ kompilator może wybrać sposób zamawiania elementów członkowskich w tej sytuacji. W związku z tym można memcopy takich obiektów, ale nie można niezawodnie zużywać je z programu C. Trywialny typ T można skopiować do tablicy char lub niepodpisanego char i bezpiecznie skopiować z powrotem do zmiennej T. Należy zauważyć, że ze względu na wymagania dotyczące wyrównania, może być dopełnienie bajtów między członkami typu.

Typy trywialne mają trywialny konstruktor domyślny, konstruktor kopii trywialne, operator przypisywania trywialne kopiowanie i destruktor trywialny. W każdym przypadku *trywialny* oznacza, że konstruktor/operator/destruktor nie jest dostarczany przez użytkownika i należy do klasy, która

- brak funkcji wirtualnych lub wirtualnych klas podstawowych,

- brak klas podstawowych z odpowiednim nietrywialnym konstruktorem/operatorem/destruktorem

- brak elementów członkowskich danych typu klasy z odpowiednim nietrywialnym konstruktorem/operatorem/destruktorem

Poniższe przykłady pokazują typy trywialne. W Trivial2 obecność konstruktora `Trivial2(int a, int b)` wymaga podania domyślnego konstruktora. Aby typ kwalifikował się jako trywialny, należy jawnie domyślnie tego konstruktora.

```cpp
struct Trivial
{
   int i;
private:
   int j;
};

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>Standardowe typy układu

Gdy klasa lub struktura nie zawiera niektórych funkcji języka C++, takich jak funkcje wirtualne, które nie znajdują się w języku C, a wszystkie elementy członkowskie mają tę samą kontrolę dostępu, jest to typ układu standardowego. Jest w stanie memkopii i układ jest wystarczająco zdefiniowany, że może być spożywane przez programy C. Typy układu standardowego mogą mieć zdefiniowane przez użytkownika specjalne funkcje członkowskie. Ponadto standardowe typy układu mają następujące cechy:

- brak funkcji wirtualnych lub wirtualnych klas podstawowych

- wszystkie elementy członkowskie danych niestatycznych mają taką samą kontrolę dostępu

- wszystkie niestatyczne elementy członkowskie typu klasy są układem standardowym

- wszystkie klasy podstawowe są standardowym układem

- nie ma klas podstawowych tego samego typu co pierwszy element członkowski danych niestatycznych.

- spełnia jeden z następujących warunków:

  - brak niestatycznego elementu członkowskiego danych w klasie najbardziej pochodnej i nie więcej niż jedną klasę podstawową z niestatycznymi elementami członkowskimi danych, lub

  - nie ma klas podstawowych z niestatycznymi członkami danych

Poniższy kod przedstawia jeden przykład typu układu standardowego:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

Dwa ostatnie wymagania mogą być lepiej zilustrowane kodem. W następnym przykładzie, mimo że Base `Derived` jest układem standardowym, nie jest układem standardowym, ponieważ zarówno on (klasa najbardziej pochodna), jak i `Base` niestatyczne elementy członkowskie danych:

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

W tym `Derived` przykładzie jest `Base` standardowy układ, ponieważ nie ma niestatycznych elementów członkowskich danych:

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

Pochodne będzie również standardowy `Base` układ, jeśli `Derived` miał elementy członkowskie danych i miał tylko funkcje członkowskie.

## <a name="pod-types"></a>Typy POD

Gdy klasa lub struktura jest zarówno trywialne i standardowy układ, jest pod (zwykły stary dane) typu. Układ pamięci typów POD jest zatem ciągły i każdy element członkowski ma wyższy adres niż element członkowski, który został zadeklarowany przed nim, dzięki czemu bajt dla kopii bajtów i binarne we/wy mogą być wykonywane na tych typach.  Typy skalarne, takie jak int, są również typami POD. POD typy, które są klasy mogą mieć tylko pod typów jako niestatycznych elementów członkowskich danych.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia różnice między typami trywialne, standardowy układ i POD:

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
   int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
{
   int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal-types"></a><a name="literal_types"></a>Typy literały

Typ literału jest taki, którego układ można określić w czasie kompilacji. Oto typy dosłowne:

- void
- typy skalarne
- odwołania
- Tablice pustych, skalarnych typów lub odwołań
- Klasa, która ma destruktora trywialny i jeden lub więcej konstruktorów constexpr, które nie są przenieść lub skopiować konstruktorów. Ponadto wszystkie jego niestatyczne elementy członkowskie danych i klasy podstawowe muszą być typami literału i nie są zmienne.

## <a name="see-also"></a>Zobacz też

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
