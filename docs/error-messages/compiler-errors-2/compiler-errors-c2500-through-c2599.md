---
title: "C2500 błędy kompilatora za pośrednictwem C2599 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
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
dev_langs: C++
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e66a789de4a1b5cfd64ff73f6dbecd4e85bfdffd
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-errors-c2500-through-c2599"></a>C2500 błędy kompilatora za pośrednictwem C2599
Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.  
  
> [!NOTE]
>  Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).  
  
|Błąd|Komunikat|  
|-----------|-------------|  
|[C2500 błąd kompilatora](compiler-error-C2500.md)|"*identifier1*": "*identifier2*" jest już bezpośredniej klasie podstawowej|  
|C2501 błąd kompilatora|"*identyfikator*": "__declspec (*specyfikator*)" można stosować do struktur, związków, klas lub członków pól bitowych unsigned|  
|[C2502 błąd kompilatora](compiler-error-C2502.md)|"*identyfikator*": zbyt wiele modyfikatorów dostępu dla klasy podstawowej|  
|[C2503 błąd kompilatora](compiler-error-C2503.md)|"*klasy*": klasy podstawowej nie mogą zawierać tablic o rozmiarze zero|  
|[C2504 błąd kompilatora](compiler-error-C2504.md)|"*klasy*": klasa podstawowa niezdefiniowana|  
|[C2505 błąd kompilatora](compiler-error-C2505.md)|"*symbol*": "__declspec (*specyfikator*)" można stosować do deklaracji lub definicji obiektów globalnych lub statyczne elementy członkowskie danych|  
|[C2506 błąd kompilatora](compiler-error-C2506.md)|"*elementu członkowskiego*": "__declspec (*specyfikator*)" nie można zastosować do tego symbolu|  
|[C2507 błąd kompilatora](compiler-error-C2507.md)|"*identyfikator*": zbyt wiele modyfikatorów virtual dla klasy podstawowej|  
|C2508 błąd kompilatora|"*identyfikator*": "__declspec (*specifier1*)" nie można połączyć z "__declspec (*specifier2*)"|  
|[C2509 błąd kompilatora](compiler-error-C2509.md)|"*identyfikator*": funkcja członkowska nie jest zadeklarowana w "*klasy*"|  
|[C2510 błąd kompilatora](compiler-error-C2510.md)|"*identyfikator*": po lewej stronie "::" musi być klasy/struktury/Unii|  
|[C2511 błąd kompilatora](compiler-error-C2511.md)|"*identyfikator*": przeciążona funkcja członkowska nie można odnaleźć w "*klasy*"|  
|[C2512 błąd kompilatora](compiler-error-C2512.md)|"*identyfikator*": nie niedostępny odpowiedni konstruktor domyślny|  
|[C2513 błąd kompilatora](compiler-error-C2513.md)|"* typu": Brak deklaracji zmiennej przed "="|  
|[C2514 błąd kompilatora](compiler-error-C2514.md)|"*klasy*": klasa nie ma konstruktorów|  
|C2515 błąd kompilatora|"*identyfikator*": "vtguard" można stosować do deklaracji lub definicji klasy|  
|[C2516 błąd kompilatora](compiler-error-C2516.md)|"*klasy*": nie jest dozwoloną klasa podstawową|  
|[C2517 błąd kompilatora](compiler-error-C2517.md)|"*identyfikator*": po prawej '::' jest niezdefiniowana|  
|[C2518 błąd kompilatora](compiler-error-C2518.md)|słowo kluczowe "*— słowo kluczowe*" niedozwolony na liście klas podstawowych; zignorowane|  
|C2519 błąd kompilatora|"*identyfikator*": atrybuty WinRT mogą zawierać tylko pola publiczne|  
|C2520 błąd kompilatora|"*klasy*": nie niejawnego konstruktora dostępnego dla niejawnej konwersji|  
|[C2521 błąd kompilatora](compiler-error-C2521.md)|destruktor/finalizator nie przyjmuje żadnych argumentów|  
|C2522 błąd kompilatora|"*identyfikator*": przeciążony identyfikator nie można używać na "*identifier1*"jak zostało to już określone na"*identifier2*"|  
|[C2523 błąd kompilatora](compiler-error-C2523.md)|"*klasy*:: ~*identyfikator*": niezgodność tagu destruktora/finalizatora|  
|[C2524 błąd kompilatora](compiler-error-C2524.md)|"*identyfikator*": destruktor/finalizatora musi mieć listę parametrów "void"|  
|C2525 błąd kompilatora|"*identyfikator*": parametr "*identifier1*ma nazwę*identifier2*" w podstawowym działać i musi pasować w opublikowanej implementacji|  
|[C2526 błąd kompilatora](compiler-error-C2526.md)|"*identifier1*": funkcja powiązanie C nie może zwrócić klasę C++*identifier2*"|  
|C2527 błąd kompilatora|"*identyfikator*": DefaultOverload nie można określić zarówno "*function1*"i"*function2*". Usunąć jedną specyfikację lub zmienić nazwę funkcji podczas implementacji|  
|[C2528 błąd kompilatora](compiler-error-C2528.md)|"*identyfikator*": wskaźnik do odwołania jest niedozwolony|  
|[C2529 błąd kompilatora](compiler-error-C2529.md)|"*identyfikator*": odwołanie do odwołania jest niedozwolony|  
|[C2530 błąd kompilatora](compiler-error-C2530.md)|"*identyfikator*": odwołania muszą być zainicjowane|  
|[C2531 błąd kompilatora](compiler-error-C2531.md)|"*identyfikator*": odwołanie do nieco pole jest niedozwolony|  
|[C2532 błąd kompilatora](compiler-error-C2532.md)|"*identyfikator*": niedozwolony modyfikator dla odwołania|  
|[C2533 błąd kompilatora](compiler-error-C2533.md)|"*identyfikator*": konstruktorom niedozwolony typ zwracany|  
|[C2534 błąd kompilatora](compiler-error-C2534.md)|"*identyfikator*": Konstruktor nie może zwracać wartości|  
|[C2535 błąd kompilatora](compiler-error-C2535.md)|"*identyfikator*": funkcja członkowska już zdefiniowana lub zadeklarowana|  
|C2536 błąd kompilatora|Nieaktualne.|  
|[C2537 błąd kompilatora](compiler-error-C2537.md)|"*specyfikator*": Niedozwolona specyfikacja powiązania|  
|C2538 błąd kompilatora|Nieaktualne.|  
|C2539 błąd kompilatora|Nieaktualne.|
|[C2540 błąd kompilatora](compiler-error-C2540.md)|niestałe wyrażenie jako granica tablicy|  
|[C2541 błąd kompilatora](compiler-error-C2541.md)|"*identyfikator*": nie można usunąć obiektów, które nie są wskaźnikami|  
|[C2542 błąd kompilatora](compiler-error-C2542.md)|"*identyfikator*": klasa obiektu nie ma konstruktora dla inicjowania|  
|[C2543 błąd kompilatora](compiler-error-C2543.md)|Oczekiwano "]" operator '[']|  
|[C2544 błąd kompilatora](compiler-error-C2544.md)|Oczekiwano ")" dla operatora "()"|  
|[C2545 błąd kompilatora](compiler-error-C2545.md)|"*operator*": nie można odnaleźć przeciążonego operatora|  
|C2546 błąd kompilatora|"*identyfikator*": kiedy typ jest zdefiniowany zarówno jako PIA i nie PIA PIA musi odwoływać się najpierw|  
|C2547 błąd kompilatora|"*identyfikator*": wszystkie parametry opublikowanej metody muszę być jawnie nazwane w deklaracji|  
|[C2548 błąd kompilatora](compiler-error-C2548.md)|"*funkcja*": Brak domyślnego parametru dla parametru *parametru*|  
|[C2549 błąd kompilatora](compiler-error-C2549.md)|konwersja zdefiniowana przez użytkownika nie można określić zwracanego typu|  
|[C2550 błąd kompilatora](compiler-error-C2550.md)|"*identyfikator*": listy inicjatorów konstruktora są dozwolone tylko dla definicji konstruktora|  
|[C2551 błąd kompilatora](compiler-error-C2551.md)|"void *" typ wymaga jawnego rzutowania|  
|[C2552 błąd kompilatora](compiler-error-C2552.md)|"*identyfikator*": niezagregowanych nie można zainicjować przy użyciu listy inicjatora|  
|[C2553 błąd kompilatora](compiler-error-C2553.md)|"*typu* *derived_class*::*funkcja*": przesłanianie typu zwracanego funkcji wirtualnej różni się od "*typu* *base_ Klasa*::*funkcja*"|  
|[C2555 błąd kompilatora](compiler-error-C2555.md)|"*derived_class*::*funkcja*": przesłanianie wirtualnej funkcji zwracany typ różni się i nie jest kowariantne z "*base_class*::*funkcja*'|  
|[C2556 błąd kompilatora](compiler-error-C2556.md)|"*type1* *klasy*::*funkcja*": przeciążona funkcja różni się tylko typem zwracanym od "*type2* *—Klasa*::*funkcja*"|  
|[C2557 błąd kompilatora](compiler-error-C2557.md)|"*identyfikator*": prywatnych i chronionych elementów członkowskich nie można zainicjować bez konstruktora|  
|[C2558 błąd kompilatora](compiler-error-C2558.md)|klasy*klasy*": nie dostępnego konstruktora kopiującego lub Konstruktor kopiujący jest zadeklarowany jako"explicit"|  
|C2559 błąd kompilatora|"*identyfikator*": nie można przeciążyć funkcji członkowskiej bez kwalifikatora ref funkcją członkowską z kwalifikatorem ref|  
|C2560 błąd kompilatora|"*identyfikator*": nie można przeciążyć funkcji członkowskiej z kwalifikatorem ref funkcją członkowską bez kwalifikatora ref|  
|[C2561 błąd kompilatora](compiler-error-C2561.md)|"*funkcja*": funkcja musi zwracać wartość|  
|[C2562 błąd kompilatora](compiler-error-C2562.md)|"*funkcja*": "void" funkcji zwracającej wartość|  
|[C2563 błąd kompilatora](compiler-error-C2563.md)|niezgodność w liście formalnych parametrów|  
|C2564 błąd kompilatora|Nieaktualne.|  
|C2565 błąd kompilatora|"*identyfikator*": Kwalifikator ref jest niedozwolony dla konstruktorów/destruktorów|  
|[C2566 błąd kompilatora](compiler-error-C2566.md)|przeciążona funkcja w wyrażeniu warunkowym|  
|[C2567 błąd kompilatora](compiler-error-C2567.md)|Nie można otworzyć metadanych w "*filename*", *possible_reason*|  
|[C2568 błąd kompilatora](compiler-error-C2568.md)|"*identyfikator*": nie można rozpoznać przeciążenia funkcji|  
|[C2569 błąd kompilatora](compiler-error-C2569.md)|"*identyfikator*": enum/union nie można użyć jako klasa podstawowa|  
|[C2570 błąd kompilatora](compiler-error-C2570.md)|"*identyfikator*": union nie może mieć klas podstawowych|  
|[C2571 błąd kompilatora](compiler-error-C2571.md)|"*identyfikator*": funkcja wirtualna nie może być w Unii "*Unii*"|  
|[C2572 błąd kompilatora](compiler-error-C2572.md)|"*funkcja*": ponowna definicja domyślnego argumentu: parametr *numer*|  
|[C2573 błąd kompilatora](compiler-error-C2573.md)|"*klasy*": nie można usunąć wskaźników do obiektów tego typu; klasa nie ma żadnych niezlokalizowanego przeciążenia dla "operator delete". Użyj:: Usuń lub Dodaj do klasy "operator delete(void*)"|  
|[C2574 błąd kompilatora](compiler-error-C2574.md)|"*destruktora*": nie można zadeklarować jako statyczne|  
|[C2575 błąd kompilatora](compiler-error-C2575.md)|"*identyfikator*": tylko funkcje Członkowskie i typy podstawowe mogą być wirtualne|  
|C2576 błąd kompilatora|"*identyfikator*": nie można dodać nowej metody wirtualnej jako "public". Należy rozważyć zmianę metody na niewirtualną lub zmianę dostępności na "internal" lub "protected private"|  
|[C2577 błąd kompilatora](compiler-error-C2577.md)|"*identyfikator*": destruktor/finalizator nie może mieć zwracanego typu|  
|C2578 błąd kompilatora|"*klasy*": typ nie może mieć "protected" lub "protected public" — Konstruktor|  
|[C2579 błąd kompilatora](compiler-error-C2579.md)|Nie można rozpoznać typu *typu* (*przesunięcie*). Oczekuje się w *filename*|  
|C2580 błąd kompilatora|"*identyfikator*": wielu wersji domyślnych specjalnych funkcji Członkowskich są niedozwolone.|  
|[C2581 błąd kompilatora](compiler-error-C2581.md)|"*typu*": statyczne "operator =" funkcji jest niedozwolone|  
|[C2582 błąd kompilatora](compiler-error-C2582.md)|"operator *operator*"funkcja jest niedostępna w"*typu*"|  
|[C2583 błąd kompilatora](compiler-error-C2583.md)|"*identyfikator*": "const/volatile" wskaźnik "this" jest niedozwolony dla konstruktorów/destruktorów|  
|[C2584 błąd kompilatora](compiler-error-C2584.md)|"*klasy*": bezpośredniej klasy podstawowej "*base_class2*" jest niedostępna, już podstawowa dla "*base_class1*"|  
|[C2585 błąd kompilatora](compiler-error-C2585.md)|Jawna konwersja na "*typu*" jest niejednoznaczny|  
|[C2586 błąd kompilatora](compiler-error-C2586.md)|Składnia niepoprawne konwersji zdefiniowanej przez użytkownika: niedozwolone elementy pośrednie|  
|[C2587 błąd kompilatora](compiler-error-C2587.md)|"*identyfikator*": niedozwolone użycie lokalnej zmiennej jako parametru domyślnego|  
|[C2588 błąd kompilatora](compiler-error-C2588.md)|":: ~*identyfikator*": niedozwolony globalny destruktora/finalizatora|  
|[C2589 błąd kompilatora](compiler-error-C2589.md)|"*identyfikator*": niedozwolony token po prawej stronie "::"|  
|C2590 błąd kompilatora|"*identyfikator*": tylko Konstruktor może mieć podstawowej/członkowskiej liście inicjatorów|  
|C2591 błąd kompilatora|ExclusiveTo nie może użyć "*typu*" jako argumentu. Tylko "ref class" jest prawidłowym argumentem|  
|[C2592 błąd kompilatora](compiler-error-C2592.md)|"*klasy*": "*base_class2*"jest odziedziczone"*base_class1*" i nie może być ponownie określone|  
|[C2593 błąd kompilatora](compiler-error-C2593.md)|"operator *identyfikator*" jest niejednoznaczny|  
|[C2594 błąd kompilatora](compiler-error-C2594.md)|"*operator*": Niejednoznaczne konwersje z "*type1*"do"*type2*"|  
|C2595 błąd kompilatora|"*identyfikator*" typ atrybutu WinRT musi być zapieczętowane|  
|C2596 błąd kompilatora|"*identyfikator*" pole atrybutu WinRT może być tylko "public enum class", "int", "unsigned int", "bool", "Platform::Type", "Platform::String" lub "Windows Windows::Foundation:: HResult"|  
|[C2597 błąd kompilatora](compiler-error-C2597.md)|niedozwolone odwołanie do niestatycznego elementu członkowskiego "*identyfikator*"|  
|[C2598 błąd kompilatora](compiler-error-C2598.md)|Specyfikacja konsolidacji musi znajdować się w zakresie globalnym|  
|[C2599 błąd kompilatora](compiler-error-C2599.md)|"*identyfikator*": deklaracja przekazująca dalej wyliczenie managed WinRT nie jest dozwolone.|  