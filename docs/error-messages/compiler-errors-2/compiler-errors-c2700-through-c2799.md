---
title: "C2700 błędy kompilatora za pośrednictwem C2799 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: d8246cec8db138b053f3c239448043147131166c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2700-through-c2799"></a>C2700 błędy kompilatora za pośrednictwem C2799
Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.  
  
> [!NOTE]
>  Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).  
  
|Błąd|Komunikat|  
|-----------|-------------|  
|[C2700 błąd kompilatora](compiler-error-c2700.md)|"*typu*": nie może zostać rzucony (Użyj/W4 dowiedzieć się więcej)|  
|[C2701 błąd kompilatora](compiler-error-c2701.md)|"*funkcja*": funkcja szablonu/ogólnego nie może być zaprzyjaźniona z lokalną klasą|  
|[C2702 błąd kompilatora](compiler-error-c2702.md)| __except mogą być niewidoczne w bloku końcowym|  
|[C2703 błąd kompilatora](compiler-error-c2703.md)|instrukcji __leave niedozwolony|  
|[C2704 błąd kompilatora](compiler-error-c2704.md)|"*funkcja*": __va_start dozwolone tylko w przypadku typu varargs — wewnętrzne|  
|[C2705 błąd kompilatora](compiler-error-c2705.md)|"*etykiety*": niedozwolony skok do "*exception_block*" zakresu|  
|[C2706 błąd kompilatora](compiler-error-c2706.md)|niedozwolone __except bez dopasowania __try (Brak "}" w bloku __try?)|  
|[C2707 błąd kompilatora](compiler-error-c2707.md)|"*identyfikator*": zły kontekst dla wewnętrznej funkcji|  
|[C2708 błąd kompilatora](compiler-error-c2708.md)|"*identyfikator*": rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania|  
|[C2709 błąd kompilatora](compiler-error-c2709.md)|"*identyfikator*': długość parametrów formalnych w bajtach różni się od poprzedniej deklaracji|  
|[C2710 błąd kompilatora](compiler-error-c2710.md)|"*identyfikator*": "__declspec (*modyfikator*)" może być stosowany tylko do funkcji zwracającej wskaźnik|  
|[C2711 błąd kompilatora](compiler-error-c2711.md)|"*funkcja*": Ta funkcja nie może być skompilowana jako zarządzana, należy rozważyć użycie niezarządzanej funkcji #pragma|  
|[C2712 błąd kompilatora](compiler-error-c2712.md)|Nie można użyć __try w funkcjach, które wymagają rozwinięcia obiektu|  
|[C2713 błąd kompilatora](compiler-error-c2713.md)|tylko jeden formularz obsługi wyjątku dozwolony w pojedynczej funkcji|  
|[C2714 błąd kompilatora](compiler-error-c2714.md)|alignof(void) jest niedozwolone.|  
|[C2715 błąd kompilatora](compiler-error-c2715.md)|"*typu*": nie można zgłosić lub przechwycić tego typu|  
|C2716 błąd kompilatora|Nieaktualne.|  
|C2717 błąd kompilatora|Nieaktualne.|  
|[C2718 błąd kompilatora](compiler-error-c2718.md)|"*typu*": rzeczywisty parametr z żądanym wyrównaniem *numer* nie zostanie wyrównany|  
|[C2719 błąd kompilatora](compiler-error-c2719.md)|"*parametru*": formalny parametr z żądanym wyrównaniem *numer* nie zostanie wyrównany|  
|[C2720 błąd kompilatora](compiler-error-c2720.md)|"*identyfikator*": "*specyfikator*" Specyfikator klasy składującej niedozwolony dla elementów członkowskich|  
|[C2721 błąd kompilatora](compiler-error-c2721.md)|"*specyfikator*": Specyfikator klasy składującej niedozwolony między słowem kluczowym operatora i typu|  
|[C2722 błąd kompilatora](compiler-error-c2722.md)|"::*operator*": niedozwolone polecenie po operatorze; Użyj "operator *operator*"|  
|[C2723 błąd kompilatora](compiler-error-c2723.md)|"*funkcja*": "*specyfikator*" niedozwolony specyfikator w definicji funkcji|  
|[C2724 błąd kompilatora](compiler-error-c2724.md)|"*funkcja*": "static" nie powinna być używana w funkcji członkowskiej zdefiniowanej w zakresie pliku|  
|[C2725 błąd kompilatora](compiler-error-c2725.md)|"*typu*": nie można zgłosić lub przechwycić obiektu managed WinRT przez wartość lub odwołanie|  
|[C2726 błąd kompilatora](compiler-error-c2726.md)|słowa kluczowego "gcnew" może służyć tylko do utworzenia obiektu z typem managed WinRT|  
|C2727 błąd kompilatora|Nieaktualne.|  
|[C2728 błąd kompilatora](compiler-error-c2728.md)|"*typu*": natywna tablica nie może zawierać tego typu|  
|C2729 błąd kompilatora|Nieaktualne.|  
|[C2730 błąd kompilatora](compiler-error-c2730.md)|"*klasy*": nie może być klasą podstawową samego siebie|  
|[C2731 błąd kompilatora](compiler-error-c2731.md)|"*funkcja*": funkcja nie może być przeciążony.|  
|[C2732 błąd kompilatora](compiler-error-c2732.md)|Specyfikacja powiązania jest sprzeczna z wcześniejszą specyfikacją dla "*funkcja*"|  
|[C2733 błąd kompilatora](compiler-error-c2733.md)|"*funkcja*": drugie powiązanie C przeciążonej funkcji jest niedozwolone|  
|[C2734 błąd kompilatora](compiler-error-c2734.md)|"*identyfikator*": obiekt "const" musi zostać zainicjowany, jeśli nie "extern"|  
|[C2735 błąd kompilatora](compiler-error-c2735.md)|"*— słowo kluczowe*" — słowo kluczowe nie jest dozwolone w specyfikatorze typu formalnego parametru|  
|[C2736 błąd kompilatora](compiler-error-c2736.md)|"*— słowo kluczowe*" — słowo kluczowe nie jest dozwolone przy rzutowaniu|  
|C2737 błąd kompilatora|"*identyfikator*": obiekt "constexpr" musi zostać zainicjowany|  
|[C2738 błąd kompilatora](compiler-error-c2738.md)|"operator *typu*": jest niejednoznaczny lub nie jest elementem członkowskim "*klasy*"|  
|[C2739 błąd kompilatora](compiler-error-c2739.md)|"*numer*": jawne tablicy managed WinRT wymiary muszą być od 1 do 32|  
|C2740 błąd kompilatora|wartość operandu "*numer*"jest poza zakresem"*lower_bound* - *upper_bound*"|  
|C2741 błąd kompilatora|zbyt duży rozmiar ramki|  
|C2742 błąd kompilatora|Nieaktualne.|  
|[C2743 błąd kompilatora](compiler-error-c2743.md)|"*typu*": nie można przechwycić natywnego typu destruktorem __clrcall lub konstruktorem kopiującym|  
|C2744 błąd kompilatora|"*operator*" nie jest prawidłowym operatorem CLR i WinRT|  
|[C2745 błąd kompilatora](compiler-error-c2745.md)|"*tokenu*": ten token nie można przekonwertować na identyfikator|  
|C2746 błąd kompilatora|Nieaktualne.|  
|C2747 błąd kompilatora|Nieaktualne.|  
|[C2748 błąd kompilatora](compiler-error-c2748.md)|do utworzenia tablicy Managed WinRT musi mieć rozmiaru tablicy lub inicjatora tablicy|  
|[C2749 błąd kompilatora](compiler-error-c2749.md)|"*typu*": może tylko zgłosić lub przechwycić uchwyt do zarządzanej klasy z/CLR: Safe|  
|[C2750 błąd kompilatora](compiler-error-c2750.md)|"*typu*": nie można użyć "new" w odwołaniu typu; zamiast niego użyj słowa kluczowego "gcnew"|  
|[C2751 błąd kompilatora](compiler-error-c2751.md)|"*parametru*": Nazwa parametru funkcji nie może być kwalifikowany.|  
|[C2752 błąd kompilatora](compiler-error-c2752.md)|"*szablonu*": więcej niż jedna składowa specjalizacji pasuje do szablonu listy argumentów|  
|[C2753 błąd kompilatora](compiler-error-c2753.md)|"*szablonu*": składowa specjalizacji nie odpowiada liście argumentów dla podstawowego szablonu|  
|[C2754 błąd kompilatora](compiler-error-c2754.md)|"*szablonu*": składowa specjalizacji nie może mieć parametru szablonu bez typu zależnego|  
|[C2755 błąd kompilatora](compiler-error-c2755.md)|"*parametru*": stała parametryzująca składowej specjalizacji musi być prostym identyfikatorem|  
|[C2756 błąd kompilatora](compiler-error-c2756.md)|"*szablonu*": domyślne szablonowe argumenty niedozwolone w składowej specjalizacji|  
|[C2757 błąd kompilatora](compiler-error-c2757.md)|"*identyfikator*": symbol o tej nazwie już istnieje i dlatego ta nazwa nie może służyć jako nazwy przestrzeni nazw|  
|[C2758 błąd kompilatora](compiler-error-c2758.md)|"*elementu członkowskiego*": element członkowski typu referencyjnego musi zostać zainicjowany|  
|C2759 błąd kompilatora|Raporty asemblera w wierszu: *error_message*|  
|[C2760 błąd kompilatora](compiler-error-c2760.md)|Błąd składniowy: oczekiwano "*token1*'not'*token2*"|  
|[C2761 błąd kompilatora](compiler-error-c2761.md)|"*funkcja*": niedozwolone funkcji członkowskiej|  
|[C2762 błąd kompilatora](compiler-error-c2762.md)|"*szablonu*": nieprawidłowe wyrażenie jako argument szablonu dla "*parametru*"|  
|C2763 błąd kompilatora|"*szablonu*": nieprawidłowe użycie ciągu literałów jako argument szablonu dla "*parametru*"|  
|[C2764 błąd kompilatora](compiler-error-c2764.md)|"*parametru*": parametr szablonu nieużywany lub dający się wywieźć w składowej specjalizacji "*specjalizacji*"|  
|[C2765 błąd kompilatora](compiler-error-c2765.md)|"*funkcja*": jawna specjalizacja szablonu funkcji nie może mieć argumentów domyślnych|  
|[C2766 błąd kompilatora](compiler-error-c2766.md)|jawna specjalizacja; "*specjalizacji*" został już zdefiniowany|  
|[C2767 błąd kompilatora](compiler-error-c2767.md)|Niezgodność wymiaru tablicy Managed WinRT: Oczekiwano *numer* argumenty: *numer* podane|  
|[C2768 błąd kompilatora](compiler-error-c2768.md)|"*funkcja*": niedozwolone użycie argumentów jawnego szablonu|  
|C2769 błąd kompilatora|użytkownik nie może zainicjować nawiasu klamrowego tablicą managed WinRT w podstawowej/członkowskiej liście inicjatorów|  
|[C2770 błąd kompilatora](compiler-error-c2770.md)|Nieprawidłowy jawnego szablonu/generic argumentów dla '*szablonu*"|  
|[C2771 błąd kompilatora](compiler-error-c2771.md)|#import dozwolone tylko globalnie lub zakresie przestrzeni nazw|  
|C2772 błąd kompilatora|Nieaktualne.|  
|[C2773 błąd kompilatora](compiler-error-c2773.md)|#import i #using dostępne tylko w kompilatorze języka C++|  
|[C2774 błąd kompilatora](compiler-error-c2774.md)|"*identyfikator*": nie metody "put" jest skojarzony z tą właściwością|  
|[C2775 błąd kompilatora](compiler-error-c2775.md)|"*identyfikator*": Brak metody "get" jest skojarzony z tą właściwością|  
|[C2776 błąd kompilatora](compiler-error-c2776.md)|tylko jedna metoda "get" może być określona dla właściwości|  
|[C2777 błąd kompilatora](compiler-error-c2777.md)|tylko jedna metoda "put" może być określona dla właściwości|  
|[C2778 błąd kompilatora](compiler-error-c2778.md)|niewłaściwie uformowane GUID w __declspec(uuid())|  
|[C2779 błąd kompilatora](compiler-error-c2779.md)|"*deklaracji*": właściwość metod może być skojarzony tylko z elementami członkowskimi danych niestatycznych|  
|[C2780 błąd kompilatora](compiler-error-c2780.md)|"*deklaracji*": oczekuje *numer* argumentów - *numer* podane|  
|[C2781 błąd kompilatora](compiler-error-c2781.md)|"*deklaracji*": oczekuje co najmniej *numer* argumentu - *numer* podane|  
|[C2782 błąd kompilatora](compiler-error-c2782.md)|"*deklaracji*": parametr szablonu/ogólne "*parametru*" jest niejednoznaczny|  
|[C2783 błąd kompilatora](compiler-error-c2783.md)|"*deklaracji*": nie można wywnioskować argumentu szablonu/ogólne "*identyfikator*"|  
|[C2784 błąd kompilatora](compiler-error-c2784.md)|"*deklaracji*": nie można wywnioskować argumentu szablonu/ogólne "*type1*"od"*type2*"|  
|[C2785 błąd kompilatora](compiler-error-c2785.md)|"*declaration1*"i"*declaration2*" mają różne typy zwracane|  
|[C2786 błąd kompilatora](compiler-error-c2786.md)|"*typu*": nieprawidłowy operand dla __uuidof|  
|[C2787 błąd kompilatora](compiler-error-c2787.md)|"*identyfikator*": żaden identyfikator GUID nie został skojarzony z tym obiektem|  
|[C2788 błąd kompilatora](compiler-error-c2788.md)|"*identyfikator*": więcej niż jeden GUID skojarzony z tym obiektem|  
|C2789 błąd kompilatora|"*identyfikator*": obiekt kwalifikowanego typu const musi zostać zainicjowany|  
|[C2790 błąd kompilatora](compiler-error-c2790.md)|"super": to słowo kluczowe może być użyte tylko w treści funkcji członkowskiej klasy|  
|[C2791 błąd kompilatora](compiler-error-c2791.md)|niedozwolone użycie "super": "*klasy*" nie ma żadnych klas podstawowych|  
|[C2792 błąd kompilatora](compiler-error-c2792.md)|'super": musi następować słowo kluczowe '::'|  
|[C2793 błąd kompilatora](compiler-error-c2793.md)|"*tokenu*": nieoczekiwany token następujący "::", identyfikatora lub słowa kluczowego 'operator' oczekiwano|  
|[C2794 błąd kompilatora](compiler-error-c2794.md)|"*identyfikator*": nie jest elementem członkowskim żadnych bezpośrednich lub pośrednich klasa podstawowa "*klasy*"|  
|[C2795 błąd kompilatora](compiler-error-c2795.md)|"super::*identyfikator*" nie jest funkcją członkowską|  
|C2796 błąd kompilatora|"ref new" może używać tylko do utworzenia wystąpienia typu WinRT|  
|[Błąd kompilatora C2797](compiler-error-c2797.md)|(Przestarzałe) "*identyfikator*": Inicjalizacja listy wewnątrz listy inicjatorów elementu członkowskiego lub inicjator elementu członkowskiego danych niestatycznych nie jest zaimplementowana.|  
|[C2798 błąd kompilatora](compiler-error-c2798.md)|"super::*identyfikator*" jest niejednoznaczny|  
|C2799 błąd kompilatora|"*identyfikator*": konieczne jest zainicjowanie obiektu typu klasy kwalifikatora const bez konstruktora domyślnego określonego przez użytkownika|  
