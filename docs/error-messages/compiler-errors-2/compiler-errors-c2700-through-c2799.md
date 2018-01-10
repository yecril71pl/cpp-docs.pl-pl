---
title: "C2700 błędy kompilatora za pośrednictwem C2799 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
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
dev_langs: C++
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd610e74ec877229fdc720ed3c57c5a653370d94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2700-through-c2799"></a>C2700 błędy kompilatora za pośrednictwem C2799

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2700](compiler-error-c2700.md)|"*typu*": nie może zostać rzucony (Użyj/W4 dowiedzieć się więcej)|
|[Błąd kompilatora C2701](compiler-error-c2701.md)|"*funkcja*": funkcja szablonu/ogólnego nie może być zaprzyjaźniona z lokalną klasą|
|[Błąd kompilatora C2702](compiler-error-c2702.md)| __except mogą być niewidoczne w bloku końcowym|
|[Błąd kompilatora C2703](compiler-error-c2703.md)|instrukcji __leave niedozwolony|
|[Błąd kompilatora C2704](compiler-error-c2704.md)|"*funkcja*": __va_start dozwolone tylko w przypadku typu varargs — wewnętrzne|
|[Błąd kompilatora C2705](compiler-error-c2705.md)|"*etykiety*": niedozwolony skok do "*exception_block*" zakresu|
|[Błąd kompilatora C2706](compiler-error-c2706.md)|niedozwolone __except bez dopasowania __try (Brak "}" w bloku __try?)|
|[Błąd kompilatora C2707](compiler-error-c2707.md)|"*identyfikator*": zły kontekst dla wewnętrznej funkcji|
|[Błąd kompilatora C2708](compiler-error-c2708.md)|"*identyfikator*": rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania|
|[Błąd kompilatora C2709](compiler-error-c2709.md)|"*identyfikator*': długość parametrów formalnych w bajtach różni się od poprzedniej deklaracji|
|[Błąd kompilatora C2710](compiler-error-c2710.md)|"*identyfikator*": "__declspec (*modyfikator*)" może być stosowany tylko do funkcji zwracającej wskaźnik|
|[Błąd kompilatora C2711](compiler-error-c2711.md)|"*funkcja*": Ta funkcja nie może być skompilowana jako zarządzana, należy rozważyć użycie niezarządzanej funkcji #pragma|
|[Błąd kompilatora C2712](compiler-error-c2712.md)|Nie można użyć __try w funkcjach, które wymagają rozwinięcia obiektu|
|[Błąd kompilatora C2713](compiler-error-c2713.md)|tylko jeden formularz obsługi wyjątku dozwolony w pojedynczej funkcji|
|[Błąd kompilatora C2714](compiler-error-c2714.md)|alignof(void) jest niedozwolone.|
|[Błąd kompilatora C2715](compiler-error-c2715.md)|"*typu*": nie można zgłosić lub przechwycić tego typu|
|C2716 błąd kompilatora|Nieaktualne.|
|C2717 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2718](compiler-error-c2718.md)|"*typu*": rzeczywisty parametr z żądanym wyrównaniem *numer* nie zostanie wyrównany|
|[Błąd kompilatora C2719](compiler-error-c2719.md)|"*parametru*": formalny parametr z żądanym wyrównaniem *numer* nie zostanie wyrównany|
|[Błąd kompilatora C2720](compiler-error-c2720.md)|"*identyfikator*": "*specyfikator*" Specyfikator klasy składującej niedozwolony dla elementów członkowskich|
|[Błąd kompilatora C2721](compiler-error-c2721.md)|"*specyfikator*": Specyfikator klasy składującej niedozwolony między słowem kluczowym operatora i typu|
|[Błąd kompilatora C2722](compiler-error-c2722.md)|"::*operator*": niedozwolone polecenie po operatorze; Użyj "operator *operator*"|
|[Błąd kompilatora C2723](compiler-error-c2723.md)|"*funkcja*": "*specyfikator*" niedozwolony specyfikator w definicji funkcji|
|[Błąd kompilatora C2724](compiler-error-c2724.md)|"*funkcja*": "static" nie powinna być używana w funkcji członkowskiej zdefiniowanej w zakresie pliku|
|[Błąd kompilatora C2725](compiler-error-c2725.md)|"*typu*": nie można zgłosić lub przechwycić obiektu managed WinRT przez wartość lub odwołanie|
|[Błąd kompilatora C2726](compiler-error-c2726.md)|słowa kluczowego "gcnew" może służyć tylko do utworzenia obiektu z typem managed WinRT|
|C2727 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2728](compiler-error-c2728.md)|"*typu*": natywna tablica nie może zawierać tego typu|
|C2729 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2730](compiler-error-c2730.md)|"*klasy*": nie może być klasą podstawową samego siebie|
|[Błąd kompilatora C2731](compiler-error-c2731.md)|"*funkcja*": funkcja nie może być przeciążony.|
|[Błąd kompilatora C2732](compiler-error-c2732.md)|Specyfikacja powiązania jest sprzeczna z wcześniejszą specyfikacją dla "*funkcja*"|
|[Błąd kompilatora C2733](compiler-error-c2733.md)|"*funkcja*": drugie powiązanie C przeciążonej funkcji jest niedozwolone|
|[Błąd kompilatora C2734](compiler-error-c2734.md)|"*identyfikator*": obiekt "const" musi zostać zainicjowany, jeśli nie "extern"|
|[Błąd kompilatora C2735](compiler-error-c2735.md)|"*— słowo kluczowe*" — słowo kluczowe nie jest dozwolone w specyfikatorze typu formalnego parametru|
|[Błąd kompilatora C2736](compiler-error-c2736.md)|"*— słowo kluczowe*" — słowo kluczowe nie jest dozwolone przy rzutowaniu|
|C2737 błąd kompilatora|"*identyfikator*": obiekt "constexpr" musi zostać zainicjowany|
|[Błąd kompilatora C2738](compiler-error-c2738.md)|"operator *typu*": jest niejednoznaczny lub nie jest elementem członkowskim "*klasy*"|
|[Błąd kompilatora C2739](compiler-error-c2739.md)|"*numer*": jawne tablicy managed WinRT wymiary muszą być od 1 do 32|
|C2740 błąd kompilatora|wartość operandu "*numer*"jest poza zakresem"*lower_bound* - *upper_bound*"|
|C2741 błąd kompilatora|zbyt duży rozmiar ramki|
|C2742 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2743](compiler-error-c2743.md)|"*typu*": nie można przechwycić natywnego typu destruktorem __clrcall lub konstruktorem kopiującym|
|C2744 błąd kompilatora|"*operator*" nie jest prawidłowym operatorem CLR i WinRT|
|[Błąd kompilatora C2745](compiler-error-c2745.md)|"*tokenu*": ten token nie można przekonwertować na identyfikator|
|C2746 błąd kompilatora|Nieaktualne.|
|C2747 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2748](compiler-error-c2748.md)|do utworzenia tablicy Managed WinRT musi mieć rozmiaru tablicy lub inicjatora tablicy|
|[Błąd kompilatora C2749](compiler-error-c2749.md)|"*typu*": może tylko zgłosić lub przechwycić uchwyt do zarządzanej klasy z/CLR: Safe|
|[Błąd kompilatora C2750](compiler-error-c2750.md)|"*typu*": nie można użyć "new" w odwołaniu typu; zamiast niego użyj słowa kluczowego "gcnew"|
|[Błąd kompilatora C2751](compiler-error-c2751.md)|"*parametru*": Nazwa parametru funkcji nie może być kwalifikowany.|
|[Błąd kompilatora C2752](compiler-error-c2752.md)|"*szablonu*": więcej niż jedna składowa specjalizacji pasuje do szablonu listy argumentów|
|[Błąd kompilatora C2753](compiler-error-c2753.md)|"*szablonu*": składowa specjalizacji nie odpowiada liście argumentów dla podstawowego szablonu|
|[Błąd kompilatora C2754](compiler-error-c2754.md)|"*szablonu*": składowa specjalizacji nie może mieć parametru szablonu bez typu zależnego|
|[Błąd kompilatora C2755](compiler-error-c2755.md)|"*parametru*": stała parametryzująca składowej specjalizacji musi być prostym identyfikatorem|
|[Błąd kompilatora C2756](compiler-error-c2756.md)|"*szablonu*": domyślne szablonowe argumenty niedozwolone w składowej specjalizacji|
|[Błąd kompilatora C2757](compiler-error-c2757.md)|"*identyfikator*": symbol o tej nazwie już istnieje i dlatego ta nazwa nie może służyć jako nazwy przestrzeni nazw|
|[Błąd kompilatora C2758](compiler-error-c2758.md)|"*elementu członkowskiego*": element członkowski typu referencyjnego musi zostać zainicjowany|
|C2759 błąd kompilatora|Raporty asemblera w wierszu: *error_message*|
|[Błąd kompilatora C2760](compiler-error-c2760.md)|Błąd składniowy: oczekiwano "*token1*'not'*token2*"|
|[Błąd kompilatora C2761](compiler-error-c2761.md)|"*funkcja*": niedozwolone funkcji członkowskiej|
|[Błąd kompilatora C2762](compiler-error-c2762.md)|"*szablonu*": nieprawidłowe wyrażenie jako argument szablonu dla "*parametru*"|
|C2763 błąd kompilatora|"*szablonu*": nieprawidłowe użycie ciągu literałów jako argument szablonu dla "*parametru*"|
|[Błąd kompilatora C2764](compiler-error-c2764.md)|"*parametru*": parametr szablonu nieużywany lub dający się wywieźć w składowej specjalizacji "*specjalizacji*"|
|[Błąd kompilatora C2765](compiler-error-c2765.md)|"*funkcja*": jawna specjalizacja szablonu funkcji nie może mieć argumentów domyślnych|
|[Błąd kompilatora C2766](compiler-error-c2766.md)|jawna specjalizacja; "*specjalizacji*" został już zdefiniowany|
|[Błąd kompilatora C2767](compiler-error-c2767.md)|Niezgodność wymiaru tablicy Managed WinRT: Oczekiwano *numer* argumenty: *numer* podane|
|[Błąd kompilatora C2768](compiler-error-c2768.md)|"*funkcja*": niedozwolone użycie argumentów jawnego szablonu|
|C2769 błąd kompilatora|użytkownik nie może zainicjować nawiasu klamrowego tablicą managed WinRT w podstawowej/członkowskiej liście inicjatorów|
|[Błąd kompilatora C2770](compiler-error-c2770.md)|Nieprawidłowy jawnego szablonu/generic argumentów dla '*szablonu*"|
|[Błąd kompilatora C2771](compiler-error-c2771.md)|#import dozwolone tylko globalnie lub zakresie przestrzeni nazw|
|C2772 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2773](compiler-error-c2773.md)|#import i #using dostępne tylko w kompilatorze języka C++|
|[Błąd kompilatora C2774](compiler-error-c2774.md)|"*identyfikator*": nie metody "put" jest skojarzony z tą właściwością|
|[Błąd kompilatora C2775](compiler-error-c2775.md)|"*identyfikator*": Brak metody "get" jest skojarzony z tą właściwością|
|[Błąd kompilatora C2776](compiler-error-c2776.md)|tylko jedna metoda "get" może być określona dla właściwości|
|[Błąd kompilatora C2777](compiler-error-c2777.md)|tylko jedna metoda "put" może być określona dla właściwości|
|[Błąd kompilatora C2778](compiler-error-c2778.md)|niewłaściwie uformowane GUID w __declspec(uuid())|
|[Błąd kompilatora C2779](compiler-error-c2779.md)|"*deklaracji*": właściwość metod może być skojarzony tylko z elementami członkowskimi danych niestatycznych|
|[Błąd kompilatora C2780](compiler-error-c2780.md)|"*deklaracji*": oczekuje *numer* argumentów - *numer* podane|
|[Błąd kompilatora C2781](compiler-error-c2781.md)|"*deklaracji*": oczekuje co najmniej *numer* argumentu - *numer* podane|
|[Błąd kompilatora C2782](compiler-error-c2782.md)|"*deklaracji*": parametr szablonu/ogólne "*parametru*" jest niejednoznaczny|
|[Błąd kompilatora C2783](compiler-error-c2783.md)|"*deklaracji*": nie można wywnioskować argumentu szablonu/ogólne "*identyfikator*"|
|[Błąd kompilatora C2784](compiler-error-c2784.md)|"*deklaracji*": nie można wywnioskować argumentu szablonu/ogólne "*type1*"od"*type2*"|
|[Błąd kompilatora C2785](compiler-error-c2785.md)|"*declaration1*"i"*declaration2*" mają różne typy zwracane|
|[Błąd kompilatora C2786](compiler-error-c2786.md)|"*typu*": nieprawidłowy operand dla __uuidof|
|[Błąd kompilatora C2787](compiler-error-c2787.md)|"*identyfikator*": żaden identyfikator GUID nie został skojarzony z tym obiektem|
|[Błąd kompilatora C2788](compiler-error-c2788.md)|"*identyfikator*": więcej niż jeden GUID skojarzony z tym obiektem|
|C2789 błąd kompilatora|"*identyfikator*": obiekt kwalifikowanego typu const musi zostać zainicjowany|
|[Błąd kompilatora C2790](compiler-error-c2790.md)|"super": to słowo kluczowe może być użyte tylko w treści funkcji członkowskiej klasy|
|[Błąd kompilatora C2791](compiler-error-c2791.md)|niedozwolone użycie "super": "*klasy*" nie ma żadnych klas podstawowych|
|[Błąd kompilatora C2792](compiler-error-c2792.md)|'super": musi następować słowo kluczowe '::'|
|[Błąd kompilatora C2793](compiler-error-c2793.md)|"*tokenu*": nieoczekiwany token następujący "::", identyfikatora lub słowa kluczowego 'operator' oczekiwano|
|[Błąd kompilatora C2794](compiler-error-c2794.md)|"*identyfikator*": nie jest elementem członkowskim żadnych bezpośrednich lub pośrednich klasa podstawowa "*klasy*"|
|[Błąd kompilatora C2795](compiler-error-c2795.md)|"super::*identyfikator*" nie jest funkcją członkowską|
|C2796 błąd kompilatora|"ref new" może używać tylko do utworzenia wystąpienia typu WinRT|
|[Błąd kompilatora C2797](compiler-error-c2797.md)|(Przestarzałe) "*identyfikator*": Inicjalizacja listy wewnątrz listy inicjatorów elementu członkowskiego lub inicjator elementu członkowskiego danych niestatycznych nie jest zaimplementowana.|
|[Błąd kompilatora C2798](compiler-error-c2798.md)|"super::*identyfikator*" jest niejednoznaczny|
|C2799 błąd kompilatora|"*identyfikator*": konieczne jest zainicjowanie obiektu typu klasy kwalifikatora const bez konstruktora domyślnego określonego przez użytkownika|
