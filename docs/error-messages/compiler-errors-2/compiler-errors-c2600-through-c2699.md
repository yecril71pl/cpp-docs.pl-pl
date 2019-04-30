---
title: Błędy kompilatora — od C2600 do C2699
ms.date: 04/21/2019
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
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
ms.openlocfilehash: 9ac5f5724490574aecf0e5b542f6fdd42b0ae5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406512"
---
# <a name="compiler-errors-c2600-through-c2699"></a>Błędy kompilatora — od C2600 do C2699

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2600](compiler-error-c2600.md)|"*funkcja*": nie można zdefiniować generowanych przez kompilator specjalną funkcję członkowską (musi być zadeklarowana w klasie najpierw)|
|[Błąd kompilatora C2601](compiler-error-c2601.md)|"*funkcja*": definicje funkcji lokalnych są niedozwolone|
|[Błąd kompilatora C2602](compiler-error-c2602.md)|"*klasy*::*identyfikator*"nie jest elementem członkowskim klasy bazowej"*klasy*"|
|[Błąd kompilatora C2603](compiler-error-c2603.md)|"*funkcja*": Zbyt wiele bloku statycznych obiektów w zakresie z konstruktorem/destruktorami w funkcji|
|Błąd kompilatora C2604|"*identyfikator*": Nie można zaimplementować więcej niż jednej metody interfejsu|
|[Błąd kompilatora C2605](compiler-error-c2605.md)|"*identyfikator*": Ta metoda jest zastrzeżona w obrębie klasy zarządzane/WinRT|
|Błąd kompilatora C2606|"*klasa1*": nie można zaimplementować ponownie "*elementu członkowskiego*", ponieważ jest odziedziczone z podstawowego środowiska uruchomieniowego"*klasa2*"|
|Błąd kompilatora C2607|asercja statyczna nie powiodło się|
|Błąd kompilatora C2608|Nieaktualne.|
|Błąd kompilatora C2609|Nieaktualne.|
|Błąd kompilatora C2610|"*klasy*::*elementu członkowskiego*": Brak funkcji specjalnych elementów członkowskich, które może być ustawiana domyślnie|
|[Błąd kompilatora C2611](compiler-error-c2611.md)|"*tokenu*": niedozwolony następujące "~" (oczekiwany identyfikator)|
|[Błąd kompilatora C2612](compiler-error-c2612.md)|końcowe "*znak*" niedozwolony na liście inicjatora bazowych/składowych|
|[Błąd kompilatora C2613](compiler-error-c2613.md)|końcowe "*znak*" niedozwolony na liście klas bazowych|
|[Błąd kompilatora C2614](compiler-error-c2614.md)|"*klasy*": niedozwolone inicjowanie składowej: "*identyfikator*" nie jest obiektem bazowym ani składową|
|Błąd kompilatora C2615|Nieaktualne.|
|[Błąd kompilatora C2616](compiler-error-c2616.md)|"*konwersji*": nie można niejawnie przekonwertować non-lvalue "*type1*" do "*type2*' który nie jest stałą|
|[Błąd kompilatora C2617](compiler-error-c2617.md)|"*funkcja*": niespójna instrukcja return|
|Błąd kompilatora C2618|Nieaktualne.|
|[Błąd kompilatora C2619](compiler-error-c2619.md)|"*identyfikator*": statyczna składowa danych nie jest dozwolona w anonimowej strukturze/związku|
|Błąd kompilatora C2620|Nieaktualne.|
|Błąd kompilatora C2621|Nieaktualne.|
|Błąd kompilatora C2622|Nieaktualne.|
|Błąd kompilatora C2623|Nieaktualne.|
|[Błąd kompilatora C2624](compiler-error-c2624.md)|"*zakres*::*typu*': klas lokalnych nie można zadeklarować zmienne 'extern'|
|Błąd kompilatora C2625|"*identyfikator*": niedozwolony składowa Unii; typ "*typu*" jest typem referencyjnym|
|[Błąd kompilatora C2626](compiler-error-c2626.md)|"*identyfikator*": składowa/prywatnych, chronionych danych nie jest dozwolona w anonimowej strukturze/związku|
|[Błąd kompilatora C2627](compiler-error-c2627.md)|"*funkcja*": funkcja składowa nie jest dozwolona w anonimowej Unii|
|[Błąd kompilatora C2628](compiler-error-c2628.md)|"*type1*"następuje"*type2*" jest niedozwolony (zapomnialeś ';'?)|
|Błąd kompilatora C2629|"*identyfikator*": anonimowy struktury/Unii nie można zadeklarować typu zagnieżdżonego|
|[Błąd kompilatora C2630](compiler-error-c2630.md)|"*symbol*" w czymś co powinno być rozdzielaną przecinkami listę|
|Błąd kompilatora C2631|"*identyfikator*": klasy lub wyliczenia nie może być zdefiniowana w szablonie aliasu|
|[Błąd kompilatora C2632](compiler-error-c2632.md)|"*type1*"następuje"*type2*" jest niedozwolony|
|[Błąd kompilatora C2633](compiler-error-c2633.md)|"*identyfikator*": "inline" jest jedyną dozwoloną klasą magazynu dla konstruktorów|
|[Błąd kompilatora C2634](compiler-error-c2634.md)|"*klasy*::*elementu członkowskiego*": wskaźnik do odwołania składowej jest niedozwolony|
|[Błąd kompilatora C2635](compiler-error-c2635.md)|Nie można przekonwertować "*type1*\*" do "*type2*\*"; jest implikowane konwersję z wirtualnej klasy bazowej|
|[Błąd kompilatora C2636](compiler-error-c2636.md)|"*identyfikator*": wskaźnik do odwołania składowej jest niedozwolony|
|[Błąd kompilatora C2637](compiler-error-c2637.md)|"*identyfikator*": nie można modyfikować wskaźników do składowych danych|
|[Błąd kompilatora C2638](compiler-error-c2638.md)|"*identyfikator*": modyfikator __based jest niedozwolony we wskaźniku do składowej|
|Błąd kompilatora C2639|Nieaktualne.|
|[Błąd kompilatora C2640](compiler-error-c2640.md)|"*identyfikator*": modyfikator __based niedozwolony dla odwołania|
|Błąd kompilatora C2641|Nieaktualne.|
|Błąd kompilatora C2642|Nieaktualne.|
|Błąd kompilatora C2643|Nieaktualne.|
|Błąd kompilatora C2644|Nieaktualne.|
|[Błąd kompilatora C2645](compiler-error-c2645.md)|Nazwa niekwalifikowana dla wskaźnika do składowej (znaleziono ":: *")|
|[Błąd kompilatora C2646](compiler-error-c2646.md)|anonimowej strukturze/związku globalnie lub zakresie przestrzeni nazw musi być zadeklarowane jako statyczne|
|[Błąd kompilatora C2647](compiler-error-c2647.md)|"*operator*": nie można wyłuskać "*type1*" na "*type2*"|
|[Błąd kompilatora C2648](compiler-error-c2648.md)|"*identyfikator*": użycie składowej jako parametru domyślnego wymaga statycznej składowej|
|[Błąd kompilatora C2649](compiler-error-c2649.md)|"*identyfikator*": nie jest "class/struct/union"|
|[Błąd kompilatora C2650](compiler-error-c2650.md)|"*operator*": nie może być wirtualną funkcją|
|[Błąd kompilatora C2651](compiler-error-c2651.md)|"*typu*": po lewej stronie "::" musi być klasy, struktury lub Unii|
|[Błąd kompilatora C2652](compiler-error-c2652.md)|"*identyfikator*": niedozwolony Konstruktor kopiujący: pierwszy parametr nie może być "*typu*"|
|[Błąd kompilatora C2653](compiler-error-c2653.md)|"*identyfikator*": nie jest klasą lub przestrzenią nazw|
|[Błąd kompilatora C2654](compiler-error-c2654.md)|"*identyfikator*": próba uzyskania dostępu do składowej spoza funkcji składowej|
|[Błąd kompilatora C2655](compiler-error-c2655.md)|"*identyfikator*": definicja lub ponowna deklaracja jest niedozwolona w bieżącym zakresie|
|[Compiler error C2656](compiler-error-c2656.md)|"*funkcja*": funkcja nie jest dozwolona jako pole bitowe|
|[Błąd kompilatora C2657](compiler-error-c2657.md)|"*klasy*:: *" znaleziono w chwili rozpoczęcia instrukcji (Czy pamiętasz o określeniu typu?)|
|[Błąd kompilatora C2658](compiler-error-c2658.md)|"*identyfikator*": ponowna definicja w anonimowej strukturze/związku|
|[Compiler error C2659](compiler-error-c2659.md)|"*operator*": funkcja jako lewy operand|
|[Błąd kompilatora C2660](compiler-error-c2660.md)|"*funkcja*": funkcja nie przyjmuje *numer* argumentów|
|[Błąd kompilatora C2661](compiler-error-c2661.md)|"*funkcja*": Brak przeciążonej funkcji przyjmującej *numer* argumentów|
|[Błąd kompilatora C2662](compiler-error-c2662.md)|"*funkcja*": nie można konwertować wskaźnika "this" z "*type1*"to"*type2*"|
|[Błąd kompilatora C2663](compiler-error-c2663.md)|"*funkcja*": *numer* przeciążenia nie posiadają dozwolonej konwersji dla wskaźnika "this"|
|[Błąd kompilatora C2664](compiler-error-c2664.md)|"*funkcja*": nie można przekonwertować argumentu *numer* z "*type1*"to"*type2*"|
|[Błąd kompilatora C2665](compiler-error-c2665.md)|"*funkcja*": żaden z *numer* przeciążenia może konwertować wszystkich typów argumentów|
|[Błąd kompilatora C2666](compiler-error-c2666.md)|"*funkcja*": *numer* przeciążenia mają podobne konwersje|
|[Błąd kompilatora C2667](compiler-error-c2667.md)|"*funkcja*": żaden z *numer* przeciążenia nie posiada najlepszej konwersji|
|[Błąd kompilatora C2668](compiler-error-c2668.md)|"*funkcja*": niejednoznaczne wywołanie przeciążonej funkcji|
|[Compiler error C2669](compiler-error-c2669.md)|Funkcja składowa nie jest dozwolona w anonimowej Unii|
|[Błąd kompilatora C2670](compiler-error-c2670.md)|"*funkcja*": szablon funkcji nie można przekonwertować parametru *numer* z typu "*typu*"|
|[Błąd kompilatora C2671](compiler-error-c2671.md)|"*funkcja*": statyczne funkcje Członkowskie nie mają wskaźników "this"|
|[Błąd kompilatora C2672](compiler-error-c2672.md)|"*funkcja*": nie zgodnej przeciążonej funkcji, o których odnaleźć|
|[Błąd kompilatora C2673](compiler-error-c2673.md)|"*funkcja*": funkcje globalne nie mają wskaźników "this"|
|[Błąd kompilatora C2674](compiler-error-c2674.md)|w tym kontekście deklaracji ogólnej jest niedozwolone.|
|[Błąd kompilatora C2675](compiler-error-c2675.md)|Jednoargumentowy "*operator*": "*typu*" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora|
|[Błąd kompilatora C2676](compiler-error-c2676.md)|binarny "*operator*": "*typu*" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora|
|[Błąd kompilatora C2677](compiler-error-c2677.md)|binarny "*operator*": znaleziono żadnego globalnego operatora, który przyjmuje typ "*typu*" (lub nie jest dopuszczalne konwersja)|
|[Błąd kompilatora C2678](compiler-error-c2678.md)|binarny "*operator*": znaleziono żadnego operatora, który przyjmuje lewostronny operand typu "*typu*" (lub nie jest dopuszczalne konwersja)|
|[Błąd kompilatora C2679](compiler-error-c2679.md)|binarny "*operator*": znaleziono żadnego operatora, który przyjmuje prawostronny operand typu "*typu*" (lub nie jest dopuszczalne konwersja)|
|[Błąd kompilatora C2680](compiler-error-c2680.md)|"*typu*": nieprawidłowy typ docelowy dla *rzutowania*|
|[Błąd kompilatora C2681](compiler-error-c2681.md)|"*typu*": nieprawidłowy typ wyrażenia dla *rzutowania*|
|[Błąd kompilatora C2682](compiler-error-c2682.md)|Nie można użyć "*rzutowania*" do konwersji z"*type1*"to"*type2*"|
|[Błąd kompilatora C2683](compiler-error-c2683.md)|"*rzutowania*": "*typu*" nie jest typem polimorficznym|
|Błąd kompilatora C2684|"*deklaratora*": funkcje usunięte i domyślne nie są obsługiwane w klasach zarządzane/WinRT|
|Błąd kompilatora C2685|"*deklaratora*": funkcje usunięte i domyślne nie są obsługiwane z jawnymi specyfikatorami ograniczeń|
|Błąd kompilatora C2686|Nie można przeciążać statycznych i niestatycznych elementów członkowskich z tymi samymi typami parametrów|
|[Błąd kompilatora C2687](compiler-error-c2687.md)|"*typu*": zgłoszenie wyjątku nie może być "void" lub oznaczeniem typu niekompletnego lub wskaźnikiem bądź odwołaniem do niekompletnego typu|
|[Błąd kompilatora C2688](compiler-error-c2688.md)|"*typu*::*elementu członkowskiego*": kowariantne zwracane z wielokrontym lub wirtualnym dziedziczeniem nie są obsługiwane przez funkcję VarArgs|
|[Compiler error C2689](compiler-error-c2689.md)|"*funkcja*": funkcja zaprzyjaźniona nie może być zdefiniowana w ramach lokalnej klasy|
|[Błąd kompilatora C2690](compiler-error-c2690.md)|"*operator*": nie można wykonać arytmetyki wskaźnika na tablicy zarządzane/WinRT|
|[Błąd kompilatora C2691](compiler-error-c2691.md)|"*typu*": tablica zarządzana WinRT nie może posiadać tego typu elementu|
|[Błąd kompilatora C2692](compiler-error-c2692.md)|"*funkcja*": wymagano w pełni prototypowanych funkcji w kompilatorze języka C z "/ clr" opcja|
|[Błąd kompilatora C2693](compiler-error-c2693.md)|"*operator*": niedozwolone porównanie dla odwołań do tablicy zarządzane/WinRT|
|[Błąd kompilatora C2694](compiler-error-c2694.md)|"*override_function*": przesłanianie wirtualnej funkcji ma mniej restrykcyjną specyfikację wyjątku niż klasa bazowa wirtualnej funkcji składowej "*base_function*"|
|[Błąd kompilatora C2695](compiler-error-c2695.md)|"*override_function*": przesłanianie wirtualnej funkcji różni się od "*base_function*" tylko przez Konwencję wywoływania|
|[Compiler error C2696](compiler-error-c2696.md)|Nie można utworzyć tymczasowego obiektu tego typu zarządzanego WinRT "*typu*"|
|Błąd kompilatora C2697|Nieaktualne.|
|[Błąd kompilatora C2698](compiler-error-c2698.md)|Deklaracja using dla "*declaration1*" nie może współistnieć z istniejącą deklaracją using dla"*declaration2*"|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
