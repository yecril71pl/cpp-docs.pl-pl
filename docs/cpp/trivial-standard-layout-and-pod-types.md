---
title: Typy proste, standardowe układu, POD i literału
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: b31fefd31b32a5fc4aa3f655b90d39f60a524ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188067"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Typy proste, standardowe układu, POD i literału

*Termin "* odnosi się do sposobu, w jaki elementy członkowskie obiektu klasy, struktury lub Unii są rozmieszczone w pamięci. W niektórych przypadkach układ jest dobrze zdefiniowany przez specyfikację języka. Ale jeśli Klasa lub struktura zawiera pewne C++ funkcje języka, takie jak wirtualne klasy bazowe, funkcje wirtualne i elementy członkowskie z różnymi kontrolami dostępu, kompilator jest bezpłatny do wybierania układu. Ten układ może się różnić w zależności od tego, jakie optymalizacje są wykonywane i w wielu przypadkach obiekt może nie zajmować ciągłego obszaru pamięci. Na przykład jeśli klasa ma funkcje wirtualne, wszystkie wystąpienia tej klasy mogą współużytkować jedną tabelę funkcji wirtualnych. Takie typy są bardzo przydatne, ale mają także ograniczenia. Ponieważ układ jest niezdefiniowany, nie można go przekazywać do programów pisanych w innych językach, takich jak C, i ponieważ mogą one być nieciągłe, nie mogą być niezawodnie kopiowane przy użyciu szybkich funkcji niskiego poziomu, takich jak `memcopy`, lub serializowanych przez sieć.

Aby włączyć kompilatory, a także C++ programy i aplikacje, które mają przyczynić się do uzyskania przydatności danego typu dla operacji, które zależą od określonego układu pamięci, język c++ 14 wprowadził trzy kategorie prostych klas i struktur: warstwy *prostej*, *standardowej-układu*i *pod* lub zwykłe stare dane. Biblioteka standardowa ma `is_trivial<T>`szablonów funkcji, `is_standard_layout<T>` i `is_pod<T>`, które określają, czy dany typ należy do danej kategorii.

## <a name="trivial-types"></a>Typy proste

Gdy Klasa lub struktura w programie C++ ma jawnie określone lub jawne specjalne funkcje członkowskie, to jest typem prostym. Zajmuje on ciągły obszar pamięci. Może mieć elementy członkowskie z różnymi specyfikatorami dostępu. W C++programie kompilator jest bezpłatny, aby wybrać sposób uporządkowania elementów członkowskich w tej sytuacji. W związku z tym można memcopy takie obiekty, ale nie można ich w niezawodny sposób wykorzystać z programu C. Typ prosty T może być skopiowany do tablicy char lub unsigned char i bezpiecznie skopiowany do zmiennej T. Należy zauważyć, że ze względu na wymagania dotyczące wyrównania mogą wystąpić bajty uzupełniające między elementami członkowskimi typu.

Typy proste mają uproszczony Konstruktor domyślny, Konstruktor trivial kopiujący, operator przypisania prostego kopiowania i prosty destruktor. W każdym przypadku, *uproszczone* oznacza, że Konstruktor/operator/destruktor nie jest podany przez użytkownika i należy do klasy, która ma

- Brak funkcji wirtualnych lub wirtualnych klas bazowych,

- Brak klas bazowych z odpowiadającym im nieuproszczonym konstruktorem/destruktorem

- Brak składowych danych typu klasy z odpowiadającym nieuproszczonym konstruktorem/operatorem/destruktorem

W poniższych przykładach pokazano typy proste. W Trivial2, obecność konstruktora `Trivial2(int a, int b)` wymaga podania domyślnego konstruktora. Aby można było zakwalifikować typ jako uproszczony, należy jawnie określić domyślnego konstruktora.

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

## <a name="standard-layout-types"></a>Standardowe typy układów

Gdy Klasa lub struktura nie zawiera niektórych C++ funkcji języka, takich jak funkcje wirtualne, które nie znajdują się w języku C, a wszystkie elementy członkowskie mają tę samą kontrolę dostępu, jest to typ układu standardowego. Jest to memcopy, a układ jest wystarczająco zdefiniowany, że może być używany przez programy języka C. Standardowe typy układów mogą zawierać specjalne funkcje członkowskie zdefiniowane przez użytkownika. Ponadto standardowe typy układów mają następujące cechy:

- Brak funkcji wirtualnych ani wirtualnych klas bazowych

- wszystkie niestatyczne składowe danych mają tę samą kontrolę dostępu

- wszystkie niestatyczne elementy członkowskie typu klasy są układem standardowym

- wszystkie klasy podstawowe są układem standardowym.

- nie ma klas bazowych tego samego typu co pierwszy niestatyczny element członkowski danych.

- spełnia jeden z następujących warunków:

  - Brak niestatycznego elementu członkowskiego danych w klasie najbardziej pochodnej i nie więcej niż jednej klasy bazowej z niestatycznymi elementami członkowskimi danych.

  - nie ma klas bazowych z niestatycznymi elementami członkowskimi danych

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

Ostatnie dwa wymagania mogą być lepiej zilustrowane kodem. W następnym przykładzie, nawet jeśli podstawowy jest układ standardowy, `Derived` nie jest układem standardowym, ponieważ obie te (Klasa pochodna) i `Base` mają niestatyczne elementy członkowskie danych:

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

W tym przykładzie `Derived` jest układem standardowym, ponieważ `Base` nie ma elementów członkowskich danych niestatycznych:

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

Pochodna również będzie układem standardowym, jeśli `Base` miały elementy członkowskie danych i `Derived` mieli tylko funkcje składowe.

## <a name="pod-types"></a>Typy POD

Gdy Klasa lub struktura jest układem prostym i standardowym, jest to na przykład typ zwykłego starego danych. Układ pamięci typów POD jest w związku z tym ciągły, a każdy element członkowski ma wyższy adres niż element członkowski, który został zadeklarowany przed nim, dzięki czemu można wykonywać bajty dla kopii bajtowych i binarnych operacji we/wy na tych typach.  Typy skalarne, takie jak int, są również typami. Typy POD, które są klasy mogą mieć tylko typy POD, jako niestatyczne elementy członkowskie danych.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano różnice między typami prostymi, standardowymi i POD:

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

## <a name="literal-types"></a><a name="literal_types"></a>Typy literałów

Typ literału to jeden, którego układ można określić w czasie kompilacji. Poniżej przedstawiono typy literałów:

- void
- typy skalarne
- odwołania
- Tablice typów void, skalarnych lub odwołań
- Klasa, która ma prosty destruktor i jeden lub więcej konstruktorów constexpr, które nie są przenoszone lub kopiujące konstruktorów. Ponadto wszystkie jego niestatyczne składowe danych i klasy bazowe muszą być typami literałów i nievolatile.

## <a name="see-also"></a>Zobacz też

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
