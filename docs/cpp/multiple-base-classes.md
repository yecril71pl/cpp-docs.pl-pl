---
title: Wiele klas podstawowych
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 7cac70da5dd7093ce3e9c1cf3d2350d780c6b391
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353733"
---
# <a name="multiple-base-classes"></a>Wiele klas podstawowych

Klasa może pochodzić z więcej niż jednej klasy podstawowej. W modelu wielokrotnego dziedziczenia (gdzie klasy pochodzą z więcej niż jednej klasy podstawowej), klasy podstawowe są określane przy użyciu elementu gramatyki *listy podstawowej.* Na przykład, można określić deklarację klasy dla `CollectionOfBook`, pochodzącej z `Collection` i `Book`:

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

Kolejność, w której określane są klasy bazowe nie ma znaczenia z wyjątkiem niektórych przypadków, gdy wywoływane są konstruktory i destruktory. W tych przypadkach, kolejność, w której określane są klasy bazowe ma wpływ na:

- Kolejność, w której następuje inicjowanie przez konstruktor. Jeśli kod opiera się na tym, aby część `Book` kolekcji `CollectionOfBook` została zainicjowana przed częścią `Collection`, kolejność specyfikacji ma znaczenie. Inicjowanie odbywa się w kolejności, *w.*

- Kolejność, w której wywoływane są destruktory, aby dokonać czyszczenia. Ponownie, jeśli określona „część” klasy musi być obecna, gdy niszczona jest inna część, kolejność ma znaczenie. Destruktory są wywoływane w odwrotnej kolejności klas określonych na *liście podstawowej*.

    > [!NOTE]
    >  Kolejność specyfikacji klas bazowych może wpływać na układ pamięci klasy. Nie należy podejmować żadnych decyzji programistycznych na podstawie kolejności elementów podstawowych w pamięci.

Podczas określania *listy podstawowej*nie można określić tej samej nazwy klasy więcej niż raz. Jednak klasa może być pośrednią podstawą dla klasy pochodnej więcej niż raz.

## <a name="virtual-base-classes"></a>Wirtualne klasy podstawowe

Ponieważ klasa może być pośrednią klasą bazową do klasy pochodnej więcej niż raz, w języku C++ zapewniono możliwość optymalizacji sposobu działania klas bazowych. Wirtualne klasy bazowe oferują sposób, aby zaoszczędzić miejsce i uniknąć niejasności w hierarchii klas, które używają wielokrotnego dziedziczenia.

Każdy obiekt niewirtualny zawiera kopię składowych danych zdefiniowanych w klasie podstawowej. Ta duplikacja powoduje utratę miejsca i wymaga od użytkownika wybrania kopii składowych klasy podstawowej przy każdym uzyskiwaniu dostępu do nich.

Gdy klasa podstawowa jest określona jako baza wirtualna, może ona działać jako baza pośrednia więcej niż raz, bez duplikacji jej składowych danych. Pojedyncza kopia składowych danych jest współużytkowana przez wszystkie klasy podstawowe, które używają jej jako bazy wirtualnej.

Podczas deklarowania wirtualnej klasy podstawowej **wirtualne** słowo kluczowe pojawia się na listach podstawowych klas pochodnych.

Należy uwzględnić hierarchię klas na poniższym rysunku, który ilustruje symulowaną kolejkę po obiad.

![Wykres symulowanej linii obiadowej](../cpp/media/vc38xp1.gif "Wykres symulowanej linii obiadowej") <br/>
Symulowany wykres linii lunchu

Na rysunku `Queue` jest klasą bazową dla `CashierQueue` i `LunchQueue`. Jednakże, gdy obie klasy są połączone, tworząc `LunchCashierQueue`, pojawia się następujący problem: nowa klasa zawiera dwa podobiekty typu `Queue`, jeden `CashierQueue`, a drugi `LunchQueue`. Na poniższej ilustracji pokazano koncepcyjny układ pamięci (rzeczywisty układ pamięci może być zoptymalizowany).

![Symulowany obiekt&#45;linii lunchu](../cpp/media/vc38xp2.gif "Symulowany obiekt&#45;linii lunchu") <br/>
Symulowany obiekt z linii lunchu

Należy zauważyć, że istnieją dwa podobiekty `Queue` w obiekcie `LunchCashierQueue`. W poniższym kodzie `Queue` zadeklarowano jako wirtualną klasę bazową:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**Wirtualne** słowo kluczowe zapewnia, że tylko jedna `Queue` kopia podobiektu jest uwzględniona (zobacz poniższy rysunek).

![Symulowany obiekt&#45;linii obiadowej, wirtualne klasy podstawowe](../cpp/media/vc38xp3.gif "Symulowany obiekt&#45;linii obiadowej, wirtualne klasy podstawowe") <br/>
Symulowany obiekt z linii lunchu z wirtualnymi klasami bazowym

Klasa może mieć zarówno wirtualny jak i niewirtualny składnik danego typu. Tak się dzieje w warunkach przedstawionych na poniższej ilustracji.

![Wirtualne i nie&#45;składniki wirtualne klasy](../cpp/media/vc38xp4.gif "Wirtualne i nie&#45;składniki wirtualne klasy") <br/>
Składniki wirtualne i niewirtualne tej samej klasy

Na rysunku `CashierQueue` i `LunchQueue` używają `Queue` jako wirtualnej klasy bazowej. Jednak `TakeoutQueue` określa `Queue` jako klasę bazową, a nie wirtualną klasę bazową. W związku z tym `LunchTakeoutCashierQueue` posiada dwa podobiekty typu `Queue`: jeden ze ścieżki dziedziczenia, która zawiera `LunchCashierQueue` a drugi ze ścieżki, która zawiera `TakeoutQueue`. To zostało zilustrowane na poniższym rysunku.

![Wirtualne & nie&#45;dziedziczenie wirtualne w układzie obiektów](../cpp/media/vc38xp5.gif "Wirtualne & nie&#45;dziedziczenie wirtualne w układzie obiektów") <br/>
Układ obiektów z dziedziczeniem wirtualnym i niewirtuacyjnym

> [!NOTE]
> Dziedziczenie wirtualne zapewnia znaczące korzyści dotyczące rozmiaru w porównaniu do dziedziczenia niewirtualnego. Jednak może to wprowadzić dodatkowe obciążenie dotyczące przetwarzania.

Jeśli w klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, oraz jeśli konstruktor lub destruktor klasy pochodnej wywołuje tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może wprowadzić dodatkowe ukryte pola „vtordisp” do klas z bazami wirtualnymi. Opcja `/vd0` kompilatora pomija dodanie ukrytego elementu członkowskiego konstruktora/destruktora.The compiler option suppresses the addition of the hidden vtordisp constructor/destructor displacement member. Opcja `/vd1` kompilatora, domyślna, włącza je tam, gdzie są one niezbędne. Wyłącz vtordisps tylko wtedy, gdy masz pewność, że wszystkie konstruktory i destruktory klas wywołują funkcje wirtualne w sposób wirtualny.

Opcja `/vd` kompilatora wpływa na cały moduł kompilacji. `vtordisp` Pragma służy do wygaszania pól, a następnie ponownego włączania `vtordisp` na podstawie klasy po klasie:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Niejednoznaczności nazw

Wielokrotne dziedziczenie wprowadza dla nazw możliwość dziedziczenia wzdłuż więcej niż jednej ścieżki. Nazwy klas składowych wzdłuż tych ścieżek nie muszą być unikatowe. Te konflikty nazw są nazywane „niejasnościami”.

Dowolne wyrażenie, które odwołuje się do składowej klasy, musi być jednoznacznym odniesieniem. W poniższym przykładzie pokazano, jak rozwijają się niejasności:

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

Biorąc pod uwagę powyższe deklaracje klas, następujący kod jest niejednoznaczny, ponieważ nie jest jasne, czy `b` dotyczy `b` w `A`, czy w `B`:

```cpp
C *pc = new C;

pc->b();
```

Należy rozważyć poprzedni przykład. Ponieważ nazwa `a` jest składową obu klas `A` i `B`, kompilator nie może rozpoznać, które `a` wyznacza funkcję, która ma być wywoływana. Dostęp do elementu członkowskiego jest niejednoznaczny, jeżeli może odnosić się do więcej niż jednej funkcji, obiektu, typu lub modułu wyliczającego.

Kompilator wykrywa niejasności wykonując testy w następującej kolejności:

1. Jeśli dostęp do nazwy jest niejednoznaczny (jak opisano powyżej), generowany jest komunikat o błędzie.

1. Jeśli funkcje przeciążone są jednoznaczne, są one rozwiązane.

1. Jeśli dostęp do nazwy narusza uprawnienia dostępu do elementu członkowskiego, generowany jest komunikat o błędzie. (Aby uzyskać więcej informacji, zobacz [Kontrola dostępu do członka](../cpp/member-access-control-cpp.md).)

Gdy wyrażenie powoduje niejednoznaczność poprzez dziedziczenie, można ją rozwiązać ręcznie kwalifikując nazwę w pytaniu o nazwę klasy. Aby w poprzednim przykładzie skompilować poprawnie, bez niejasności, należy użyć kodu takiego jak:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> Gdy zadeklarowane jest `C`, może ono powodować błędy, podczas gdy ma miejsce odwołanie do `B` w zakresie `C`. Błąd nie jest zgłaszany, do chwili faktycznego dokonania niekwalifikowanego odwołania do `B` w zakresie `C`.

### <a name="dominance"></a>Dominacja

Jest możliwe dla więcej niż jedną nazwę (funkcja, obiekt lub wyliczacz) można osiągnąć za pomocą wykresu dziedziczenia. Takie przypadki są uważane za niejednoznaczne z niewirtualnych klas podstawowych. Są one również niejednoznaczne z wirtualnych klas podstawowych, chyba że jedna z nazw "dominuje" inne.

Nazwa dominuje inna nazwa, jeśli jest zdefiniowana w obu klasach i jedna klasa jest pochodną drugiej. Dominująca nazwa to nazwa w klasie pochodnej; nazwa ta jest używana, gdy w przeciwnym razie powstałaby niejednoznaczność, jak pokazano w poniższym przykładzie:

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>Niejednoznaczne konwersje

Jawne i niejawne konwersje ze wskaźników lub odwołań do typów klas może powodować niejednoznaczności. Na następnej ilustracji niejednoznaczna konwersja wskaźników do klas podstawowych przedstawiono następujące elementy:

- Deklaracja typu przedmiotu `D`.

- Efekt zastosowania operatora adresowego (**&**) do tego przedmiotu. Należy zauważyć, że operator adresu zawsze dostarcza adres podstawowy obiektu.

- Efekt jawnego przekonwertowania wskaźnika uzyskanego przy użyciu operatora `A`adresu na typ klasy podstawowej . Należy zauważyć, że wymuszanie `A*` adresu obiektu do typu nie zawsze dostarcza kompilatorowi `A` wystarczających informacji, które podobiekty typu wybrać; w tym przypadku istnieją dwa podobiekty.

![Niejednoznaczna konwersja wskaźników do klas podstawowych](../cpp/media/vc38xt1.gif "Niejednoznaczna konwersja wskaźników do klas podstawowych") <br/>
Niejednoznaczna konwersja wskaźników do klas podstawowych

Konwersja do `A*` typu `A`(wskaźnik do) jest niejednoznaczna, ponieważ nie ma sposobu, `A` aby rozpoznać, który podobiekt typu jest poprawny. Należy zauważyć, że można uniknąć niejednoznaczności, wyraźnie określając, który podobiekt ma być używany, w następujący sposób:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Niejednoznaczności i wirtualne klasy podstawowe

Jeśli używane są wirtualne klasy podstawowe, funkcje, obiekty, typy i wyliczacze można osiągnąć za pośrednictwem ścieżek wielokrotnego dziedziczenia. Ponieważ istnieje tylko jedno wystąpienie klasy podstawowej, nie ma niejednoznaczności podczas uzyskiwania dostępu do tych nazw.

Na poniższej ilustracji przedstawiono, jak obiekty są składane przy użyciu dziedziczenia wirtualnego i niewirtualnego.

![Wirtualne wyprowadzenie i nie&#45;wirtualne wyprowadzenie](../cpp/media/vc38xr1.gif "Wirtualne wyprowadzenie i nie&#45;wirtualne wyprowadzenie") <br/>
Wyprowadzenie wirtualne a niewirtualne

Na rysunku dostęp do dowolnego `A` członka klasy za pośrednictwem niewirtualnych klas podstawowych powoduje niejednoznaczność; kompilator nie ma informacji wyjaśniających, czy używać podobiektu skojarzonego `B` z `C`podobiektem lub podobiektu skojarzonego z programem . Jednak gdy `A` jest określony jako wirtualnej klasy podstawowej, nie ma wątpliwości, które podobiekty jest dostępny.

## <a name="see-also"></a>Zobacz też

[Dziedziczenie](../cpp/inheritance-cpp.md)
