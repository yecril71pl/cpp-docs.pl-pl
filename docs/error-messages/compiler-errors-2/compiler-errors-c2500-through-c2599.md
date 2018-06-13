---
title: C2500 błędy kompilatora za pośrednictwem C2599 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
dev_langs:
- C++
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 994f29009294e6b49851a817a5872fcaa122b153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284267"
---
# <a name="compiler-errors-c2500-through-c2599"></a>C2500 błędy kompilatora za pośrednictwem C2599

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2500](compiler-error-C2500.md)|"*identifier1*": "*identifier2*" jest już bezpośredniej klasie podstawowej|
|C2501 błąd kompilatora|"*identyfikator*": "__declspec (*specyfikator*)" można stosować do struktur, związków, klas lub członków pól bitowych unsigned|
|[Błąd kompilatora C2502](compiler-error-C2502.md)|"*identyfikator*": zbyt wiele modyfikatorów dostępu dla klasy podstawowej|
|[Błąd kompilatora C2503](compiler-error-C2503.md)|"*klasy*": klasy podstawowej nie mogą zawierać tablic o rozmiarze zero|
|[Błąd kompilatora C2504](compiler-error-C2504.md)|"*klasy*": klasa podstawowa niezdefiniowana|
|[Błąd kompilatora C2505](compiler-error-C2505.md)|"*symbol*": "__declspec (*specyfikator*)" można stosować do deklaracji lub definicji obiektów globalnych lub statyczne elementy członkowskie danych|
|[Błąd kompilatora C2506](compiler-error-C2506.md)|"*elementu członkowskiego*": "__declspec (*specyfikator*)" nie można zastosować do tego symbolu|
|[Błąd kompilatora C2507](compiler-error-C2507.md)|"*identyfikator*": zbyt wiele modyfikatorów virtual dla klasy podstawowej|
|C2508 błąd kompilatora|"*identyfikator*": "__declspec (*specifier1*)" nie można połączyć z "__declspec (*specifier2*)"|
|[Błąd kompilatora C2509](compiler-error-C2509.md)|"*identyfikator*": funkcja członkowska nie jest zadeklarowana w "*klasy*"|
|[Błąd kompilatora C2510](compiler-error-C2510.md)|"*identyfikator*": po lewej stronie "::" musi być klasy/struktury/Unii|
|[Błąd kompilatora C2511](compiler-error-C2511.md)|"*identyfikator*": przeciążona funkcja członkowska nie można odnaleźć w "*klasy*"|
|[Błąd kompilatora C2512](compiler-error-C2512.md)|"*identyfikator*": nie niedostępny odpowiedni konstruktor domyślny|
|[Błąd kompilatora C2513](compiler-error-C2513.md)|"* typu": Brak deklaracji zmiennej przed "="|
|[Błąd kompilatora C2514](compiler-error-C2514.md)|"*klasy*": klasa nie ma konstruktorów|
|C2515 błąd kompilatora|"*identyfikator*": "vtguard" można stosować do deklaracji lub definicji klasy|
|[Błąd kompilatora C2516](compiler-error-C2516.md)|"*klasy*": nie jest dozwoloną klasa podstawową|
|[Błąd kompilatora C2517](compiler-error-C2517.md)|"*identyfikator*": po prawej '::' jest niezdefiniowana|
|[Błąd kompilatora C2518](compiler-error-C2518.md)|słowo kluczowe "*— słowo kluczowe*" niedozwolony na liście klas podstawowych; zignorowane|
|C2519 błąd kompilatora|"*identyfikator*": atrybuty WinRT mogą zawierać tylko pola publiczne|
|C2520 błąd kompilatora|"*klasy*": nie niejawnego konstruktora dostępnego dla niejawnej konwersji|
|[Błąd kompilatora C2521](compiler-error-C2521.md)|destruktor/finalizator nie przyjmuje żadnych argumentów|
|C2522 błąd kompilatora|"*identyfikator*": przeciążony identyfikator nie można używać na "*identifier1*"jak zostało to już określone na"*identifier2*"|
|[Błąd kompilatora C2523](compiler-error-C2523.md)|"*klasy*:: ~*identyfikator*": niezgodność tagu destruktora/finalizatora|
|[Błąd kompilatora C2524](compiler-error-C2524.md)|"*identyfikator*": destruktor/finalizatora musi mieć listę parametrów "void"|
|C2525 błąd kompilatora|"*identyfikator*": parametr "*identifier1*ma nazwę*identifier2*" w podstawowym działać i musi pasować w opublikowanej implementacji|
|[Błąd kompilatora C2526](compiler-error-C2526.md)|"*identifier1*": funkcja powiązanie C nie może zwrócić klasę C++*identifier2*"|
|C2527 błąd kompilatora|"*identyfikator*": DefaultOverload nie można określić zarówno "*function1*"i"*function2*". Usunąć jedną specyfikację lub zmienić nazwę funkcji podczas implementacji|
|[Błąd kompilatora C2528](compiler-error-C2528.md)|"*identyfikator*": wskaźnik do odwołania jest niedozwolony|
|[Błąd kompilatora C2529](compiler-error-C2529.md)|"*identyfikator*": odwołanie do odwołania jest niedozwolony|
|[Błąd kompilatora C2530](compiler-error-C2530.md)|"*identyfikator*": odwołania muszą być zainicjowane|
|[Błąd kompilatora C2531](compiler-error-C2531.md)|"*identyfikator*": odwołanie do nieco pole jest niedozwolony|
|[Błąd kompilatora C2532](compiler-error-C2532.md)|"*identyfikator*": niedozwolony modyfikator dla odwołania|
|[Błąd kompilatora C2533](compiler-error-C2533.md)|"*identyfikator*": konstruktorom niedozwolony typ zwracany|
|[Błąd kompilatora C2534](compiler-error-C2534.md)|"*identyfikator*": Konstruktor nie może zwracać wartości|
|[Błąd kompilatora C2535](compiler-error-C2535.md)|"*identyfikator*": funkcja członkowska już zdefiniowana lub zadeklarowana|
|C2536 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2537](compiler-error-C2537.md)|"*specyfikator*": Niedozwolona specyfikacja powiązania|
|C2538 błąd kompilatora|Nieaktualne.|
|C2539 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2540](compiler-error-C2540.md)|niestałe wyrażenie jako granica tablicy|
|[Błąd kompilatora C2541](compiler-error-C2541.md)|"*identyfikator*": nie można usunąć obiektów, które nie są wskaźnikami|
|[Błąd kompilatora C2542](compiler-error-C2542.md)|"*identyfikator*": klasa obiektu nie ma konstruktora dla inicjowania|
|[Błąd kompilatora C2543](compiler-error-C2543.md)|Oczekiwano "]" operator '[']|
|[Błąd kompilatora C2544](compiler-error-C2544.md)|Oczekiwano ")" dla operatora "()"|
|[Błąd kompilatora C2545](compiler-error-C2545.md)|"*operator*": nie można odnaleźć przeciążonego operatora|
|C2546 błąd kompilatora|"*identyfikator*": kiedy typ jest zdefiniowany zarówno jako PIA i nie PIA PIA musi odwoływać się najpierw|
|C2547 błąd kompilatora|"*identyfikator*": wszystkie parametry opublikowanej metody muszę być jawnie nazwane w deklaracji|
|[Błąd kompilatora C2548](compiler-error-C2548.md)|"*funkcja*": Brak domyślnego parametru dla parametru *parametru*|
|[Błąd kompilatora C2549](compiler-error-C2549.md)|konwersja zdefiniowana przez użytkownika nie można określić zwracanego typu|
|[Błąd kompilatora C2550](compiler-error-C2550.md)|"*identyfikator*": listy inicjatorów konstruktora są dozwolone tylko dla definicji konstruktora|
|[Błąd kompilatora C2551](compiler-error-C2551.md)|"void *" typ wymaga jawnego rzutowania|
|[Błąd kompilatora C2552](compiler-error-C2552.md)|"*identyfikator*": niezagregowanych nie można zainicjować przy użyciu listy inicjatora|
|[Błąd kompilatora C2553](compiler-error-C2553.md)|"*typu* *derived_class*::*funkcja*": przesłanianie typu zwracanego funkcji wirtualnej różni się od "*typu* *base_ Klasa*::*funkcja*"|
|[Błąd kompilatora C2555](compiler-error-C2555.md)|"*derived_class*::*funkcja*": przesłanianie wirtualnej funkcji zwracany typ różni się i nie jest kowariantne z "*base_class*::*funkcja*'|
|[Błąd kompilatora C2556](compiler-error-C2556.md)|"*type1* *klasy*::*funkcja*": przeciążona funkcja różni się tylko typem zwracanym od "*type2* *—Klasa*::*funkcja*"|
|[Błąd kompilatora C2557](compiler-error-C2557.md)|"*identyfikator*": prywatnych i chronionych elementów członkowskich nie można zainicjować bez konstruktora|
|[Błąd kompilatora C2558](compiler-error-C2558.md)|klasy*klasy*": nie dostępnego konstruktora kopiującego lub Konstruktor kopiujący jest zadeklarowany jako"explicit"|
|C2559 błąd kompilatora|"*identyfikator*": nie można przeciążyć funkcji członkowskiej bez kwalifikatora ref funkcją członkowską z kwalifikatorem ref|
|C2560 błąd kompilatora|"*identyfikator*": nie można przeciążyć funkcji członkowskiej z kwalifikatorem ref funkcją członkowską bez kwalifikatora ref|
|[Błąd kompilatora C2561](compiler-error-C2561.md)|"*funkcja*": funkcja musi zwracać wartość|
|[Błąd kompilatora C2562](compiler-error-C2562.md)|"*funkcja*": "void" funkcji zwracającej wartość|
|[Błąd kompilatora C2563](compiler-error-C2563.md)|niezgodność w liście formalnych parametrów|
|C2564 błąd kompilatora|Nieaktualne.|
|C2565 błąd kompilatora|"*identyfikator*": Kwalifikator ref jest niedozwolony dla konstruktorów/destruktorów|
|[Błąd kompilatora C2566](compiler-error-C2566.md)|przeciążona funkcja w wyrażeniu warunkowym|
|[Błąd kompilatora C2567](compiler-error-C2567.md)|Nie można otworzyć metadanych w "*filename*", *possible_reason*|
|[Błąd kompilatora C2568](compiler-error-C2568.md)|"*identyfikator*": nie można rozpoznać przeciążenia funkcji|
|[Błąd kompilatora C2569](compiler-error-C2569.md)|"*identyfikator*": enum/union nie można użyć jako klasa podstawowa|
|[Błąd kompilatora C2570](compiler-error-C2570.md)|"*identyfikator*": union nie może mieć klas podstawowych|
|[Błąd kompilatora C2571](compiler-error-C2571.md)|"*identyfikator*": funkcja wirtualna nie może być w Unii "*Unii*"|
|[Błąd kompilatora C2572](compiler-error-C2572.md)|"*funkcja*": ponowna definicja domyślnego argumentu: parametr *numer*|
|[Błąd kompilatora C2573](compiler-error-C2573.md)|"*klasy*": nie można usunąć wskaźników do obiektów tego typu; klasa nie ma żadnych niezlokalizowanego przeciążenia dla "operator delete". Użyj:: Usuń lub Dodaj do klasy "operator delete(void*)"|
|[Błąd kompilatora C2574](compiler-error-C2574.md)|"*destruktora*": nie można zadeklarować jako statyczne|
|[Błąd kompilatora C2575](compiler-error-C2575.md)|"*identyfikator*": tylko funkcje Członkowskie i typy podstawowe mogą być wirtualne|
|C2576 błąd kompilatora|"*identyfikator*": nie można dodać nowej metody wirtualnej jako "public". Należy rozważyć zmianę metody na niewirtualną lub zmianę dostępności na "internal" lub "protected private"|
|[Błąd kompilatora C2577](compiler-error-C2577.md)|"*identyfikator*": destruktor/finalizator nie może mieć zwracanego typu|
|C2578 błąd kompilatora|"*klasy*": typ nie może mieć "protected" lub "protected public" — Konstruktor|
|[Błąd kompilatora C2579](compiler-error-C2579.md)|Nie można rozpoznać typu *typu* (*przesunięcie*). Oczekuje się w *filename*|
|C2580 błąd kompilatora|"*identyfikator*": wielu wersji domyślnych specjalnych funkcji Członkowskich są niedozwolone.|
|[Błąd kompilatora C2581](compiler-error-C2581.md)|"*typu*": statyczne "operator =" funkcji jest niedozwolone|
|[Błąd kompilatora C2582](compiler-error-C2582.md)|"operator *operator*"funkcja jest niedostępna w"*typu*"|
|[Błąd kompilatora C2583](compiler-error-C2583.md)|"*identyfikator*": "const/volatile" wskaźnik "this" jest niedozwolony dla konstruktorów/destruktorów|
|[Błąd kompilatora C2584](compiler-error-C2584.md)|"*klasy*": bezpośredniej klasy podstawowej "*base_class2*" jest niedostępna, już podstawowa dla "*base_class1*"|
|[Błąd kompilatora C2585](compiler-error-C2585.md)|Jawna konwersja na "*typu*" jest niejednoznaczny|
|[Błąd kompilatora C2586](compiler-error-C2586.md)|Składnia niepoprawne konwersji zdefiniowanej przez użytkownika: niedozwolone elementy pośrednie|
|[Błąd kompilatora C2587](compiler-error-C2587.md)|"*identyfikator*": niedozwolone użycie lokalnej zmiennej jako parametru domyślnego|
|[Błąd kompilatora C2588](compiler-error-C2588.md)|":: ~*identyfikator*": niedozwolony globalny destruktora/finalizatora|
|[Błąd kompilatora C2589](compiler-error-C2589.md)|"*identyfikator*": niedozwolony token po prawej stronie "::"|
|C2590 błąd kompilatora|"*identyfikator*": tylko Konstruktor może mieć podstawowej/członkowskiej liście inicjatorów|
|C2591 błąd kompilatora|ExclusiveTo nie może użyć "*typu*" jako argumentu. Tylko "ref class" jest prawidłowym argumentem|
|[Błąd kompilatora C2592](compiler-error-C2592.md)|"*klasy*": "*base_class2*"jest odziedziczone"*base_class1*" i nie może być ponownie określone|
|[Błąd kompilatora C2593](compiler-error-C2593.md)|"operator *identyfikator*" jest niejednoznaczny|
|[Błąd kompilatora C2594](compiler-error-C2594.md)|"*operator*": Niejednoznaczne konwersje z "*type1*"do"*type2*"|
|C2595 błąd kompilatora|"*identyfikator*" typ atrybutu WinRT musi być zapieczętowane|
|C2596 błąd kompilatora|"*identyfikator*" pole atrybutu WinRT może być tylko "public enum class", "int", "unsigned int", "bool", "Platform::Type", "Platform::String" lub "Windows Windows::Foundation:: HResult"|
|[Błąd kompilatora C2597](compiler-error-C2597.md)|niedozwolone odwołanie do niestatycznego elementu członkowskiego "*identyfikator*"|
|[Błąd kompilatora C2598](compiler-error-C2598.md)|Specyfikacja konsolidacji musi znajdować się w zakresie globalnym|
|[Błąd kompilatora C2599](compiler-error-C2599.md)|"*identyfikator*": deklaracja przekazująca dalej wyliczenie managed WinRT nie jest dozwolone.|  