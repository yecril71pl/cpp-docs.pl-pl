---
title: Błędy kompilatora — od C2500 do C2599
ms.date: 04/21/2019
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
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
ms.openlocfilehash: 87728c2d7055715b7e7d986d5ab8792ceba5c450
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857081"
---
# <a name="compiler-errors-c2500-through-c2599"></a>Błędy kompilatora — od C2500 do C2599

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Message|
|-----------|-------------|
|[Błąd kompilatora od C2500](compiler-error-C2500.md)|"*identifier1*": "*identifier2*" jest już bezpośrednią klasą bazową|
|Błąd kompilatora C2501|"*identyfikator*": "__declspec (*specyfikator*)" może być stosowane tylko do struktur, Unii, klas lub składowych pól bitowych unsigned|
|[Błąd kompilatora C2502](compiler-error-C2502.md)|"*identyfikator*": zbyt wiele modyfikatorów dostępu dla klasy bazowej|
|[Błąd kompilatora C2503](compiler-error-C2503.md)|"*klasy*": klasy bazowe nie mogą zawierać tablic o rozmiarze zerowym|
|[Błąd kompilatora C2504](compiler-error-C2504.md)|"*klasy*": klasa bazowa niezdefiniowana|
|[Błąd kompilatora C2505](compiler-error-C2505.md)|"*symbol*": "__declspec (*specyfikator*)" może być stosowane tylko do deklaracji lub definicji obiektów globalnych albo statycznych składowych danych|
|[Błąd kompilatora C2506](compiler-error-C2506.md)|"*elementu członkowskiego*": "__declspec (*specyfikator*)" nie można zastosować do tego symbolu|
|[Błąd kompilatora C2507](compiler-error-C2507.md)|"*identyfikator*": zbyt wiele modyfikatorów virtual dla klasy bazowej|
|Błąd kompilatora C2508|"*identyfikator*": "__declspec (*specifier1*)" nie można połączyć z "__declspec (*specifier2*)"|
|[Compiler error C2509](compiler-error-C2509.md)|"*identyfikator*": funkcja składowa nie jest zadeklarowana w "*klasy*"|
|[Błąd kompilatora C2510](compiler-error-C2510.md)|"*identyfikator*": po lewej stronie "::" musi być klasy/struct/union|
|[Compiler error C2511](compiler-error-C2511.md)|"*identyfikator*": przeciążona funkcja składowa nie znaleziono w "*klasy*"|
|[Błąd kompilatora C2512](compiler-error-C2512.md)|"*identyfikator*": nie niedostępny odpowiedni konstruktor domyślny|
|[Błąd kompilatora C2513](compiler-error-C2513.md)|"* typu": Brak deklaracji zmiennej przed "="|
|[Błąd kompilatora C2514](compiler-error-C2514.md)|"*klasy*": klasa nie ma konstruktorów|
|Błąd kompilatora C2515|"*identyfikator*": "vtguard" może być stosowane tylko do deklaracji lub definicji klasy|
|[Błąd kompilatora C2516](compiler-error-C2516.md)|"*klasy*": nie jest dozwoloną klasa bazową|
|[Błąd kompilatora C2517](compiler-error-C2517.md)|"*identyfikator*": po prawej stronie "::" jest niezdefiniowana|
|[Compiler error C2518](compiler-error-C2518.md)|słowo kluczowe "*— słowo kluczowe*" niedozwolony na liście klas bazowych; zignorowane|
|Błąd kompilatora C2519|"*identyfikator*": Atrybuty WinRT mogą zawierać tylko pola publiczne|
|Błąd kompilatora C2520|"*klasy*": Brak niejawnego konstruktora dostępnego dla niejawnej konwersji|
|[Błąd kompilatora C2521](compiler-error-C2521.md)|destruktor/finalizator nie przyjmuje żadnych argumentów|
|Błąd kompilatora C2522|"*identyfikator*": Przeciążony identyfikator nie pozwala na "*identifier1*"ponieważ jest już określony w"*identifier2*"|
|[Błąd kompilatora C2523](compiler-error-C2523.md)|"*klasy*:: ~*identyfikator*": niezgodność tagu destruktor/finalizatora|
|[Błąd kompilatora C2524](compiler-error-C2524.md)|"*identyfikator*": destruktor/finalizator musi mieć listę parametrów "void"|
|Błąd kompilatora C2525|"*identyfikator*": Parametr "*identifier1*ma nazwę*identifier2*" na podstawie funkcji i musi pasować w opublikowanej implementacji|
|[Compiler error C2526](compiler-error-C2526.md)|"*identifier1*": Powiązanie z funkcją języka C nie można zwrócić C++ klasy*identifier2*"|
|Błąd kompilatora C2527|"*identyfikator*": DefaultOverload nie można określić zarówno "*function1*"i"*function2*". Usunąć jedną specyfikację lub zmienić nazwę funkcji podczas implementacji|
|[Błąd kompilatora C2528](compiler-error-C2528.md)|"*identyfikator*": wskaźnik do odwołania jest niedozwolone|
|[Błąd kompilatora C2529](compiler-error-C2529.md)|"*identyfikator*": odwołanie do odwołania jest niedozwolone|
|[Błąd kompilatora C2530](compiler-error-C2530.md)|"*identyfikator*": odwołania muszą być zainicjowane|
|[Błąd kompilatora C2531](compiler-error-C2531.md)|"*identyfikator*": odwołanie do nieco pola jest niedozwolony|
|[Błąd kompilatora C2532](compiler-error-C2532.md)|"*identyfikator*": niedozwolony modyfikator dla odwołania|
|[Błąd kompilatora C2533](compiler-error-C2533.md)|"*identyfikator*": konstruktorom niedozwolony typ zwracany|
|[Błąd kompilatora C2534](compiler-error-C2534.md)|"*identyfikator*": Konstruktor nie może zwracać wartości|
|[Błąd kompilatora C2535](compiler-error-C2535.md)|"*identyfikator*": funkcja składowa już zdefiniowana lub zadeklarowana|
|Błąd kompilatora C2536|Nieaktualne.|
|[Błąd kompilatora C2537](compiler-error-C2537.md)|"*specyfikator*": Niedozwolona specyfikacja powiązania|
|Błąd kompilatora C2538|Nieaktualne.|
|Błąd kompilatora C2539|Nieaktualne.|
|[Błąd kompilatora C2540](compiler-error-C2540.md)|niestałe wyrażenie jako granica tablicy|
|[Błąd kompilatora C2541](compiler-error-C2541.md)|"*identyfikator*": nie można usunąć obiektów, które nie są wskaźnikami|
|[Błąd kompilatora C2542](compiler-error-C2542.md)|"*identyfikator*": obiekt klasy nie ma konstruktora by inicjowania|
|[Błąd kompilatora C2543](compiler-error-C2543.md)|Oczekiwano "]" dla operatora "[]"|
|[Błąd kompilatora C2544](compiler-error-C2544.md)|Oczekiwano ")" dla operatora "()"|
|[Błąd kompilatora C2545](compiler-error-C2545.md)|"*operator*": nie można odnaleźć przeciążonego operatora|
|Compiler error C2546|"*identyfikator*": kiedy typ jest zdefiniowany w zarówno jako PIA i nie PIA PIA musi odwoływać się najpierw|
|Błąd kompilatora C2547|"*identyfikator*": Wszystkie parametry opublikowanej metody muszę być jawnie nazwane w deklaracji|
|[Compiler error C2548](compiler-error-C2548.md)|"*funkcja*": Brak domyślnego parametru dla parametru *parametru*|
|[Compiler error C2549](compiler-error-C2549.md)|konwersja zdefiniowana przez użytkownika nie może określić zwracanego typu|
|[Błąd kompilatora C2550](compiler-error-C2550.md)|"*identyfikator*": listy inicjatorów konstruktora są dozwolone tylko dla definicji konstruktora|
|[Compiler error C2551](compiler-error-C2551.md)|"void *" typ wymaga jawnego rzutowania|
|[Błąd kompilatora C2552](compiler-error-C2552.md)|"*identyfikator*": obiektów niebędących agregacjami nie można zainicjować z listy inicjalizatora|
|[Błąd kompilatora C2553](compiler-error-C2553.md)|"*typu* *derived_class*::*funkcja*": przesłanianie zwracany typ funkcji wirtualnej różni się od "*typu* *base_ Klasa*::*funkcja*"|
|[Błąd kompilatora C2555](compiler-error-C2555.md)|"*derived_class*::*funkcja*": przesłanianie wirtualnej funkcji zwracanego typu różni się i nie jest kowariantne z "*element $base_class*::*funkcja*'|
|[Compiler error C2556](compiler-error-C2556.md)|"*type1* *klasy*::*funkcja*": przeciążona funkcja różni się tylko typ zwracany z "*type2* *klasy*::*funkcja*"|
|[Błąd kompilatora C2557](compiler-error-C2557.md)|"*identyfikator*": prywatnych i chronionych składowych nie można zainicjować bez konstruktora|
|[Compiler error C2558](compiler-error-C2558.md)|klasy*klasy*": nie dostępnego konstruktora kopiującego lub Konstruktor kopiujący jest zadeklarowany jako"explicit"|
|Błąd kompilatora C2559|"*identyfikator*": nie można przeciążyć funkcji składowej bez kwalifikatora ref funkcją składową z kwalifikatorem ref|
|Błąd kompilatora C2560|"*identyfikator*": nie można przeciążyć funkcji składowej z kwalifikatorem ref funkcją składową bez kwalifikatora ref|
|[Błąd kompilatora C2561](compiler-error-C2561.md)|"*funkcja*": funkcja musi zwracać wartość|
|[Błąd kompilatora C2562](compiler-error-C2562.md)|"*funkcja*": funkcja "void" zwraca wartość|
|[Błąd kompilatora C2563](compiler-error-C2563.md)|niezgodność w liście formalnych parametrów|
|Błąd kompilatora C2564|Nieaktualne.|
|Błąd kompilatora C2565|"*identyfikator*": Kwalifikator ref jest niedozwolony dla konstruktorów/destruktorów|
|[Compiler error C2566](compiler-error-C2566.md)|przeciążona funkcja w wyrażeniu warunkowym|
|[Błąd kompilatora C2567](compiler-error-C2567.md)|Nie można otworzyć metadanych w "*filename*", *possible_reason*|
|[Compiler error C2568](compiler-error-C2568.md)|"*identyfikator*": nie można rozpoznać przeciążenia funkcji|
|[Compiler error C2569](compiler-error-C2569.md)|"*identyfikator*": wyliczenia/Unii nie można użyć jako klasa bazowa|
|[Błąd kompilatora C2570](compiler-error-C2570.md)|"*identyfikator*": Unia nie może mieć klas bazowych|
|[Błąd kompilatora C2571](compiler-error-C2571.md)|"*identyfikator*": funkcja wirtualna nie może być w Unii "*Unii*"|
|[Błąd kompilatora C2572](compiler-error-C2572.md)|"*funkcja*": ponowna definicja domyślnego argumentu: parametr *numer*|
|[Błąd kompilatora C2573](compiler-error-C2573.md)|"*klasy*": nie można usunąć wskaźników do obiektów tego typu; klasa nie ma żadnych niezlokalizowanego przeciążenia dla "operator delete". Użyj:: Usuń lub Dodaj "operator delete(void*)""do klasy|
|[Błąd kompilatora C2574](compiler-error-C2574.md)|"*destruktor*": nie może być zadeklarowane jako statyczne|
|[Błąd kompilatora C2575](compiler-error-C2575.md)|"*identyfikator*": tylko do elementów członkowskich i typy bazowe mogą być wirtualne|
|Błąd kompilatora C2576|"*identyfikator*": nie można przedstawić metody wirtualnej jako "public". Należy rozważyć zmianę metody na niewirtualną lub zmienić dostępności na "internal" lub "protected private"|
|[Błąd kompilatora C2577](compiler-error-C2577.md)|"*identyfikator*": destruktor/finalizator nie może posiadać typu zwracanego|
|Błąd kompilatora C2578|"*klasy*": typ nie może mieć "protected" lub "protected public" Konstruktor|
|[Compiler error C2579](compiler-error-C2579.md)|Nie można rozpoznać typu *typu* (*przesunięcie*). Oczekuje się w *nazwy pliku*|
|Błąd kompilatora C2580|"*identyfikator*": wiele wersji domyślnych specjalnych funkcji składowych nie są dozwolone.|
|[Compiler error C2581](compiler-error-C2581.md)|"*typu*": statyczne "operator =" funkcji jest niedozwolone|
|[Compiler error C2582](compiler-error-C2582.md)|"operator *operator*"funkcja jest niedostępna w"*typu*"|
|[Błąd kompilatora C2583](compiler-error-C2583.md)|"*identyfikator*": "const/volatile" wskaźnik "this" jest niedozwolony dla konstruktorów/destruktorów|
|[Compiler error C2584](compiler-error-C2584.md)|"*klasy*": bezpośredniej klasy podstawowej '*base_class2*"jest niedostępny; już baza dla"*base_class1*"|
|[Błąd kompilatora C2585](compiler-error-C2585.md)|Jawna konwersja na "*typu*" jest niejednoznaczny|
|[Compiler error C2586](compiler-error-C2586.md)|Składnia Nieprawidłowa konwersja zdefiniowana przez użytkownika: niedozwolone elementy pośrednie|
|[Błąd kompilatora C2587](compiler-error-C2587.md)|"*identyfikator*": niedozwolone użycie lokalnej zmiennej jako parametru domyślnego|
|[Błąd kompilatora C2588](compiler-error-C2588.md)|":: ~*identyfikator*": niedozwolony globalny destruktor/finalizatora|
|[Compiler error C2589](compiler-error-C2589.md)|"*identyfikator*": niedozwolony token po prawej stronie "::"|
|Błąd kompilatora C2590|"*identyfikator*": tylko Konstruktor może mieć listy inicjatorów bazowych/składowych|
|Błąd kompilatora C2591|ExclusiveTo nie może użyć "*typu*" jako argumentu. Tylko "ref class" jest prawidłowym argumentem|
|[Błąd kompilatora C2592](compiler-error-C2592.md)|"*klasy*": "*base_class2*"jest odziedziczone po"*base_class1*" i nie może być ponownie określone|
|[Błąd kompilatora C2593](compiler-error-C2593.md)|"operator *identyfikator*" jest niejednoznaczny|
|[Błąd kompilatora C2594](compiler-error-C2594.md)|"*operator*": Niejednoznaczne konwersje z "*type1*"to"*type2*"|
|Błąd kompilatora C2595|"*identyfikator*" typ atrybutu WinRT musi być zapieczętowany.|
|Compiler error C2596|"*identyfikator*" pole atrybutu WinRT może być tylko "public enum class", "int", "unsigned int", "bool", "Platform::Type", "Platform::String" lub "Windows Windows::Foundation:: HResult"|
|[Błąd kompilatora C2597](compiler-error-C2597.md)|niedozwolone odwołanie do niestatycznej składowej "*identyfikator*"|
|[Błąd kompilatora C2598](compiler-error-C2598.md)|Specyfikacja konsolidacji musi znajdować się w zakresie globalnym|
|[Błąd kompilatora C2599](compiler-error-C2599.md)|"*identyfikator*": deklaracja wyliczenia zarządzane WinRT nie jest dozwolone.|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
