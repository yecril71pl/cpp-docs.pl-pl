---
title: "C2600 błędy kompilatora za pośrednictwem C2699 | Dokumentacja firmy Microsoft"
ms.date: 10/25/2017
ms.technology: cpp-tools
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
dev_langs: C++
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70ea205ef770fe98cb94cbfc4107fdb4af6560b5
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-errors-c2600-through-c2699"></a>C2600 błędy kompilatora za pośrednictwem C2699

Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.

> [!NOTE]
> Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).

|Błąd|Komunikat|
|-----------|-------------|
|[C2600 błąd kompilatora](compiler-error-c2600.md)|"*funkcja*": nie można zdefiniować generowane przez kompilator specjalnej funkcji członkowskiej (musi być zadeklarowana w klasie najpierw)|
|[C2601 błąd kompilatora](compiler-error-c2601.md)|"*funkcja*": definicje funkcji lokalnych są niedozwolone|
|[C2602 błąd kompilatora](compiler-error-c2602.md)|"*klasy*::*identyfikator*"nie jest elementem członkowskim jest klasą podstawową"*klasy*"|
|[C2603 błąd kompilatora](compiler-error-c2603.md)|"*funkcja*": zbyt wiele bloku zakresem statycznych obiektów z konstruktorem/destruktorami w funkcji|
|C2604 błąd kompilatora|"*identyfikator*": nie można zaimplementować więcej niż jednej metody interfejsu|
|[C2605 błąd kompilatora](compiler-error-c2605.md)|"*identyfikator*": Ta metoda jest zastrzeżony w obrębie klasy managed WinRT|
|C2606 błąd kompilatora|"*class1*": nie można zaimplementować ponownie "*elementu członkowskiego*", ponieważ jest odziedziczone z podstawowego środowiska uruchomieniowego"*class2*"|
|C2607 błąd kompilatora|nie powiodła się asercja statyczna|
|C2608 błąd kompilatora|Nieaktualne.|
|C2609 błąd kompilatora|Nieaktualne.|
|C2610 błąd kompilatora|"*klasy*::*elementu członkowskiego*": nie jest funkcją członkowską specjalne, które można przywrócić wartość domyślną|
|[C2611 błąd kompilatora](compiler-error-c2611.md)|"*tokenu*": niedozwolony następujące "~" (oczekiwany identyfikator)|
|[C2612 błąd kompilatora](compiler-error-c2612.md)|końcowe znaki "*znak*" niedozwolony na liście inicjatora podstawowych/elementów członkowskich|
|[C2613 błąd kompilatora](compiler-error-c2613.md)|końcowe znaki "*znak*" niedozwolony na liście klas podstawowych|
|[C2614 błąd kompilatora](compiler-error-c2614.md)|"*klasy*": niedozwolona Inicjalizacja elementu członkowskiego: "*identyfikator*" nie jest podstawowym lub elementu członkowskiego|
|C2615 błąd kompilatora|Nieaktualne.|
|[C2616 błąd kompilatora](compiler-error-c2616.md)|"*konwersji*": nie można niejawnie przekonwertować non-lvalue "*type1*" do "*type2*" nie jest to stała|
|[C2617 błąd kompilatora](compiler-error-c2617.md)|"*funkcja*": niespójna instrukcja return|
|C2618 błąd kompilatora|Nieaktualne.|
|[C2619 błąd kompilatora](compiler-error-c2619.md)|"*identyfikator*": statyczny element członkowski danych nie jest dozwolona w anonimowej strukturze/związku|
|C2620 błąd kompilatora|Nieaktualne.|
|C2621 błąd kompilatora|Nieaktualne.|
|C2622 błąd kompilatora|Nieaktualne.|
|C2623 błąd kompilatora|Nieaktualne.|
|[C2624 błąd kompilatora](compiler-error-c2624.md)|"*zakres*::*typu*': klas lokalnych nie można zadeklarować zmienne 'extern'|
|C2625 błąd kompilatora|"*identyfikator*": Niedozwolony element członkowski typu union; typ "*typu*" jest typem referencyjnym|
|[C2626 błąd kompilatora](compiler-error-c2626.md)|"*identyfikator*": element członkowski prywatnego/chronionych danych nie jest dozwolona w anonimowej strukturze/związku|
|[C2627 błąd kompilatora](compiler-error-c2627.md)|"*funkcja*": funkcja członkowska nie jest dozwolona w anonimowym związku|
|[C2628 błąd kompilatora](compiler-error-c2628.md)|"*type1*"znak"*type2*" jest niedozwolony (zapomnialeś ";"?)|
|C2629 błąd kompilatora|"*identyfikator*": anonimowe struct/union nie można zadeklarować typu zagnieżdżonego|
|[C2630 błąd kompilatora](compiler-error-c2630.md)|"*symbol*" w czymś co powinno być rozdzielaną przecinkami listą|
|C2631 błąd kompilatora|"*identyfikator*": klasy lub wyliczenia nie może być zdefiniowana w szablonie aliasu|
|[C2632 błąd kompilatora](compiler-error-c2632.md)|"*type1*"znak"*type2*" jest niedozwolony|
|[C2633 błąd kompilatora](compiler-error-c2633.md)|"*identyfikator*": "inline" jest jedyną dozwoloną klasą magazynu dla konstruktorów|
|[C2634 błąd kompilatora](compiler-error-c2634.md)|"*klasy*::*elementu członkowskiego*": wskaźnik do odwołania elementu członkowskiego jest niedozwolony|
|[C2635 błąd kompilatora](compiler-error-c2635.md)|Nie można przekonwertować "*type1*\*" do "*type2*\*"; technicznego konwersję z wirtualnej klasy podstawowej|
|[C2636 błąd kompilatora](compiler-error-c2636.md)|"*identyfikator*": wskaźnik do odwołania elementu członkowskiego jest niedozwolony|
|[C2637 błąd kompilatora](compiler-error-c2637.md)|"*identyfikator*": nie można modyfikować wskaźników do elementów członkowskich danych|
|[C2638 błąd kompilatora](compiler-error-c2638.md)|"*identyfikator*": modyfikator __based jest niedozwolony we wskaźniku do elementu członkowskiego|
|C2639 błąd kompilatora|Nieaktualne.|
|[C2640 błąd kompilatora](compiler-error-c2640.md)|"*identyfikator*": modyfikator __based jest niedozwolony dla odwołania|
|C2641 błąd kompilatora|Nieaktualne.|
|C2642 błąd kompilatora|Nieaktualne.|
|C2643 błąd kompilatora|Nieaktualne.|
|C2644 błąd kompilatora|Nieaktualne.|
|[C2645 błąd kompilatora](compiler-error-c2645.md)|Nazwa niekwalifikowana dla wskaźnika do elementu członkowskiego (znaleziono ':: * ")|
|[C2646 błąd kompilatora](compiler-error-c2646.md)|struktury/Unii anonimowej globalnie lub zakresie przestrzeni nazw musi być zadeklarowany jako statyczny|
|[C2647 błąd kompilatora](compiler-error-c2647.md)|"*operator*": nie można wyłuskać "*type1*" na "*type2*"|
|[C2648 błąd kompilatora](compiler-error-c2648.md)|"*identyfikator*": użycie elementu członkowskiego jako parametru domyślnego wymaga statycznego elementu członkowskiego|
|[C2649 błąd kompilatora](compiler-error-c2649.md)|"*identyfikator*": nie jest "class/struct/union'|
|[C2650 błąd kompilatora](compiler-error-c2650.md)|"*operator*": nie może być wirtualną funkcją|
|[C2651 błąd kompilatora](compiler-error-c2651.md)|"*typu*": po lewej stronie "::" musi być klasy, struktury lub związku|
|[C2652 błąd kompilatora](compiler-error-c2652.md)|"*identyfikator*": niedozwolony Konstruktor kopiujący: pierwszy parametr nie może być "*typu*"|
|[C2653 błąd kompilatora](compiler-error-c2653.md)|"*identyfikator*": nie jest nazwą klasy lub przestrzeni nazw|
|[C2654 błąd kompilatora](compiler-error-c2654.md)|"*identyfikator*": próba dostępu do członka poza funkcją członkowską|
|[C2655 błąd kompilatora](compiler-error-c2655.md)|"*identyfikator*": definicja lub ponowna deklaracja jest niedozwolona w bieżącym zakresie|
|[C2656 błąd kompilatora](compiler-error-c2656.md)|"*funkcja*": funkcja nie jest dozwolona jako pole bitowe|
|[C2657 błąd kompilatora](compiler-error-c2657.md)|"*klasy*:: *" znaleziono w chwili rozpoczęcia instrukcji (Czy pamiętasz o określeniu typu?)|
|[C2658 błąd kompilatora](compiler-error-c2658.md)|"*identyfikator*": ponowna definicja w anonimowej strukturze/związku|
|[C2659 błąd kompilatora](compiler-error-c2659.md)|"*operator*": funkcja jako lewy operand|
|[C2660 błąd kompilatora](compiler-error-c2660.md)|"*funkcja*": funkcja nie przyjmuje *numer* argumentów|
|[C2661 błąd kompilatora](compiler-error-c2661.md)|"*funkcja*": Brak przeciążonej funkcji przyjmującej *numer* argumentów|
|[C2662 błąd kompilatora](compiler-error-c2662.md)|"*funkcja*": nie można konwertować wskaźnika "this" z "*type1*"do"*type2*"|
|[C2663 błąd kompilatora](compiler-error-c2663.md)|"*funkcja*": *numer* przeciążenia nie posiadają dozwolonej konwersji dla wskaźnika "this"|
|[C2664 błąd kompilatora](compiler-error-c2664.md)|"*funkcja*": nie można przekonwertować argumentu *numer* z "*type1*"do"*type2*"|
|[C2665 błąd kompilatora](compiler-error-c2665.md)|"*funkcja*": żaden z *numer* przeciążenia może konwertować wszystkich typów argumentów|
|[C2666 błąd kompilatora](compiler-error-c2666.md)|"*funkcja*": *numer* przeciążenia mają podobne konwersje|
|[C2667 błąd kompilatora](compiler-error-c2667.md)|"*funkcja*": żaden z *numer* przeciążenia nie posiada najlepszej konwersji|
|[C2668 błąd kompilatora](compiler-error-c2668.md)|"*funkcja*": niejednoznaczne wywołanie przeciążonej funkcji|
|[C2669 błąd kompilatora](compiler-error-c2669.md)|Funkcja członkowska nie jest dozwolona w anonimowym związku|
|[C2670 błąd kompilatora](compiler-error-c2670.md)|"*funkcja*": funkcja szablonu nie można przekonwertować parametru *numer* z typu "*typu*"|
|[C2671 błąd kompilatora](compiler-error-c2671.md)|"*funkcja*": statyczne funkcje Członkowskie nie posiadają wskaźników "this"|
|[C2672 błąd kompilatora](compiler-error-c2672.md)|"*funkcja*": nie zgodnej przeciążonej funkcji znaleziono|
|[C2673 błąd kompilatora](compiler-error-c2673.md)|"*funkcja*": funkcje globalne nie posiadają wskaźników "this"|
|[C2674 błąd kompilatora](compiler-error-c2674.md)|Deklaracja generyczna nie jest dozwolona w tym kontekście|
|[C2675 błąd kompilatora](compiler-error-c2675.md)|Jednoargumentowy "*operator*": "*typu*" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora|
|[C2676 błąd kompilatora](compiler-error-c2676.md)|binarne "*operator*": "*typu*" nie definiuje tego operatora lub konwersji do typu akceptowalnego dla wstępnie zdefiniowanego operatora|
|[C2677 błąd kompilatora](compiler-error-c2677.md)|binarne "*operator*": nie znaleziono żadnego globalnego operatora który przyjmuje typ "*typu*" (lub nie jest dopuszczalne konwersja)|
|[C2678 błąd kompilatora](compiler-error-c2678.md)|binarne "*operator*": nie znaleziono żadnych operatora, który przyjmuje lewostronny operand typu "*typu*" (lub nie jest dopuszczalne konwersja)|
|[C2679 błąd kompilatora](compiler-error-c2679.md)|binarne "*operator*": nie znaleziono żadnych operatora, który przyjmuje prawostronny operand typu "*typu*" (lub nie jest dopuszczalne konwersja)|
|[C2680 błąd kompilatora](compiler-error-c2680.md)|"*typu*": nieprawidłowy typ docelowy dla *rzutowania*|
|[C2681 błąd kompilatora](compiler-error-c2681.md)|"*typu*": nieprawidłowy typ wyrażenia dla *rzutowania*|
|[C2682 błąd kompilatora](compiler-error-c2682.md)|Nie można użyć "*rzutowania*" do konwersji z"*type1*"do"*type2*"|
|[C2683 błąd kompilatora](compiler-error-c2683.md)|"*rzutowania*": "*typu*" nie jest typem polimorficznym|
|C2684 błąd kompilatora|"*deklarator*": funkcje usunięte i domyślne nie są obsługiwane w klasach managed WinRT|
|C2685 błąd kompilatora|"*deklarator*": funkcje usunięte i domyślne nie są obsługiwane z jawnymi specyfikatorami ograniczeń|
|C2686 błąd kompilatora|Nie można przeciążać statycznej i niestatycznej funkcji Członkowskich z tymi samymi typami parametrów|
|[C2687 błąd kompilatora](compiler-error-c2687.md)|"*typu*": zgłoszenie wyjątku nie może być "void" lub oznaczeniem niekompletnego typu lub wskaźnikiem lub odwołaniem do niekompletnego typu|
|[C2688 błąd kompilatora](compiler-error-c2688.md)|"*typu*::*elementu członkowskiego*": kowariantne wyniki zwracane z wielokrontym lub wirtualnym dziedziczeniem nie są obsługiwane przez funkcję varargs|
|[C2689 błąd kompilatora](compiler-error-c2689.md)|"*funkcja*": funkcja zaprzyjaźniona nie może być zdefiniowana w ramach lokalnej klasy|
|[C2690 błąd kompilatora](compiler-error-c2690.md)|"*operator*": nie można wykonać arytmetyki wskaźnika na tablicy managed WinRT|
|[C2691 błąd kompilatora](compiler-error-c2691.md)|"*typu*": tablica managed WinRT nie może posiadać tego typu elementu|
|[C2692 błąd kompilatora](compiler-error-c2692.md)|"*funkcji*": funkcje wymagane w kompilatorze języka C z w pełni prototypowane "/ clr" — opcja|
|[C2693 błąd kompilatora](compiler-error-c2693.md)|"*operator*": niedozwolone porównanie dla odwołań do tablicy managed WinRT|
|[C2694 błąd kompilatora](compiler-error-c2694.md)|"*override_function*": przesłanianie wirtualnej funkcji ma mniej restrykcyjną specyfikację wyjątku niż klasa podstawowa wirtualnej funkcji członkowskiej "*base_function*"|
|[C2695 błąd kompilatora](compiler-error-c2695.md)|"*override_function*": przesłanianie wirtualnej funkcji różni się od "*base_function*" tylko przez konwencji wywoływania|
|[C2696 błąd kompilatora](compiler-error-c2696.md)|Nie można utworzyć tymczasowego obiektu typu zarządzanego WinRT "*typu*"|
|C2697 błąd kompilatora|Nieaktualne.|
|[C2698 błąd kompilatora](compiler-error-c2698.md)|Deklaracja using dla "*declaration1*" nie może współistnieć z istniejącą deklaracją using dla"*declaration2*"|
