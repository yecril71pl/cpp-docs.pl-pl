---
title: Wiele klas podstawowych
ms.date: 11/04/2016
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: fbbe6d6194b878b4851cbde84b55d71b9e4fc02c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483463"
---
# <a name="multiple-base-classes"></a>Wiele klas podstawowych

Klasy mogą pochodzić z więcej niż jednej klasy bazowej. W modelu dziedziczenia wielokrotnego (gdzie klasy pochodzą z więcej niż jednej klasy bazowej) klasy bazowe są określane za pomocą *lista_bazowa* elementu gramatyki. Na przykład, można określić deklarację klasy dla `CollectionOfBook`, pochodzącej z `Collection` i `Book`:

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

- Kolejność, w której następuje inicjowanie przez konstruktor. Jeśli kod opiera się na tym, aby część `Book` kolekcji `CollectionOfBook` została zainicjowana przed częścią `Collection`, kolejność specyfikacji ma znaczenie. Inicjowanie odbywa się w kolejności klas określonej w *lista_bazowa*.

- Kolejność, w której wywoływane są destruktory, aby dokonać czyszczenia. Ponownie, jeśli określona „część” klasy musi być obecna, gdy niszczona jest inna część, kolejność ma znaczenie. Destruktory są wywoływane w odwrotnej kolejności klas do określonej w *lista_bazowa*.

    > [!NOTE]
    >  Kolejność specyfikacji klas bazowych może wpływać na układ pamięci klasy. Nie należy podejmować żadnych decyzji programistycznych na podstawie kolejności elementów podstawowych w pamięci.

Podczas określania *lista_bazowa*, tej samej nazwy klasy nie można określić więcej niż jeden raz. Jednak klasa może być pośrednią podstawą dla klasy pochodnej więcej niż raz.

## <a name="virtual-base-classes"></a>Wirtualne klasy bazowe

Ponieważ klasa może być pośrednią klasą bazową do klasy pochodnej więcej niż raz, w języku C++ zapewniono możliwość optymalizacji sposobu działania klas bazowych. Wirtualne klasy bazowe oferują sposób, aby zaoszczędzić miejsce i uniknąć niejasności w hierarchii klas, które używają wielokrotnego dziedziczenia.

Każdy obiekt niewirtualny zawiera kopię składowych danych zdefiniowanych w klasie podstawowej. Ta duplikacja powoduje utratę miejsca i wymaga od użytkownika wybrania kopii składowych klasy podstawowej przy każdym uzyskiwaniu dostępu do nich.

Gdy klasa podstawowa jest określona jako baza wirtualna, może ona działać jako baza pośrednia więcej niż raz, bez duplikacji jej składowych danych. Pojedyncza kopia składowych danych jest współużytkowana przez wszystkie klasy podstawowe, które używają jej jako bazy wirtualnej.

Podczas deklarowania wirtualnej klasy bazowej, **wirtualnego** — słowo kluczowe jest wyświetlana na listach bazowych klas pochodnych.

Należy uwzględnić hierarchię klas na poniższym rysunku, który ilustruje symulowaną kolejkę po obiad.

![Wykres symulowanej obiad](../cpp/media/vc38xp1.gif "vc38XP1") symulowanej kolejki po obiad wykresu

Na rysunku `Queue` jest klasą bazową dla `CashierQueue` i `LunchQueue`. Jednakże, gdy obie klasy są połączone, tworząc `LunchCashierQueue`, pojawia się następujący problem: nowa klasa zawiera dwa podobiekty typu `Queue`, jeden `CashierQueue`, a drugi `LunchQueue`. Na poniższej ilustracji pokazano koncepcyjny układ pamięci (rzeczywisty układ pamięci może być zoptymalizowany).

![Symulowane obiad&#45;obiektu wiersza](../cpp/media/vc38xp2.gif "vc38XP2") symulował obiekt kolejki po obiad

Należy zauważyć, że istnieją dwa podobiekty `Queue` w obiekcie `LunchCashierQueue`. W poniższym kodzie `Queue` zadeklarowano jako wirtualną klasę bazową:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**Wirtualnego** — słowo kluczowe gwarantuje, że tylko jedna kopia podobiektu `Queue` wchodzi (patrz poniższy rysunek).

![Symulowane obiad&#45;obiektu wiersza, wirtualne klasy bazowe](../cpp/media/vc38xp3.gif "vc38XP3") symulował obiekt kolejki po obiad z wirtualnymi klasami bazowymi

Klasa może mieć zarówno wirtualny jak i niewirtualny składnik danego typu. Tak się dzieje w warunkach przedstawionych na poniższej ilustracji.

![Wirtualne i niewirtualne składniki klasy](../cpp/media/vc38xp4.gif "vc38XP4") wirtualne i niewirtualne składniki tej samej klasy

Na rysunku `CashierQueue` i `LunchQueue` używają `Queue` jako wirtualnej klasy bazowej. Jednak `TakeoutQueue` określa `Queue` jako klasę bazową, a nie wirtualną klasę bazową. W związku z tym `LunchTakeoutCashierQueue` posiada dwa podobiekty typu `Queue`: jeden ze ścieżki dziedziczenia, która zawiera `LunchCashierQueue` a drugi ze ścieżki, która zawiera `TakeoutQueue`. To zostało zilustrowane na poniższym rysunku.

![Dziedziczenie wirtualne i niewirtualne w układ obiektu](../cpp/media/vc38xp5.gif "vc38XP5") układ obiektu z wirtualne i niewirtualne dziedziczenie

> [!NOTE]
>  Dziedziczenie wirtualne zapewnia znaczące korzyści dotyczące rozmiaru w porównaniu do dziedziczenia niewirtualnego. Jednak może to wprowadzić dodatkowe obciążenie dotyczące przetwarzania.

Jeśli w klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, oraz jeśli konstruktor lub destruktor klasy pochodnej wywołuje tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może wprowadzić dodatkowe ukryte pola „vtordisp” do klas z bazami wirtualnymi. `/vd0` — Opcja kompilatora pomija dodanie elementu członkowskiego przemieszczenia konstruktora/destruktora vtordisp ukryte. `/vd1` — Opcja kompilatora, domyślnie, włącza je gdzie są one niezbędne. Wyłącz vtordisps tylko wtedy, gdy masz pewność, że wszystkie konstruktory i destruktory klas wywołują funkcje wirtualne w sposób wirtualny.

`/vd` — Opcja kompilatora ma wpływ na cały moduł kompilacji. Użyj `vtordisp` pragmy do pominięcia i ponownego `vtordisp` pola na zasadzie klasa po klasie:

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

1. Jeśli dostęp do nazwy narusza uprawnienia dostępu do elementu członkowskiego, generowany jest komunikat o błędzie. (Aby uzyskać więcej informacji, zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md).)

Gdy wyrażenie powoduje niejednoznaczność poprzez dziedziczenie, można ją rozwiązać ręcznie kwalifikując nazwę w pytaniu o nazwę klasy. Aby w poprzednim przykładzie skompilować poprawnie, bez niejasności, należy użyć kodu takiego jak:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
>  Gdy zadeklarowane jest `C`, może ono powodować błędy, podczas gdy ma miejsce odwołanie do `B` w zakresie `C`. Błąd nie jest zgłaszany, do chwili faktycznego dokonania niekwalifikowanego odwołania do `B` w zakresie `C`.

### <a name="dominance"></a>Dominacja

Istnieje możliwość dla więcej niż jedną nazwę (funkcji, obiekt lub moduł wyliczający) można połączyć się za pośrednictwem programu graph dziedziczenia. Takie przypadki są traktowane jako niejednoznaczny z niewirtualnych klas podstawowych. Są one również niejednoznaczny z wirtualnymi klasami bazowymi, chyba że jedną z nazw "zajmuje większą część ekranu" inne.

Nazwę większą inną nazwę, jeśli jest zdefiniowana w obu klasach i jedna klasa pochodzi od innych. Nazwa dominująca jest nazwą klasy pochodnej; Ta nazwa jest używana, gdy niejednoznaczność mogłyby w przeciwnym razie pojawiły się, jak pokazano w poniższym przykładzie:

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

### <a name="ambiguous-conversions"></a>Wyrażenie niejednoznaczne

Jawne i niejawne konwersje z wskaźników lub odwołań do typów klasy może powodować niejednoznaczności. Na kolejnej ilustracji, niejednoznaczne konwersję wskaźniki do klas podstawowych, przedstawiono poniżej:

- Deklaracja obiektu typu `D`.

- Efektem zastosowania operatora address-of (**&**) do tego obiektu. Należy pamiętać, że operator address-of zawsze dostarcza adres podstawowy obiekt.

- Efekt jawnej konwersji wskaźnika uzyskany przy użyciu operatora address-of na typ klasy bazowej `A`. Należy pamiętać, coercing adresu obiektu na typ `A*` nie zawsze zawiera kompilator o wystarczającej ilości informacji na temat których podobiektu typu `A` wybrać; w tym przypadku istnieją dwa podobiekty.

![Niejednoznaczna konwersja wskaźniki do klas bazowych](../cpp/media/vc38xt1.gif "vc38XT1") niejednoznaczne konwersję wskaźniki do klas bazowych

Konwersja na typ `A*` (wskaźnik do `A`) jest niejednoznaczny, ponieważ nie istnieje sposób do określenia, które podobiektu typu na `A` jest poprawne. Należy zwrócić uwagę na to, że można uniknąć niejednoznaczności, jawnie ustawiając podobiektów, który miał zostać użyty w następujący sposób:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Niejednoznaczności i wirtualne klasy bazowe

Wirtualne klasy bazowe są używane, funkcji, obiekty, typy i moduły wyliczające można uzyskać dostęp przez ścieżki dziedziczenia wielokrotnego. Ponieważ istnieje tylko jedno wystąpienie klasy bazowej, nie ma żadnych niejednoznaczności podczas uzyskiwania dostępu do tych nazw.

Poniższy rysunek przedstawia sposób obiekty są złożone, wirtualnej, a dziedziczenia niewirtualnego.

![Wyprowadzanie wirtualne i niewirtualne informacje](../cpp/media/vc38xr1.gif "vc38XR1") wirtualne programu vs. Niewirtualne informacje

Na rysunku, uzyskiwanie dostępu do dowolnego elementu członkowskiego klasy `A` za pośrednictwem niewirtualnych klas podstawowych przyczyn wiadomość niejednoznaczności; kompilator nie ma informacji o który objaśnia, czy ma być używany podobiektu skojarzone z `B` lub podobiektów skojarzone z `C`. Jednak gdy `A` jest określony jako wirtualnej klasy bazowej, nie ma żadnych pytanie podobiektów, który jest dostępny.

## <a name="see-also"></a>Zobacz także

[Dziedziczenie](../cpp/inheritance-cpp.md)