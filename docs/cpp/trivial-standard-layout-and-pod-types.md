---
title: Prosta, standardowego układu, ZASOBNIKÓW i typy literałów
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: a1ab49e9e2813d0debc77e6a2ff02ec85bb9aeb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568489"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Prosta, standardowego układu, ZASOBNIKÓW i typy literałów

Termin *układ* odwołuje się do sposób rozmieszczenia elementów członkowskich obiektu klasy, struktury lub Unii w pamięci. W niektórych przypadkach układ jest dobrze zdefiniowany przez specyfikację języka. Ale jeśli klasa lub struktura zawiera niektórych funkcji języka C++, takich jak wirtualne klasy bazowe, funkcji wirtualnych elementów członkowskich przy użyciu kontroli dostępu w różnych, następnie kompilator swobodę wyboru układu. Taki układ mogą się różnić w zależności od tego, jakie optymalizacje wykonywane i w wielu przypadkach obiektu może nie nawet zajmować ciągły obszar pamięci. Na przykład jeśli klasa ma funkcje wirtualne, wszystkie wystąpienia tej klasy może udostępniać tabeli jednej funkcji wirtualnej. Typy takie oczywiście są bardzo przydatne, ale mają ograniczenia. Ponieważ układ jest niezdefiniowana nie mogą być przekazywane do programów napisanych w innych językach, takich jak C, a ponieważ mogą one być nieciągłych one nie można niezawodnie skopiować przy użyciu funkcji szybkiego niskiego poziomu takich jak `memcopy` lub serializowana za pośrednictwem sieci.

Aby włączyć programy w języku C++, a także metaprograms przeglądanie informacji o gotowości każdego typu operacji, które są zależne od układu pamięci i Kompilatory języka, C ++ 14 wprowadzone trzy kategorie proste klasy i struktury: *prosta*, *standardowego układu*, i *ZASOBNIKA* lub zwykłe stare dane. Standardowa biblioteka zawiera szablony funkcji `is_trivial<T>`, `is_standard_layout<T>` i `is_pod<T>` określające, czy dany typ należy do danej kategorii.

## <a name="trivial-types"></a>Typy proste

Po klasie lub strukturze w języku C++ ma podane do kompilatora lub jawnie przyjmujące wartości domyślne funkcji specjalnych elementów członkowskich, a następnie jest typem prosta. Zajmuje obszar pamięci ciągłej. Może mieć elementów członkowskich z specyfikatory różnych dostępu. W języku C++ kompilator jest bezpłatne wybierz sposób uporządkowania elementów członkowskich w takiej sytuacji. Dlatego możesz memcopy takie obiekty, ale nie można niezawodnie korzystać z programu C. Prosta typu T można kopiowana do tablicy znaków lub unsigned char i bezpieczne kopiowanie do zmiennej T. Należy pamiętać, że ze względu na wymagania wyrównania, może być bajtów uzupełniających między elementy członkowskie typu.

Proste typy mają trivial domyślnego konstruktora, Konstruktor kopiujący prosta, operator przypisania kopiowania prosta i prosta — destruktor. W każdym przypadku *trivial* oznacza, że Konstruktor/operator/destruktor nie jest dostarczony przez użytkownika i należy do klasy, która ma

- nie funkcji wirtualnych lub wirtualne klasy bazowe,

- nie klas bazowych nietrywialnymi odpowiedniego konstruktora/operator/destruktora

- żadnych składowych danych typu klasy z nietrywialnymi odpowiedniego konstruktora/operator/destruktorem

W poniższych przykładach pokazano typy proste. W Trivial2, obecności `Trivial2(int a, int b)` Konstruktor wymaga podania domyślnego konstruktora. Dla typu zakwalifikować się jak prosta możesz jawnie tworzyć domyślne tego konstruktora.

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

## <a name="standard-layout-types"></a>Typy standardowego układu

Gdy klasa lub struktura nie zawierać niektórych funkcji języka C++, takich jak funkcje wirtualne, które nie znajdują się w języku C, a wszyscy członkowie mają ten sam kontroli dostępu, jest to typ standardowego układu. Jest w stanie memcopy i czy mogą być używane przez programy c. wystarczająco zdefiniowany układ. Typy standardowego układu mogą mieć zdefiniowane przez użytkownika specjalnych funkcji Członkowskich. Ponadto typy standardowego układu ma następującą charakterystykę:

- nie funkcji wirtualnych lub wirtualne klasy bazowe

- Wszyscy członkowie danych niestatycznych mają ten sam kontroli dostępu

- wszystkie składowe niestatycznych o typie klasy są bezpieczne standardowego układu

- żadnych klas bazowych są standardowego układu

- ma nie mają tego samego typu jako pierwszy element członkowski danych niestatycznych klas bazowych.

- spełnia jeden z następujących warunków:

  - nie niestatyczny element członkowski w najbardziej pochodnego klasy i nie więcej niż jedną klasę bazową przy użyciu danych niestatycznych elementów członkowskich, lub

  - ma nie klas bazowych danych niestatycznych elementów członkowskich

Poniższy kod przedstawia przykład tego typu standardowego układu:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

Ostatnie dwa wymagania mogą być może lepiej zilustrowane konkretnymi kodu. Mimo że w następnym przykładzie podstawowy jest standardowego układu `Derived` nie jest standardowego układu, ponieważ zarówno przez dział it (najbardziej pochodnej klasy) i `Base` mają danych niestatycznych elementów członkowskich:

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

W tym przykładzie `Derived` jest standardowego układu ponieważ `Base` nie ma danych niestatycznych elementów członkowskich:

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

Pochodne będą również standardowego układu Jeśli `Base` miał składowych danych i `Derived` miał tylko elementów członkowskich.

## <a name="pod-types"></a>Typy POD

Gdy klasa lub struktura jest prosta i standardowego układu, jest typem POD (zwykłe stare dane). Układ pamięci typów POD w związku z tym jest ciągły, a każdy element członkowski ma adres wyższe niż elementu członkowskiego, który został zadeklarowany, tak, aby kopiuje bajtu na potrzeby bajtów i binarny we/wy, które mogą być wykonywane na tych typach.  Typy skalarne, takie jak int są również typy POD. Typy POD, które są klasy mogą być tylko typy POD danych niestatycznych elementów członkowskich.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono różnice między prosta, standardowego układu oraz typy ZASOBNIKA:

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

## <a name="literal_types"></a> Typy literałów

Literał jest jednym którego układ można określić w czasie kompilacji. Dostępne są następujące typy literałów:

- void
- typy skalarne
- odwołania
- Tablice void, typów skalarnych lub odwołuje się do
- Klasa, która ma destruktor proste, a konstruktory constexpr, które nie są przenoszenie lub kopiowanie konstruktorów. Ponadto wszystkie jej elementy członkowskie danych niestatyczna i klas bazowych musi być typy literałów i nie jest nietrwały.

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)