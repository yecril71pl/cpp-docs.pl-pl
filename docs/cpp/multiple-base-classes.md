---
title: Wiele klas podstawowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b765fabe8b83169353650286d05d02301dcb4807
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multiple-base-classes"></a>Wiele klas podstawowych
Zgodnie z opisem w [dziedziczenie wielokrotne](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca), klasy mogą pochodzić z więcej niż jedną klasę podstawową. W modelu dziedziczenia wielokrotnego (gdzie klasy pochodne więcej niż jedną klasę podstawową) klasy podstawowe są określane za pomocą *lista podstawowego* element gramatyki. Na przykład, można określić deklarację klasy dla `CollectionOfBook`, pochodzącej z `Collection` i `Book`:  
  
```  
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
  
-   Kolejność, w której następuje inicjowanie przez konstruktor. Jeśli kod opiera się na tym, aby część `Book` kolekcji `CollectionOfBook` została zainicjowana przed częścią `Collection`, kolejność specyfikacji ma znaczenie. Inicjowanie odbywa się w kolejności klas są określone w *lista podstawowego*.  
  
-   Kolejność, w której wywoływane są destruktory, aby dokonać czyszczenia. Ponownie, jeśli określona „część” klasy musi być obecna, gdy niszczona jest inna część, kolejność ma znaczenie. W odwrotnej kolejności klasy określony w zostaną wywołane destruktory *lista podstawowego*.  
  
    > [!NOTE]
    >  Kolejność specyfikacji klas bazowych może wpływać na układ pamięci klasy. Nie należy podejmować żadnych decyzji programistycznych na podstawie kolejności elementów podstawowych w pamięci.  
  
 Podczas określania *lista podstawowego*, tej samej nazwie klasy nie można określić więcej niż raz. Jednak klasa może być pośrednią podstawą dla klasy pochodnej więcej niż raz.  
  
## <a name="virtual-base-classes"></a>Wirtualne klasy podstawowe  
 Ponieważ klasa może być pośrednią klasą bazową do klasy pochodnej więcej niż raz, w języku C++ zapewniono możliwość optymalizacji sposobu działania klas bazowych. Wirtualne klasy bazowe oferują sposób, aby zaoszczędzić miejsce i uniknąć niejasności w hierarchii klas, które używają wielokrotnego dziedziczenia.  
  
 Każdy obiekt niewirtualny zawiera kopię składowych danych zdefiniowanych w klasie podstawowej. Ta duplikacja powoduje utratę miejsca i wymaga od użytkownika wybrania kopii składowych klasy podstawowej przy każdym uzyskiwaniu dostępu do nich.  
  
 Gdy klasa podstawowa jest określona jako baza wirtualna, może ona działać jako baza pośrednia więcej niż raz, bez duplikacji jej składowych danych. Pojedyncza kopia składowych danych jest współużytkowana przez wszystkie klasy podstawowe, które używają jej jako bazy wirtualnej.  
  
 Przy deklarowaniu wirtualna klasa podstawowa **wirtualnego** — słowo kluczowe zostanie wyświetlony na liście podstawowej klas pochodnych.  
  
 Należy uwzględnić hierarchię klas na poniższym rysunku, który ilustruje symulowaną kolejkę po obiad.  
  
 ![Wykres wiersza symulowane obiad](../cpp/media/vc38xp1.gif "vc38XP1")  
Wykres symulowanej kolejki po obiad  
  
 Na rysunku `Queue` jest klasą bazową dla `CashierQueue` i `LunchQueue`. Jednakże, gdy obie klasy są połączone, tworząc `LunchCashierQueue`, pojawia się następujący problem: nowa klasa zawiera dwa podobiekty typu `Queue`, jeden `CashierQueue`, a drugi `LunchQueue`. Na poniższej ilustracji pokazano koncepcyjny układ pamięci (rzeczywisty układ pamięci może być zoptymalizowany).  
  
 ![Symulowane obiad &#45; obiekt](../cpp/media/vc38xp2.gif "vc38XP2")  
Obiekt symulowanej kolejki po obiad  
  
 Należy zauważyć, że istnieją dwa podobiekty `Queue` w obiekcie `LunchCashierQueue`. W poniższym kodzie `Queue` zadeklarowano jako wirtualną klasę bazową:  
  
```  
// deriv_VirtualBaseClasses.cpp  
// compile with: /LD  
class Queue {};  
class CashierQueue : virtual public Queue {};  
class LunchQueue : virtual public Queue {};  
class LunchCashierQueue : public LunchQueue, public CashierQueue {};  
```  
  
 Słowo kluczowe `virtual` zapewnia, że zawarta jest tylko jedna kopia podobiektu `Queue` (patrz poniższy rysunek).  
  
 ![Symulowane obiad &#45; obiektu wiersza i wirtualne klasy podstawowe](../cpp/media/vc38xp3.gif "vc38XP3")  
Obiekt symulowanej kolejki po obiad z wirtualnymi klasami podstawowymi  
  
 Klasa może mieć zarówno wirtualny jak i niewirtualny składnik danego typu. Tak się dzieje w warunkach przedstawionych na poniższej ilustracji.  
  
 ![Składniki wirtualnej i niewirtualne klasy](../cpp/media/vc38xp4.gif "vc38XP4")  
Wirtualne i niewirtualne składniki tej samej klasy  
  
 Na rysunku `CashierQueue` i `LunchQueue` używają `Queue` jako wirtualnej klasy bazowej. Jednak `TakeoutQueue` określa `Queue` jako klasę bazową, a nie wirtualną klasę bazową. W związku z tym `LunchTakeoutCashierQueue` posiada dwa podobiekty typu `Queue`: jeden ze ścieżki dziedziczenia, która zawiera `LunchCashierQueue` a drugi ze ścieżki, która zawiera `TakeoutQueue`. To zostało zilustrowane na poniższym rysunku.  
  
 ![Wirtualne i niewirtualne dziedziczenia w układzie obiektu](../cpp/media/vc38xp5.gif "vc38XP5")  
Układ obiektu z wirtualnym i niewirtualnym dziedziczeniem  
  
> [!NOTE]
>  Dziedziczenie wirtualne zapewnia znaczące korzyści dotyczące rozmiaru w porównaniu do dziedziczenia niewirtualnego. Jednak może to wprowadzić dodatkowe obciążenie dotyczące przetwarzania.  
  
 Jeśli w klasie pochodnej przeciążono funkcję wirtualną, która jest dziedziczona z wirtualnej klasy bazowej, oraz jeśli konstruktor lub destruktor klasy pochodnej wywołuje tę funkcję za pomocą wskaźnika do wirtualnej klasy bazowej, kompilator może wprowadzić dodatkowe ukryte pola „vtordisp” do klas z bazami wirtualnymi. Opcja kompilatora /vd0 pomija dodanie ukrytego elementu członkowskiego przemieszczenia konstruktora/destruktora vtordisp. Domyślna opcja kompilatora /vd1 włącza je wtedy, gdy są niezbędne. Wyłącz vtordisps tylko wtedy, gdy masz pewność, że wszystkie konstruktory i destruktory klas wywołują funkcje wirtualne w sposób wirtualny.  
  
 Opcja kompilatora /vd wpływa na cały moduł kompilacji. Użyj **vtordisp** pragma, aby wyłączyć i ponownie włączyć vtordisp — pola na podstawie klasy klasy:  
  
```  
#pragma vtordisp( off )  
class GetReal : virtual public { ... };  
#pragma vtordisp( on )  
```  
  
## <a name="name-ambiguities"></a>Niejednoznaczności nazw  
 Wielokrotne dziedziczenie wprowadza dla nazw możliwość dziedziczenia wzdłuż więcej niż jednej ścieżki. Nazwy klas składowych wzdłuż tych ścieżek nie muszą być unikatowe. Te konflikty nazw są nazywane „niejasnościami”.  
  
 Dowolne wyrażenie, które odwołuje się do składowej klasy, musi być jednoznacznym odniesieniem. W poniższym przykładzie pokazano, jak rozwijają się niejasności:  
  
```  
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
  
```  
C *pc = new C;  
  
pc->b();  
```  
  
 Należy rozważyć poprzedni przykład. Ponieważ nazwa `a` jest składową obu klas `A` i `B`, kompilator nie może rozpoznać, które `a` wyznacza funkcję, która ma być wywoływana. Dostęp do elementu członkowskiego jest niejednoznaczny, jeżeli może odnosić się do więcej niż jednej funkcji, obiektu, typu lub modułu wyliczającego.  
  
 Kompilator wykrywa niejasności wykonując testy w następującej kolejności:  
  
1.  Jeśli dostęp do nazwy jest niejednoznaczny (jak opisano powyżej), generowany jest komunikat o błędzie.  
  
2.  Jeśli funkcje przeciążone są jednoznaczne, są one rozwiązane.
  
3.  Jeśli dostęp do nazwy narusza uprawnienia dostępu do elementu członkowskiego, generowany jest komunikat o błędzie. (Aby uzyskać więcej informacji, zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md).)  
  
 Gdy wyrażenie powoduje niejednoznaczność poprzez dziedziczenie, można ją rozwiązać ręcznie kwalifikując nazwę w pytaniu o nazwę klasy. Aby w poprzednim przykładzie skompilować poprawnie, bez niejasności, należy użyć kodu takiego jak:  
  
```  
C *pc = new C;  
  
pc->B::a();  
```  
  
> [!NOTE]
>  Gdy zadeklarowane jest `C`, może ono powodować błędy, podczas gdy ma miejsce odwołanie do `B` w zakresie `C`. Błąd nie jest zgłaszany, do chwili faktycznego dokonania niekwalifikowanego odwołania do `B` w zakresie `C`.  
  
### <a name="dominance"></a>Dominacja  
 Istnieje możliwość dla więcej niż jedną nazwę (funkcja, obiektu lub moduł wyliczający) można połączyć się za pośrednictwem Wykres dziedziczenia. Takiej sytuacji, są traktowane jako niejednoznaczny z niewirtualnych klas podstawowych. Są one również niejednoznaczne z wirtualnymi klasami podstawowymi, chyba że jedną z nazw "dominuje" innych.  
  
 Nazwę dominuje inną nazwę, jeśli jest on zdefiniowany w obu klasach i jedna klasa pochodzi od innych. Nazwa dominująca jest nazwą w klasie pochodnej; Ta nazwa jest używana, gdy niejednoznaczności mogłyby w przeciwnym razie pojawiły się, jak pokazano w poniższym przykładzie:  
  
```  
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
 Jawne i niejawne konwersje z wskaźniki lub odwołania do typu klasy może powodować niejednoznaczności. Następny rysunek niejednoznaczne konwersji wskaźniki do klasy podstawowej, przedstawiono poniżej:  
  
-   Deklaracja typu obiektu `D`.  
  
-   Skutek stosowania address-of — operator (**&**) do tego obiektu. Należy pamiętać, że operator address-of zawsze dostarcza adres podstawowy obiektu.  
  
-   Efekt jawnej konwersji wskaźnika uzyskany przy użyciu operator address-of na typ klasy podstawowej `A`. Należy zwrócić uwagę coercing adresu obiektu na typ `A*` nie zawsze daje kompilator za mało informacje określające, które podobiektów typu `A` wybierz; w takim przypadku istnieją dwa podobiektów.  
  
 ![Niejednoznaczne konwersji wskaźników do klasy podstawowej](../cpp/media/vc38xt1.gif "vc38XT1")  
Niejednoznaczne konwersja wskaźniki do klas podstawowych  
  
 Konwersja na typ `A*` (wskaźnik do `A`) jest niejednoznaczny, ponieważ nie istnieje sposób do wykrycia które podobiektów typu `A` jest poprawne. Należy pamiętać, że można uniknąć niejednoznaczności, jawnie określając podobiektów, który miał zostać użyty w następujący sposób:  
  
```  
(A *)(B *)&d       // Use B subobject.  
(A *)(C *)&d       // Use C subobject.  
```  
  
### <a name="ambiguities-and-virtual-base-classes"></a>Niejednoznaczności i wirtualne klasy podstawowe  
 Jeśli wirtualne klasy podstawowe są używane, funkcje, obiekty, typy i moduły wyliczające można osiągnąć za pośrednictwem ścieżki dziedziczenia wielokrotnego. Ponieważ istnieje tylko jedno wystąpienie klasy podstawowej, brak nie niejednoznaczności podczas uzyskiwania dostępu do tych nazw.  
  
 Poniższy rysunek przedstawia sposób obiekty są składa wirtualnej i niewirtualna dziedziczenia.  
  
 ![Wirtualne pochodnym i niewirtualne informacje](../cpp/media/vc38xr1.gif "vc38XR1")  
Vs wirtualnego. Niewirtualne informacje  
  
 Na ilustracji, podczas uzyskiwania dostępu do członków klasy `A` przez niewirtualnych klas podstawowych przyczyn jako niejednoznaczności; kompilator nie zawiera informacji o który wyjaśnia, czy ma być używany podobiektów skojarzone z `B` lub podobiektów skojarzone z `C`. Jednakże, gdy `A` jest określony jako wirtualna klasa podstawowa pozostaje nie podobiektów, który jest dostępny.  
  
## <a name="see-also"></a>Zobacz też  
 [Dziedziczenie](../cpp/inheritance-cpp.md)