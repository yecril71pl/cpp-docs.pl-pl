---
title: Błędy kompilatora — od C2700 do C2799
ms.date: 04/21/2019
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
ms.openlocfilehash: 174f6a9c8ec9e44deadfca090ba492cb32d53e9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197517"
---
# <a name="compiler-errors-c2700-through-c2799"></a>Błędy kompilatora — od C2700 do C2799

W artykułach w tej sekcji dokumentacji wyjaśniono podzestaw komunikatów o błędach generowanych przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Wiadomość|
|-----------|-------------|
|[Błąd kompilatora C2700](compiler-error-c2700.md)|"*Type*": nie można wyrzucać (Użyj/W4, aby uzyskać więcej informacji)|
|[Błąd kompilatora C2701](compiler-error-c2701.md)|"*Function*": szablon funkcji/generyczna nie może być zaprzyjaźniona z lokalną klasą|
|[Błąd kompilatora C2702](compiler-error-c2702.md)| __except mogą nie występować w bloku zakończenia|
|[Błąd kompilatora C2703](compiler-error-c2703.md)|Niedozwolona instrukcja __leave|
|[Błąd kompilatora C2704](compiler-error-c2704.md)|"*Function*": __va_start wewnętrzna dozwolona tylko w elemencie VarArgs|
|[Błąd kompilatora C2705](compiler-error-c2705.md)|"*Label*": niedozwolony skok do zakresu "*exception_block*"|
|[Błąd kompilatora C2706](compiler-error-c2706.md)|niedozwolone __except bez pasujących __try (brak "}" w bloku __try?)|
|[Błąd kompilatora C2707](compiler-error-c2707.md)|"*Identyfikator*": zły kontekst dla funkcji wewnętrznej|
|[Błąd kompilatora C2708](compiler-error-c2708.md)|"*Identyfikator*": rzeczywiste parametry długości w bajtach różnią się od poprzedniego wywołania lub odwołania|
|[Błąd kompilatora C2709](compiler-error-c2709.md)|"*Identyfikator*": długość parametrów formalnych w bajtach różni się od poprzedniej deklaracji|
|[Błąd kompilatora C2710](compiler-error-c2710.md)|"*Identyfikator*": "__declspec (*modyfikator*)" można stosować tylko do funkcji zwracającej wskaźnik|
|[Błąd kompilatora C2711](compiler-error-c2711.md)|"*Function*": Ta funkcja nie może być skompilowana jako zarządzana, rozważ użycie #pragma niezarządzane|
|[Błąd kompilatora C2712](compiler-error-c2712.md)|Nie można użyć __try w funkcjach, które wymagają odwinięcia obiektu|
|[Błąd kompilatora C2713](compiler-error-c2713.md)|Tylko jeden formularz obsługi wyjątków dozwolony dla funkcji|
|[Błąd kompilatora C2714](compiler-error-c2714.md)| `alignof(void)`nie jest dozwolone|
|[Błąd kompilatora C2715](compiler-error-c2715.md)|"*Type*": nie można zgłosić lub przechwycić tego typu|
|Błąd kompilatora C2716|Nieaktualne.|
|Błąd kompilatora C2717|Nieaktualne.|
|[Błąd kompilatora C2718](compiler-error-c2718.md)|"*Type*": rzeczywisty parametr z żądanym wyrównaniem *liczby* nie będzie wyrównany|
|[Błąd kompilatora C2719](compiler-error-c2719.md)|"*Parameter*": formalny parametr z żądanym wyrównaniem *liczby* nie będzie wyrównany|
|[Błąd kompilatora C2720](compiler-error-c2720.md)|"*Identyfikator*": specyfikator klasy magazynu "*specyfikator*" jest niedozwolony w składowych|
|[Błąd kompilatora C2721](compiler-error-c2721.md)|"*specyfikator*": specyfikator klasy magazynu jest niedozwolony między słowem kluczowym operatora i typem|
|[Błąd kompilatora C2722](compiler-error-c2722.md)|"::*operator*": niedozwolone polecenie po operatorze; Użyj " *operator*operatora"|
|[Błąd kompilatora C2723](compiler-error-c2723.md)|"*Function*": specyfikator "*specyfikator*" jest niedozwolony w definicji funkcji|
|[Błąd kompilatora C2724](compiler-error-c2724.md)|"*Function*": element "static" nie powinien być używany w funkcjach członkowskich zdefiniowanych w zakresie pliku|
|[Błąd kompilatora C2725](compiler-error-c2725.md)|"*Type*": nie można zgłosić lub przechwycić obiektu zarządzanego/WinRT przez wartość lub odwołanie|
|[Błąd kompilatora C2726](compiler-error-c2726.md)|"gcnew" może być użyty tylko do utworzenia obiektu z typem zarządzanym/WinRT|
|Błąd kompilatora C2727|Nieaktualne.|
|[Błąd kompilatora C2728](compiler-error-c2728.md)|"*Type*": natywna tablica nie może zawierać tego typu|
|Błąd kompilatora C2729|Nieaktualne.|
|[Błąd kompilatora C2730](compiler-error-c2730.md)|"*Class*": nie może być klasą bazową samej siebie|
|[Błąd kompilatora C2731](compiler-error-c2731.md)|"*Function*": funkcja nie może być przeciążona|
|[Błąd kompilatora C2732](compiler-error-c2732.md)|Specyfikacja powiązania jest sprzeczna z wcześniejszą specyfikacją dla elementu "*Function*"|
|[Błąd kompilatora C2733](compiler-error-c2733.md)|"*Function*": drugie powiązanie C przeciążonej funkcji jest niedozwolone|
|[Błąd kompilatora C2734](compiler-error-c2734.md)|"*Identyfikator*": obiekt const musi zostać zainicjowany, jeśli nie jest "extern"|
|[Błąd kompilatora C2735](compiler-error-c2735.md)|słowo kluczowe "*Keyword*" jest niedozwolone w specyfikatorze typu formalnego parametru|
|[Błąd kompilatora C2736](compiler-error-c2736.md)|słowo kluczowe "*Keyword*" jest niedozwolone w rzutowaniu|
|Błąd kompilatora C2737|"*Identyfikator*": obiekt "constexpr" musi zostać zainicjowany|
|[Błąd kompilatora C2738](compiler-error-c2738.md)|" *Typ*operatora": jest niejednoznaczny lub nie jest składową elementu "*Class*"|
|[Błąd kompilatora C2739](compiler-error-c2739.md)|"*Number*": jawne Wymiary tablicy Managed/WinRT muszą zawierać się w przedziale od 1 do 32|
|Błąd kompilatora C2740|wartość operandu "*Number*" jest poza zakresem "*lower_bound*  -  *upper_bound*"|
|Błąd kompilatora C2741|rozmiar ramki jest zbyt duży|
|Błąd kompilatora C2742|Nieaktualne.|
|[Błąd kompilatora C2743](compiler-error-c2743.md)|"*Type*": nie można przechwycić natywnego typu z __clrcall destruktorem lub konstruktorem kopiującym|
|Błąd kompilatora C2744|"*operator*" nie jest prawidłowym operatorem CLR/WinRT|
|[Błąd kompilatora C2745](compiler-error-c2745.md)|"*token*": ten token nie może zostać przekonwertowany na identyfikator|
|Błąd kompilatora C2746|Nieaktualne.|
|Błąd kompilatora C2747|Nieaktualne.|
|[Błąd kompilatora C2748](compiler-error-c2748.md)|tworzenie tablicy zarządzanej/WinRT musi mieć rozmiar tablicy lub Inicjator tablicy|
|[Błąd kompilatora C2749](compiler-error-c2749.md)|"*Type*": może zgłosić lub przechwycić uchwyt do zarządzanej klasy z/CLR: Safe|
|[Błąd kompilatora C2750](compiler-error-c2750.md)|"*Type*": nie można użyć "New" dla typu referencyjnego; Zamiast tego użyj "gcnew"|
|[Błąd kompilatora C2751](compiler-error-c2751.md)|"*Parameter*": Nazwa parametru funkcji nie może być kwalifikowana|
|[Błąd kompilatora C2752](compiler-error-c2752.md)|"*Template*": więcej niż jedna specjalizacja częściowa jest zgodna z listą argumentów szablonu|
|[Błąd kompilatora C2753](compiler-error-c2753.md)|"*Template*": Częściowa specjalizacja nie jest zgodna z listą argumentów dla szablonu podstawowego|
|[Błąd kompilatora C2754](compiler-error-c2754.md)|"*Template*": Częściowa specjalizacja nie może mieć zależnego parametru szablonu bez typu|
|[Błąd kompilatora C2755](compiler-error-c2755.md)|"*Parameter*": parametr niebędący typem częściowej specjalizacji musi być prostym identyfikatorem|
|[Błąd kompilatora C2756](compiler-error-c2756.md)|"*Template*": domyślne argumenty szablonu nie są dozwolone dla częściowej specjalizacji|
|[Błąd kompilatora C2757](compiler-error-c2757.md)|"*Identyfikator*": symbol o tej nazwie już istnieje i dlatego nazwa ta nie może być używana jako nazwa przestrzeni nazw|
|[Błąd kompilatora C2758](compiler-error-c2758.md)|"*member*": element członkowski typu referencyjnego musi być zainicjowany|
|Błąd kompilatora C2759|Raporty asemblera wbudowanego w wierszach: *ERROR_MESSAGE*|
|[Błąd kompilatora C2760](compiler-error-c2760.md)|Błąd składniowy: oczekiwano "*token1*", a nie "*token2*"|
|[Błąd kompilatora C2761](compiler-error-c2761.md)|"*Function*": Ponowna deklaracja funkcji składowej nie jest dozwolona|
|[Błąd kompilatora C2762](compiler-error-c2762.md)|"*Template*": nieprawidłowe wyrażenie jako argument szablonu dla "*Parameter*"|
|Błąd kompilatora C2763|"*Template*": nieprawidłowe użycie literału ciągu jako argumentu szablonu dla*parametru "Parameter*"|
|[Błąd kompilatora C2764](compiler-error-c2764.md)|"*Parameter*": parametr szablonu nie został użyty lub dający się wywieźć w częściowej*specjalizacji "*|
|[Błąd kompilatora C2765](compiler-error-c2765.md)|"*Function*": Jawna specjalizacja szablonu funkcji nie może mieć żadnych argumentów domyślnych|
|[Błąd kompilatora C2766](compiler-error-c2766.md)|Jawna specjalizacja; "*specjalizacja*" została już zdefiniowana|
|[Błąd kompilatora C2767](compiler-error-c2767.md)|niezgodność wymiaru tablicy Managed/WinRT: oczekiwane argumenty *liczbowe* — podano *liczbę*|
|[Błąd kompilatora C2768](compiler-error-c2768.md)|"*Function*": niedozwolone użycie argumentów jawnego szablonu|
|Błąd kompilatora C2769|nie można zainicjować tablicy Managed/WinRT na liście inicjatorów podstawowych/składowych|
|[Błąd kompilatora C2770](compiler-error-c2770.md)|Nieprawidłowy jawny szablon/argumenty ogólne dla elementu "*Template*"|
|[Błąd kompilatora C2771](compiler-error-c2771.md)|#import dozwolone tylko w zakresie globalnym lub przestrzeni nazw|
|Błąd kompilatora C2772|Nieaktualne.|
|[Błąd kompilatora C2773](compiler-error-c2773.md)|#import i #using dostępne tylko w kompilatorze języka C++|
|[Błąd kompilatora C2774](compiler-error-c2774.md)|"*Identyfikator*": brak metody "Put" skojarzonej z tą właściwością|
|[Błąd kompilatora C2775](compiler-error-c2775.md)|"*Identyfikator*": brak metody "Get" skojarzonej z tą właściwością|
|[Błąd kompilatora C2776](compiler-error-c2776.md)|tylko jedna metoda "Get" może być określona dla właściwości|
|[Błąd kompilatora C2777](compiler-error-c2777.md)|tylko jedna metoda "Put" może być określona dla właściwości|
|[Błąd kompilatora C2778](compiler-error-c2778.md)|nieprawidłowo sformułowany identyfikator GUID w __declspec (UUID ())|
|[Błąd kompilatora C2779](compiler-error-c2779.md)|"*Deklaracja*": metody właściwości mogą być skojarzone tylko z niestatycznymi składowymi danych|
|[Błąd kompilatora C2780](compiler-error-c2780.md)|"*Deklaracja*": oczekuje argumentów *liczbowych* -podanej *liczby*|
|[Błąd kompilatora C2781](compiler-error-c2781.md)|"*Deklaracja*": oczekuje co najmniej argumentu *liczbowego* *number*|
|[Błąd kompilatora C2782](compiler-error-c2782.md)|"*Deklaracja*": szablon/parametr ogólny "*Parameter*" jest niejednoznaczny|
|[Błąd kompilatora C2783](compiler-error-c2783.md)|"*Deklaracja*": nie można wywnioskować argumentu szablonu/ogólnego dla elementu "*Identifier*"|
|[Błąd kompilatora C2784](compiler-error-c2784.md)|"*Deklaracja*": nie można wywnioskować argumentu szablonu/ogólnego dla elementu "*Type1*" z "*Type2*"|
|[Błąd kompilatora C2785](compiler-error-c2785.md)|"*declaration1*" i "*declaration2*" mają różne typy zwracane|
|[Błąd kompilatora C2786](compiler-error-c2786.md)|"*Type*": nieprawidłowy operand dla __uuidof|
|[Błąd kompilatora C2787](compiler-error-c2787.md)|"*Identyfikator*": żaden identyfikator GUID nie został skojarzony z tym obiektem|
|[Błąd kompilatora C2788](compiler-error-c2788.md)|"*Identyfikator*": więcej niż jeden identyfikator GUID skojarzony z tym obiektem|
|Błąd kompilatora C2789|"*Identyfikator*": obiekt typu kwalifikowanego przy użyciu stałej musi być zainicjowany|
|[Błąd kompilatora C2790](compiler-error-c2790.md)|"Super": to słowo kluczowe może być używane tylko w treści funkcji składowej klasy|
|[Błąd kompilatora C2791](compiler-error-c2791.md)|niedozwolone użycie elementu "Super": "*Class*" nie ma żadnych klas bazowych|
|[Błąd kompilatora C2792](compiler-error-c2792.md)|"Super": to słowo kluczowe musi następować "::"|
|[Błąd kompilatora C2793](compiler-error-c2793.md)|"*token*": Nieoczekiwany token po oczekiwaniu "::", identyfikatora lub słowa kluczowego "operator"|
|[Błąd kompilatora C2794](compiler-error-c2794.md)|"*Identyfikator*": nie jest składową żadnej bezpośredniej lub pośredniej klasy podstawowej "*Class*"|
|[Błąd kompilatora C2795](compiler-error-c2795.md)|element "Super::*Identifier*" nie jest funkcją składową|
|Błąd kompilatora C2796|"ref New" może zostać użyte tylko do utworzenia wystąpienia typu WinRT|
|[Błąd kompilatora C2797](compiler-error-c2797.md)|Zbędn "*Identyfikator*": Inicjalizacja listy wewnątrz listy inicjatorów składowych lub inicjatora niestatycznej składowej danych nie jest zaimplementowana|
|[Błąd kompilatora C2798](compiler-error-c2798.md)|element "Super::*Identifier*" jest niejednoznaczny|
|Błąd kompilatora C2799|"*Identyfikator*": obiekt typu klasy kwalifikowanej przy użyciu stałej bez domyślnego konstruktora dostarczonego przez użytkownika musi być zainicjowany|

## <a name="see-also"></a>Zobacz także

[Błędy i ostrzeżenia dotyczące kompilatora i narzędzi kompilacji C/C++](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora C2000–C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
