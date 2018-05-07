---
title: C2600 błędy kompilatora za pośrednictwem C2699 | Dokumentacja firmy Microsoft
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
helpviewer_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
dev_langs:
- C++
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0637ff146ca71c1ee14c534792cf70c44c0616b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c2600-through-c2699"></a>C2600 błędy kompilatora za pośrednictwem C2699

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2600](compiler-error-c2600.md)|"*funkcja*": nie można zdefiniować generowane przez kompilator specjalnej funkcji członkowskiej (musi być zadeklarowana w klasie najpierw)|
|[Błąd kompilatora C2601](compiler-error-c2601.md)|"*funkcja*": definicje funkcji lokalnych są niedozwolone|
|[Błąd kompilatora C2602](compiler-error-c2602.md)|"*klasy*::*identyfikator*"nie jest elementem członkowskim jest klasą podstawową"*klasy*"|
|[Błąd kompilatora C2603](compiler-error-c2603.md)|"*funkcja*": zbyt wiele bloku zakresem statycznych obiektów z konstruktorem/destruktorami w funkcji|
|C2604 błąd kompilatora|"*identyfikator*": nie można zaimplementować więcej niż jednej metody interfejsu|
|[Błąd kompilatora C2605](compiler-error-c2605.md)|"*identyfikator*": Ta metoda jest zastrzeżony w obrębie klasy managed WinRT|
|C2606 błąd kompilatora|"*class1*": nie można zaimplementować ponownie "*elementu członkowskiego*", ponieważ jest odziedziczone z podstawowego środowiska uruchomieniowego"*class2*"|
|C2607 błąd kompilatora|nie powiodła się asercja statyczna|
|C2608 błąd kompilatora|Nieaktualne.|
|C2609 błąd kompilatora|Nieaktualne.|
|C2610 błąd kompilatora|"*klasy*::*elementu członkowskiego*": nie jest funkcją członkowską specjalne, które można przywrócić wartość domyślną|
|[Błąd kompilatora C2611](compiler-error-c2611.md)|"*tokenu*": niedozwolony następujące "~" (oczekiwany identyfikator)|
|[Błąd kompilatora C2612](compiler-error-c2612.md)|końcowe znaki "*znak*" niedozwolony na liście inicjatora podstawowych/elementów członkowskich|
|[Błąd kompilatora C2613](compiler-error-c2613.md)|końcowe znaki "*znak*" niedozwolony na liście klas podstawowych|
|[Błąd kompilatora C2614](compiler-error-c2614.md)|"*klasy*": niedozwolona Inicjalizacja elementu członkowskiego: "*identyfikator*" nie jest podstawowym lub elementu członkowskiego|
|C2615 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2616](compiler-error-c2616.md)|"*konwersji*": nie można niejawnie przekonwertować non-lvalue "*type1*" do "*type2*" nie jest to stała|
|[Błąd kompilatora C2617](compiler-error-c2617.md)|"*funkcja*": niespójna instrukcja return|
|C2618 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2619](compiler-error-c2619.md)|"*identyfikator*": statyczny element członkowski danych nie jest dozwolona w anonimowej strukturze/związku|
|C2620 błąd kompilatora|Nieaktualne.|
|C2621 błąd kompilatora|Nieaktualne.|
|C2622 błąd kompilatora|Nieaktualne.|
|C2623 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2624](compiler-error-c2624.md)|"*zakres*::*typu*': klas lokalnych nie można zadeklarować zmienne 'extern'|
|C2625 błąd kompilatora|"*identyfikator*": Niedozwolony element członkowski typu union; typ "*typu*" jest typem referencyjnym|
|[Błąd kompilatora C2626](compiler-error-c2626.md)|"*identyfikator*": element członkowski prywatnego/chronionych danych nie jest dozwolona w anonimowej strukturze/związku|
|[Błąd kompilatora C2627](compiler-error-c2627.md)|"*funkcja*": funkcja członkowska nie jest dozwolona w anonimowym związku|
|[Błąd kompilatora C2628](compiler-error-c2628.md)|"*type1*"znak"*type2*" jest niedozwolony (zapomnialeś ";"?)|
|C2629 błąd kompilatora|"*identyfikator*": anonimowe struct/union nie można zadeklarować typu zagnieżdżonego|
|[Błąd kompilatora C2630](compiler-error-c2630.md)|"*symbol*" w czymś co powinno być rozdzielaną przecinkami listą|
|C2631 błąd kompilatora|"*identyfikator*": klasy lub wyliczenia nie może być zdefiniowana w szablonie aliasu|
|[Błąd kompilatora C2632](compiler-error-c2632.md)|"*type1*"znak"*type2*" jest niedozwolony|
|[Błąd kompilatora C2633](compiler-error-c2633.md)|"*identyfikator*": "inline" jest jedyną dozwoloną klasą magazynu dla konstruktorów|
|[Błąd kompilatora C2634](compiler-error-c2634.md)|"*klasy*::*elementu członkowskiego*": wskaźnik do odwołania elementu członkowskiego jest niedozwolony|
|[Błąd kompilatora C2635](compiler-error-c2635.md)|Nie można przekonwertować "*type1*\*" do "*type2*\*"; technicznego konwersję z wirtualnej klasy podstawowej|
|[Błąd kompilatora C2636](compiler-error-c2636.md)|"*identyfikator*": wskaźnik do odwołania elementu członkowskiego jest niedozwolony|
|[Błąd kompilatora C2637](compiler-error-c2637.md)|"*identyfikator*": nie można modyfikować wskaźników do elementów członkowskich danych|
|[Błąd kompilatora C2638](compiler-error-c2638.md)|"*identyfikator*": modyfikator __based jest niedozwolony we wskaźniku do elementu członkowskiego|
|C2639 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2640](compiler-error-c2640.md)|"*identyfikator*": modyfikator __based jest niedozwolony dla odwołania|
|C2641 błąd kompilatora|Nieaktualne.|
|C2642 błąd kompilatora|Nieaktualne.|
|C2643 błąd kompilatora|Nieaktualne.|
|C2644 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2645](compiler-error-c2645.md)|Nazwa niekwalifikowana dla wskaźnika do elementu członkowskiego (znaleziono ':: * ")|
|[Błąd kompilatora C2646](compiler-error-c2646.md)|struktury/Unii anonimowej globalnie lub zakresie przestrzeni nazw musi być zadeklarowany jako statyczny|
|[Błąd kompilatora C2647](compiler-error-c2647.md)|"*operator*": nie można wyłuskać "*type1*" na "*type2*"|
|[Błąd kompilatora C2648](compiler-error-c2648.md)|"*identyfikator*": użycie elementu członkowskiego jako parametru domyślnego wymaga statycznego elementu członkowskiego|
|[Błąd kompilatora C2649](compiler-error-c2649.md)|"*identyfikator*": nie jest "class/struct/union'|
|[Błąd kompilatora C2650](compiler-error-c2650.md)|"*operator*": nie może być wirtualną funkcją|
|[Błąd kompilatora C2651](compiler-error-c2651.md)|"*typu*": po lewej stronie "::" musi być klasy, struktury lub związku|
|[Błąd kompilatora C2652](compiler-error-c2652.md)|"*identyfikator*": niedozwolony Konstruktor kopiujący: pierwszy parametr nie może być "*typu*"|
|[Błąd kompilatora C2653](compiler-error-c2653.md)|"*identyfikator*": nie jest nazwą klasy lub przestrzeni nazw|
|[Błąd kompilatora C2654](compiler-error-c2654.md)|"*identyfikator*": próba dostępu do członka poza funkcją członkowską|
|[Błąd kompilatora C2655](compiler-error-c2655.md)|"*identyfikator*": definicja lub ponowna deklaracja jest niedozwolona w bieżącym zakresie|
|[Błąd kompilatora C2656](compiler-error-c2656.md)|"*funkcja*": funkcja nie jest dozwolona jako pole bitowe|
|[Błąd kompilatora C2657](compiler-error-c2657.md)|"*klasy*:: *" znaleziono w chwili rozpoczęcia instrukcji (Czy pamiętasz o określeniu typu?)|
|[Błąd kompilatora C2658](compiler-error-c2658.md)|"*identyfikator*": ponowna definicja w anonimowej strukturze/związku|
|[Błąd kompilatora C2659](compiler-error-c2659.md)|"*operator*": funkcja jako lewy operand|
|[Błąd kompilatora C2660](compiler-error-c2660.md)|"*funkcja*": funkcja nie przyjmuje *numer* argumentów|
|[Błąd kompilatora C2661](compiler-error-c2661.md)|"*funkcja*": Brak przeciążonej funkcji przyjmującej *numer* argumentów|
|[Błąd kompilatora C2662](compiler-error-c2662.md)|"*funkcja*": nie można konwertować wskaźnika "this" z "*type1*"do"*type2*"|
|[Błąd kompilatora C2663](compiler-error-c2663.md)|"*funkcja*": *numer* przeciążenia nie posiadają dozwolonej konwersji dla wskaźnika "this"|
|[Błąd kompilatora C2664](compiler-error-c2664.md)|"*funkcja*": nie można przekonwertować argumentu *numer* z "*type1*"do"*type2*"|
|[Błąd kompilatora C2665](compiler-error-c2665.md)|"*funkcja*": żaden z *numer* przeciążenia może konwertować wszystkich typów argumentów|
|[Błąd kompilatora C2666](compiler-error-c2666.md)|"*funkcja*": *numer* przeciążenia mają podobne konwersje|
|[Błąd kompilatora C2667](compiler-error-c2667.md)|"*funkcja*": żaden z *numer* przeciążenia nie posiada najlepszej konwersji|
|[Błąd kompilatora C2668](compiler-error-c2668.md)|"*funkcja*": niejednoznaczne wywołanie przeciążonej funkcji|
|[Błąd kompilatora C2669](compiler-error-c2669.md)|Funkcja członkowska nie jest dozwolona w anonimowym związku|
|[Błąd kompilatora C2670](compiler-error-c2670.md)|"*funkcja*": funkcja szablonu nie można przekonwertować parametru *numer* z typu "*typu*"|
|[Błąd kompilatora C2671](compiler-error-c2671.md)|"*funkcja*": statyczne funkcje Członkowskie nie posiadają wskaźników "this"|
|[C2672 błąd kompilatora](compiler-error-c2672.md)|"*funkcja*": nie zgodnej przeciążonej funkcji znaleziono|
|[Błąd kompilatora C2673](compiler-error-c2673.md)|"*funkcja*": funkcje globalne nie posiadają wskaźników "this"|
|[Błąd kompilatora C2674](compiler-error-c2674.md)|Deklaracja generyczna nie jest dozwolona w tym kontekście|
|[Błąd kompilatora C2675](compiler-error-c2675.md)|Jednoargumentowy "*operator*": "*typu*" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora|
|[Błąd kompilatora C2676](compiler-error-c2676.md)|binarne "*operator*": "*typu*" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora|
|[Błąd kompilatora C2677](compiler-error-c2677.md)|binarne "*operator*": nie znaleziono żadnego globalnego operatora który przyjmuje typ "*typu*" (lub nie jest dopuszczalne konwersja)|
|[Błąd kompilatora C2678](compiler-error-c2678.md)|binarne "*operator*": nie znaleziono żadnych operatora, który przyjmuje lewostronny operand typu "*typu*" (lub nie jest dopuszczalne konwersja)|
|[Błąd kompilatora C2679](compiler-error-c2679.md)|binarne "*operator*": nie znaleziono żadnych operatora, który przyjmuje prawostronny operand typu "*typu*" (lub nie jest dopuszczalne konwersja)|
|[Błąd kompilatora C2680](compiler-error-c2680.md)|"*typu*": nieprawidłowy typ docelowy dla *rzutowania*|
|[Błąd kompilatora C2681](compiler-error-c2681.md)|"*typu*": nieprawidłowy typ wyrażenia dla *rzutowania*|
|[Błąd kompilatora C2682](compiler-error-c2682.md)|Nie można użyć "*rzutowania*" do konwersji z"*type1*"do"*type2*"|
|[Błąd kompilatora C2683](compiler-error-c2683.md)|"*rzutowania*": "*typu*" nie jest typem polimorficznym|
|C2684 błąd kompilatora|"*deklarator*": funkcje usunięte i domyślne nie są obsługiwane w klasach managed WinRT|
|C2685 błąd kompilatora|"*deklarator*": funkcje usunięte i domyślne nie są obsługiwane z jawnymi specyfikatorami ograniczeń|
|C2686 błąd kompilatora|Nie można przeciążać statycznej i niestatycznej funkcji Członkowskich z tymi samymi typami parametrów|
|[Błąd kompilatora C2687](compiler-error-c2687.md)|"*typu*": zgłoszenie wyjątku nie może być "void" lub oznaczeniem niekompletnego typu lub wskaźnikiem lub odwołaniem do niekompletnego typu|
|[Błąd kompilatora C2688](compiler-error-c2688.md)|"*typu*::*elementu członkowskiego*": kowariantne wyniki zwracane z wielokrontym lub wirtualnym dziedziczeniem nie są obsługiwane przez funkcję varargs|
|[Błąd kompilatora C2689](compiler-error-c2689.md)|"*funkcja*": funkcja zaprzyjaźniona nie może być zdefiniowana w ramach lokalnej klasy|
|[Błąd kompilatora C2690](compiler-error-c2690.md)|"*operator*": nie można wykonać arytmetyki wskaźnika na tablicy managed WinRT|
|[Błąd kompilatora C2691](compiler-error-c2691.md)|"*typu*": tablica managed WinRT nie może posiadać tego typu elementu|
|[Błąd kompilatora C2692](compiler-error-c2692.md)|"*funkcji*": funkcje wymagane w kompilatorze języka C z w pełni prototypowane "/ clr" — opcja|
|[Błąd kompilatora C2693](compiler-error-c2693.md)|"*operator*": niedozwolone porównanie dla odwołań do tablicy managed WinRT|
|[Błąd kompilatora C2694](compiler-error-c2694.md)|"*override_function*": przesłanianie wirtualnej funkcji ma mniej restrykcyjną specyfikację wyjątku niż klasa podstawowa wirtualnej funkcji członkowskiej "*base_function*"|
|[Błąd kompilatora C2695](compiler-error-c2695.md)|"*override_function*": przesłanianie wirtualnej funkcji różni się od "*base_function*" tylko przez konwencji wywoływania|
|[Błąd kompilatora C2696](compiler-error-c2696.md)|Nie można utworzyć tymczasowego obiektu typu zarządzanego WinRT "*typu*"|
|C2697 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2698](compiler-error-c2698.md)|Deklaracja using dla "*declaration1*" nie może współistnieć z istniejącą deklaracją using dla"*declaration2*"|
