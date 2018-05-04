---
title: Prosta, układ standard, POD i typy literału | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 7a80db109df1d9aa25f471312a9ff7103b90df7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Prosta, układ standard, POD i typy literału

Termin *układu* odwołuje się do sposób rozmieszczenia elementów członkowskich obiektu klasy, struktury lub Unii w pamięci. W niektórych przypadkach układ jest dobrze zdefiniowany przez specyfikację języka. Jednak po klasie lub strukturze zawiera niektóre funkcje języka C++, takie jak wirtualne klasy podstawowe funkcje wirtualne, elementy członkowskie z kontrolą dostępu na różnych, następnie kompilator będzie mógł wybrać układ. Taki układ może się różnić w zależności od tego, jakie funkcje optymalizacji są wykonywane i w wielu przypadkach obiekt może nie nawet zajmują ciągły obszar pamięci. Na przykład jeśli klasa ma funkcje wirtualne, wszystkie wystąpienia tej klasy mogą współdzielić tabeli jednej funkcji wirtualnych. Takie typy oczywiście są bardzo przydatne, ale ma także ograniczenia. Ponieważ układ jest niezdefiniowana nie mogą być przekazywane do programów napisanych w innych językach, takich jak C, a ponieważ mogą one być nieciągłych ich nie można niezawodnie skopiować fast niskiego poziomu funkcje takie jak `memcopy` lub serializowany przez sieć.

 Aby włączyć kompilatory oraz programy C++ i metaprograms przeglądanie informacji o przydatności danego typu w operacjach, które są zależne od układu pamięci, C ++ 14 wprowadzone trzy kategorie proste klasy i struktury: *prosta*, *układu standard*, i *POD* lub zwykły stare dane. Standardowa biblioteka ma szablonów funkcji `is_trivial<T>`, `is_standard_layout<T>` i `is_pod<T>` określające, czy dany typ należy do danej kategorii.

## <a name="trivial-types"></a>Prosta typów

 Po klasie lub strukturze w języku C++ został dostarczony do kompilatora lub jawnie ustawiana domyślnie specjalnych funkcji Członkowskich, wówczas jest prosta typu. Go zajmuje obszar pamięci ciągłej. Może mieć elementów członkowskich o specyfikatory różnych dostępu. W języku C++ kompilator jest swobodę kolejność elementów członkowskich w tej sytuacji. W związku z tym można memcopy takie obiekty, ale nie można niezawodnie korzystać z programu C. Prosta typu T można skopiować do tablicy znaków lub char bez znaku i bezpiecznie skopiować do zmiennej T. Należy pamiętać, że ze względu na wymagania dotyczące wyrównywania, może być bajtów uzupełnienie między elementami członkowskimi typu.

 Prosta typy mają trivial domyślnego konstruktora, Konstruktor kopiujący trivial, operatora przypisania kopii prosta i prosta — destruktor. W każdym przypadku *trivial* oznacza Konstruktor / — operator/destruktor nie jest dostarczane przez użytkownika i należy do klasy, która ma

- nie funkcje wirtualne i wirtualne klasy podstawowe,

- nie klas podstawowych sytemu nieuproszczony odpowiedniego konstruktora / — operator/destruktora

- nie elementów członkowskich danych typu klasy z nieuproszczony odpowiedniego konstruktora / — operator/destruktora

W poniższych przykładach pokazano typów prostych. W Trivial2, obecności `Trivial2(int a, int b)` Konstruktor wymaga podania konstruktora domyślnego. Dla typu na kwalifikować się jako trivial musi jawnie domyślne tego konstruktora.

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

## <a name="standard-layout-types"></a>Układ standardowe typy

 Po klasie lub strukturze nie zawiera pewnych funkcji języka C++, takich jak funkcje wirtualne, które nie znajdują się w języku C, a wszystkie elementy członkowskie tej samej kontrolę dostępu, jest to typ układu standard. Jest w stanie memcopy i czy mogą być używane przez programy C wystarczająco zdefiniowany układ. Typy standardowe układu może mieć zdefiniowane przez użytkownika specjalnych funkcji Członkowskich. Ponadto typy standardowe układu ma tę charakterystykę:

- nie funkcje wirtualne i wirtualne klasy podstawowe

- wszystkie elementy członkowskie danych niestatyczna mieć tej samej kontroli dostępu

- Wszyscy członkowie niestatyczna typu klasy są standardowe układu

- wszystkie klasy podstawowe są standardowe układu

- ma nie klas podstawowych tego samego typu jako pierwszego elementu członkowskiego danych niestatycznych.

- spełnia jeden z następujących warunków:

  - nie niestatyczny element członkowski danych w klasie pochodnej większość i nie więcej niż jedną klasę podstawową z elementami członkowskimi danych niestatycznych, lub

  - ma nie klas podstawowych z elementami członkowskimi danych niestatycznych

Poniższy kod przedstawia przykład typu układu standardowe:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};

```

 Ostatnie dwa wymagania można prawdopodobnie lepiej zilustrować z kodem. Mimo że w następnym przykładzie podstawowy jest standard układu `Derived` nie jest standard układu, ponieważ zarówno przez dział it (klasa najdalszych pochodnych) i `Base` mieć elementów członkowskich danych niestatyczna:

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

 W tym przykładzie `Derived` jest standard układu ponieważ `Base` nie ma danych niestatycznych członków:

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

 Pochodnego również będą układu standard Jeśli `Base` ma elementów członkowskich danych i `Derived` miał tylko funkcje Członkowskie.

## <a name="pod-types"></a>Typy POD

 Po klasie lub strukturze jest prosta i układu standard, jest typ POD (zwykły starych danych). W związku z tym jest ciągłe układu pamięci POD typów i każdy element członkowski ma adres wyższe niż elementu członkowskiego, który został zadeklarowany, tak, aby kopiuje bajtu na potrzeby bajt i binarne we/wy, można przeprowadzić na tych typów.  Typy skalarne, takie jak int są również POD typów. POD typy klasy mogą być tylko typy POD elementy członkowskie danych niestatycznego.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono różnice między trivial, standard układ i typy POD:

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

## <a name="literal_types"></a> Typy literału

Typ literału jest jednym którego układ można określić w czasie kompilacji. Poniżej przedstawiono typy literału:

- void
- typy skalarne
- odwołania
- Tablice void, typów skalarnych lub odwołuje się do
- Klasa, która ma destruktor prosta i konstruktory constexpr, które nie są przenoszenie lub kopiowanie konstruktorów. Ponadto wszystkie jego elementy członkowskie danych niestatyczna i klasy podstawowe muszą być typy literału i nietrwałe nie.

## <a name="see-also"></a>Zobacz też

 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)