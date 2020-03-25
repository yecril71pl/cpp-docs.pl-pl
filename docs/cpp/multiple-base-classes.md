---
title: Wiele klas podstawowych
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: b8bc411b1b8d0b459fe58a39cf351d59d09b2d0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179518"
---
# <a name="multiple-base-classes"></a>Wiele klas podstawowych

Klasa może pochodzić z więcej niż jednej klasy bazowej. W modelu wielokrotnego dziedziczenia (gdzie klasy pochodzą z więcej niż jednej klasy bazowej) klasy bazowe są określane przy użyciu elementu *listy podstawowej* gramatyki. Na przykład, można określić deklarację klasy dla `CollectionOfBook`, pochodzącej z `Collection` i `Book`:

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

- Kolejność, w której następuje inicjowanie przez konstruktor. Jeśli kod opiera się na tym, aby część `Book` kolekcji `CollectionOfBook` została zainicjowana przed częścią `Collection`, kolejność specyfikacji ma znaczenie. Inicjalizacja odbywa się w kolejności, w jakiej klasy są określone na *liście podstawowej*.

- Kolejność, w której wywoływane są destruktory, aby dokonać czyszczenia. Ponownie, jeśli określona „część” klasy musi być obecna, gdy niszczona jest inna część, kolejność ma znaczenie. Destruktory są wywoływane w odwrotnej kolejności klas określonych na *liście podstawowej*.

    > [!NOTE]
    >  Kolejność specyfikacji klas bazowych może wpływać na układ pamięci klasy. Nie należy podejmować żadnych decyzji programistycznych na podstawie kolejności elementów podstawowych w pamięci.

Podczas określania *listy podstawowej*nie można określić tej samej nazwy klasy więcej niż raz. Jednak klasa może być pośrednią podstawą dla klasy pochodnej więcej niż raz.

## <a name="virtual-base-classes"></a>Wirtualne klasy bazowe

Ponieważ klasa może być pośrednią klasą bazową do klasy pochodnej więcej niż raz, w języku C++ zapewniono możliwość optymalizacji sposobu działania klas bazowych. Wirtualne klasy bazowe oferują sposób, aby zaoszczędzić miejsce i uniknąć niejasności w hierarchii klas, które używają wielokrotnego dziedziczenia.

Każdy obiekt niewirtualny zawiera kopię składowych danych zdefiniowanych w klasie podstawowej. Ta duplikacja powoduje utratę miejsca i wymaga od użytkownika wybrania kopii składowych klasy podstawowej przy każdym uzyskiwaniu dostępu do nich.

Gdy klasa podstawowa jest określona jako baza wirtualna, może ona działać jako baza pośrednia więcej niż raz, bez duplikacji jej składowych danych. Pojedyncza kopia składowych danych jest współużytkowana przez wszystkie klasy podstawowe, które używają jej jako bazy wirtualnej.

Podczas deklarowania wirtualnej klasy bazowej, **wirtualne** słowo kluczowe pojawia się na podstawowych listach klas pochodnych.

Należy uwzględnić hierarchię klas na poniższym rysunku, który ilustruje symulowaną kolejkę po obiad.

![Wykres symulowanej pozostałej linii obiadu](../cpp/media/vc38xp1.gif "Wykres symulowanej pozostałej linii obiadu") <br/>
Wykres symulowanej linii obiadowej

Na rysunku `Queue` jest klasą bazową dla `CashierQueue` i `LunchQueue`. Jednakże, gdy obie klasy są połączone, tworząc `LunchCashierQueue`, pojawia się następujący problem: nowa klasa zawiera dwa podobiekty typu `Queue`, jeden `CashierQueue`, a drugi `LunchQueue`. Na poniższej ilustracji pokazano koncepcyjny układ pamięci (rzeczywisty układ pamięci może być zoptymalizowany).

![Obiekt symulowanego&#45;wiersza obiadu](../cpp/media/vc38xp2.gif "Obiekt symulowanego&#45;wiersza obiadu") <br/>
Symulowany obiekt linii obiadu

Należy zauważyć, że istnieją dwa podobiekty `Queue` w obiekcie `LunchCashierQueue`. W poniższym kodzie `Queue` zadeklarowano jako wirtualną klasę bazową:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**Wirtualne** słowo kluczowe zapewnia tylko jedną kopię `Queue` podobiektu (patrz poniższy rysunek).

![Obiekt symulowanego&#45;wiersza obiadu, wirtualne klasy bazowe](../cpp/media/vc38xp3.gif "Obiekt symulowanego&#45;wiersza obiadu, wirtualne klasy bazowe") <br/>
Symulowany obiekt linii obiadu z wirtualnymi klasami podstawowymi

Klasa może mieć zarówno wirtualny jak i niewirtualny składnik danego typu. Tak się dzieje w warunkach przedstawionych na poniższej ilustracji.

![Wirtualne i&#45;niewirtualne składniki klasy](../cpp/media/vc38xp4.gif "Wirtualne i&#45;niewirtualne składniki klasy") <br/>
Wirtualne i niewirtualne składniki tej samej klasy

Na rysunku `CashierQueue` i `LunchQueue` używają `Queue` jako wirtualnej klasy bazowej. Jednak `TakeoutQueue` określa `Queue` jako klasę bazową, a nie wirtualną klasę bazową. W związku z tym `LunchTakeoutCashierQueue` posiada dwa podobiekty typu `Queue`: jeden ze ścieżki dziedziczenia, która zawiera `LunchCashierQueue` a drugi ze ścieżki, która zawiera `TakeoutQueue`. To zostało zilustrowane na poniższym rysunku.

![Wirtualne & inne&#45;niż wirtualne dziedziczenie w układzie obiektu](../cpp/media/vc38xp5.gif "Wirtualne & inne&#45;niż wirtualne dziedziczenie w układzie obiektu") <br/>
Układ obiektu za pomocą dziedziczenia wirtualnego i niewirtualnego

> [!NOTE]
>  Dziedziczenie wirtualne zapewnia znaczące korzyści dotyczące rozmiaru w porównaniu do dziedziczenia niewirtualnego. Jednak może to wprowadzić dodatkowe obciążenie dotyczące przetwarzania.

Jeśli w klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, oraz jeśli konstruktor lub destruktor klasy pochodnej wywołuje tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może wprowadzić dodatkowe ukryte pola „vtordisp” do klas z bazami wirtualnymi. Opcja kompilatora `/vd0` pomija dodanie ukrytego elementu członkowskiego przemieszczenia konstruktora vtordisp/destruktora. Opcja kompilatora `/vd1` domyślnie umożliwia ich w razie potrzeby. Wyłącz vtordisps tylko wtedy, gdy masz pewność, że wszystkie konstruktory i destruktory klas wywołują funkcje wirtualne w sposób wirtualny.

Opcja kompilatora `/vd` ma wpływ na cały moduł kompilacji. Użyj dyrektywy pragma `vtordisp`, aby pominąć i ponownie włączyć pola `vtordisp` w oparciu o klasę klasy:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Niejasności nazwy

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

1. Jeśli dostęp do nazwy narusza uprawnienia dostępu do elementu członkowskiego, generowany jest komunikat o błędzie. (Aby uzyskać więcej informacji, zobacz [element członkowski-Access Control](../cpp/member-access-control-cpp.md).)

Gdy wyrażenie powoduje niejednoznaczność poprzez dziedziczenie, można ją rozwiązać ręcznie kwalifikując nazwę w pytaniu o nazwę klasy. Aby w poprzednim przykładzie skompilować poprawnie, bez niejasności, należy użyć kodu takiego jak:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
>  Gdy zadeklarowane jest `C`, może ono powodować błędy, podczas gdy ma miejsce odwołanie do `B` w zakresie `C`. Błąd nie jest zgłaszany, do chwili faktycznego dokonania niekwalifikowanego odwołania do `B` w zakresie `C`.

### <a name="dominance"></a>Dominacja

Jest możliwe, aby więcej niż jedna nazwa (funkcja, obiekt lub moduł wyliczający) była osiągnięta za poorednictwem grafu dziedziczenia. Takie przypadki są uważane za niejednoznaczne z niewirtualnymi klasami podstawowymi. Są one również niejednoznaczne dla wirtualnych klas bazowych, chyba że jedna z nazw "dominuje".

Nazwa dominuje inną nazwę, jeśli jest zdefiniowana w obu klasach, a jedna klasa pochodzi od drugiej. Nazwa dominująca jest nazwą w klasie pochodnej; Ta nazwa jest używana, gdy niejednoznaczność byłaby w inny sposób, jak pokazano w następującym przykładzie:

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

### <a name="ambiguous-conversions"></a>Konwersje niejednoznaczne

Jawne i niejawne konwersje ze wskaźników lub odwołań do typów klas mogą spowodować niejasności. Kolejna ilustracja, niejednoznaczna konwersja wskaźników do klas bazowych, pokazuje następujące elementy:

- Deklaracja obiektu typu `D`.

- Efekt zastosowania operatora address-of ( **&** ) do tego obiektu. Należy zauważyć, że operator address-of zawsze dostarcza adres podstawowy obiektu.

- Efekt jawnej konwersji wskaźnika uzyskanego przy użyciu operatora address-of na typ klasy bazowej `A`. Należy zauważyć, że wymuszony adres obiektu do wpisania `A*` nie zawsze zapewnia kompilatorowi wystarczające informacje, które podobiekty typu `A` do wybrania; w takim przypadku istnieją dwa podobiekty.

![Niejednoznaczna konwersja wskaźników do klas bazowych](../cpp/media/vc38xt1.gif "Niejednoznaczna konwersja wskaźników do klas bazowych") <br/>
Niejednoznaczna konwersja wskaźników do klas bazowych

Konwersja do typu `A*` (wskaźnik do `A`) jest niejednoznaczna, ponieważ nie istnieje sposób, aby rozpoznać, który podobiekt typu `A` jest poprawnym. Należy pamiętać, że można uniknąć niejednoznaczności, jawnie określając, który podobiekt ma być używany, w następujący sposób:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Niejasności i wirtualne klasy bazowe

Jeśli wirtualne klasy bazowe są używane, funkcje, obiekty, typy i moduły wyliczające można osiągnąć przez ścieżki wielokrotnego dziedziczenia. Ponieważ istnieje tylko jedno wystąpienie klasy bazowej, podczas uzyskiwania dostępu do tych nazw nie ma niejednoznaczności.

Na poniższej ilustracji przedstawiono sposób tworzenia obiektów przy użyciu wirtualnego i niewirtualnego dziedziczenia.

![Wirtualne wyprowadzenie i&#45;niewirtualne wyprowadzanie](../cpp/media/vc38xr1.gif "Wirtualne wyprowadzenie i&#45;niewirtualne wyprowadzanie") <br/>
Wirtualne a niewirtualne wyprowadzanie

Na rysunku dostęp do dowolnego elementu członkowskiego klasy `A` za pomocą niewirtualnych klas bazowych powoduje niejednoznaczność; Kompilator nie ma informacji, które wyjaśniają, czy należy używać podobiektu skojarzonego z `B` lub podobiektem skojarzonym z `C`. Jeśli jednak `A` określono jako wirtualną klasę bazową, nie ma pytania, do którego jest uzyskiwany dostęp do obiektu.

## <a name="see-also"></a>Zobacz też

[Dziedziczenie](../cpp/inheritance-cpp.md)
