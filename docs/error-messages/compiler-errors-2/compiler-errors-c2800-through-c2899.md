---
title: "C2800 błędy kompilatora za pośrednictwem C2899 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
helpviewer_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
dev_langs: C++
ms.assetid: e5de1e92-746a-4315-a331-c5d9efb76dbb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9c825bba825db2bba28e29c0cf38bb845492509c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2800-through-c2899"></a>C2800 błędy kompilatora za pośrednictwem C2899
Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.  
  
> [!NOTE]
>  Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).  
  
|Błąd|Komunikat|  
|-----------|-------------|  
|[C2800 błąd kompilatora](compiler-error-c2800.md)|"operator *operator*" nie może zostać przeciążony|  
|[C2801 błąd kompilatora](compiler-error-c2801.md)|"*elementu członkowskiego*" musi być niestatycznego elementu członkowskiego|  
|[C2802 błąd kompilatora](compiler-error-c2802.md)|statyczny element członkowski "operator *operator*" nie ma formalnych parametrów|  
|[C2803 błąd kompilatora](compiler-error-c2803.md)|"operator *operator*" musi mieć co najmniej jeden formalny parametr typu klasy|  
|[C2804 błąd kompilatora](compiler-error-c2804.md)|binarne "operator *operator*" ma zbyt wiele parametrów|  
|[C2805 błąd kompilatora](compiler-error-c2805.md)|binarne "operator *operator*" ma za mało parametrów|  
|[C2806 błąd kompilatora](compiler-error-c2806.md)|"operator *operator*" ma zbyt wiele parametrów formalnych|  
|[C2807 błąd kompilatora](compiler-error-c2807.md)|drugi formalny parametr dla przyrostkowego "operator *operator*" musi być typu "int"|  
|[C2808 błąd kompilatora](compiler-error-c2808.md)|Jednoargumentowy "operator *operator*" ma zbyt wiele parametrów formalnych|  
|[C2809 błąd kompilatora](compiler-error-c2809.md)|"operator *operator*" nie ma formalnych parametrów|  
|[C2810 błąd kompilatora](compiler-error-c2810.md)|"*interfejsu*": interfejs może dziedziczyć tylko z innego interfejsu|  
|[C2811 błąd kompilatora](compiler-error-c2811.md)|"*type1*": nie może dziedziczyć po "*type2*", klasa ref może dziedziczyć tylko z klasy interfejsu lub klasy referencyjnej|  
|[C2812 błąd kompilatora](compiler-error-c2812.md)|#import nie jest obsługiwany z/CLR: pure i/CLR: Safe|  
|[C2813 błąd kompilatora](compiler-error-c2813.md)|#import nie jest obsługiwany z /MP|  
|[C2814 błąd kompilatora](compiler-error-c2814.md)|"*elementu członkowskiego*": typ natywny nie może być zagnieżdżone w obrębie typu managed WinRT "*klasy*"|  
|[C2815 błąd kompilatora](compiler-error-c2815.md)|"operator delete": pierwszy formalny parametr musi być "void *", ale "*typu *" użyto|  
|C2816 błąd kompilatora|Nieaktualne.|  
|[C2817 błąd kompilatora](compiler-error-c2817.md)|typem zwracanym dla "operator delete" musi być "void"|  
|[C2818 błąd kompilatora](compiler-error-c2818.md)|Aplikacja przeciążonego "operator ->" jest rekursywna za pośrednictwem typu "*klasy*"|  
|[C2819 błąd kompilatora](compiler-error-c2819.md)|Typ "*klasy*" nie ma przeciążonego elementu członkowskiego "operator ->"|  
|C2820 błąd kompilatora|Nieaktualne.|  
|[C2821 błąd kompilatora](compiler-error-c2821.md)|pierwszy formalny parametr dla "operator new" musi być "size_t"|  
|C2822 błąd kompilatora|lokalne rozwinięcie nie jest obsługiwana na tej platformie|  
|[C2823 błąd kompilatora](compiler-error-c2823.md)|szablon elementu typedef/ogólnego jest niedozwolony|  
|[C2824 błąd kompilatora](compiler-error-c2824.md)|typem zwracanym dla "operator new" musi być "void *"|  
|[C2825 błąd kompilatora](compiler-error-c2825.md)|'*identyfikator*": musi być klasą lub przestrzenią nazw, gdy następuje '::'|  
|C2826 błąd kompilatora|Nieaktualne.|  
|[C2827 błąd kompilatora](compiler-error-c2827.md)|"operator *operator*" nie może być przesłaniany globalnie przez jednoargumentowy formularz|  
|[C2828 błąd kompilatora](compiler-error-c2828.md)|"operator *operator*" nie może być przesłaniany globalnie przez binarny formularz|  
|[C2829 błąd kompilatora](compiler-error-c2829.md)|"operator *operator*" nie może mieć zmiennej listy parametrów|  
|[C2830 błąd kompilatora](compiler-error-c2830.md)|tylko umieszczenie parametrów dla "operator new" może mieć wartości domyślnej|  
|[C2831 błąd kompilatora](compiler-error-c2831.md)|"operator *operator*" nie może mieć parametrów domyślnych|  
|C2832 błąd kompilatora|"*identyfikator*": Typ referencyjny nie może być inicjowany przez wartość|  
|[C2833 błąd kompilatora](compiler-error-c2833.md)|"operator *tokenu*" nie jest rozpoznany jako operator lub typ|  
|[C2834 błąd kompilatora](compiler-error-c2834.md)|"operator *operator*" musi być globalnie kwalifikowany|  
|[C2835 błąd kompilatora](compiler-error-c2835.md)|konwersja zdefiniowana przez użytkownika "*typu*" nie przyjmuje żadnych formalnych parametrów|  
|C2836 błąd kompilatora|"*identyfikator*": tylko jeden danych niestatycznego elementu Członkowskiego Unii może mieć inicjatora elementu członkowskiego domyślne|  
|C2837 błąd kompilatora|"*funkcja*": nie można użyć dyrektyw OpenMP i #pragma loop(hint_parallel) w tej samej funkcji|  
|[C2838 błąd kompilatora](compiler-error-c2838.md)|"*identyfikator*": niedozwolona nazwa kwalifikowana w deklaracji elementu członkowskiego|  
|[C2839 błąd kompilatora](compiler-error-c2839.md)|Nieprawidłowy typ zwracany "*typu*" dla przeciążonego "operator ->"|  
|C2840 błąd kompilatora|słowo argumentu instrukcji nie jest stałą|  
|C2841 błąd kompilatora|argument nie jest stałą rejestru|  
|[C2842 błąd kompilatora](compiler-error-c2842.md)|"*klasy*": typ zarządzany WinRT nie może definiować własnego "operator new" lub "operator delete"|  
|[C2843 błąd kompilatora](compiler-error-c2843.md)|"*elementu członkowskiego*": nie można przyjąć adresu elementu członkowskiego danych niestatycznych lub metody typu zarządzanego WinRT|  
|[C2844 błąd kompilatora](compiler-error-c2844.md)|"*identyfikator*": nie może być elementem członkowskim interfejsu "*interfejsu*"|  
|[C2845 błąd kompilatora](compiler-error-c2845.md)|"*typu*": arytmetyka wskaźnika nie jest dozwolona dla tego typu|  
|[C2846 błąd kompilatora](compiler-error-c2846.md)|"*interfejsu*": interfejs nie może mieć konstruktora|  
|[C2847 błąd kompilatora](compiler-error-c2847.md)|Nie można zastosować operatora sizeof do typu zarządzanego WinRT "*klasy*"|  
|C2848 błąd kompilatora|"*klasy*": typ zarządzany WinRT nie może być elementem członkowskim związku|  
|[C2849 błąd kompilatora](compiler-error-c2849.md)|"*interfejsu*": interfejs nie może mieć destruktora|  
|[C2850 błąd kompilatora](compiler-error-c2850.md)|"*skonstruować*": dozwolone tylko w zakresie pliku; może nie być w zagnieżdżonej konstrukcji|  
|C2851 błąd kompilatora|"*wyliczenia*": publiczne wyliczenie WinRT może używać tylko "int" lub "unsigned int" jako typu podstawowego|  
|C2852 błąd kompilatora|"*identyfikator*": tylko elementy członkowskie danych mogą być inicjowane w obrębie klasy|  
|C2853 błąd kompilatora|"*identyfikator*": elementu członkowskiego danych niestatycznych nie może mieć typu zawierającego "auto"|  
|[C2854 błąd kompilatora](compiler-error-c2854.md)|Błąd składni w #pragma hdrstop|  
|[C2855 błąd kompilatora](compiler-error-c2855.md)|Opcja wiersza polecenia "*opcji*" niespójna z prekompilowanym nagłówkiem|  
|[C2856 błąd kompilatora](compiler-error-c2856.md)|#pragma hdrstop nie może być wewnątrz bloku #if|  
|[C2857 błąd kompilatora](compiler-error-c2857.md)|"#include" instrukcji określony za pomocą /Yc*filename* opcji wiersza polecenia nie został znaleziony w pliku źródłowym|  
|[C2858 błąd kompilatora](compiler-error-c2858.md)|Opcja wiersza polecenia "/Yc (/Fd*filename*)" niespójna z prekompilowanym nagłówkiem, który używa "/Fd*filename*"|  
|[C2859 błąd kompilatora](compiler-error-c2859.md)|*Nazwa pliku* nie jest *filetype* pliku, który został użyty podczas tworzenia prekompilowanego nagłówka, ponownie utwórz prekompilowany nagłówek.|  
|[C2860 błąd kompilatora](compiler-error-c2860.md)|"void" nie może być typem argumentu, z wyjątkiem "(void)"|  
|[C2861 błąd kompilatora](compiler-error-c2861.md)|"*deklaracji*": funkcja członkowska interfejsu nie może być zdefiniowana|  
|[C2862 błąd kompilatora](compiler-error-c2862.md)|"*interfejsu*": interfejs może mieć tylko publiczne elementy członkowskie|  
|[C2863 błąd kompilatora](compiler-error-c2863.md)|"*interfejsu*": interfejs nie może mieć przyjaciół|  
|[C2864 błąd kompilatora](compiler-error-c2864.md)|"*identyfikator*": zmienna szablon/elementu członkowskiego danych statycznych z inicjatorem w obrębie klasy musi mieć typ całkowitoliczbowy const-volatile|  
|[C2865 błąd kompilatora](compiler-error-c2865.md)|"*operator*": niedozwolone porównanie dla obiekt wskaźnika/dojścia|  
|C2866 błąd kompilatora|Nieaktualne.|  
|[C2867 błąd kompilatora](compiler-error-c2867.md)|"*identyfikator*": nie jest przestrzenią nazw|  
|[C2868 błąd kompilatora](compiler-error-c2868.md)|"*identyfikator*": Niedozwolona składnia dla deklaracji using; Oczekiwano kwalifikowanej nazwy|  
|[C2869 błąd kompilatora](compiler-error-c2869.md)|"*identyfikator*": została już zdefiniowana jako przestrzeń nazw|  
|[C2870 błąd kompilatora](compiler-error-c2870.md)|"*identyfikator*": definicja przestrzeni nazw musi znajdować się w zakresie pliku albo natychmiast w innej definicji przestrzeni nazw|  
|[C2871 błąd kompilatora](compiler-error-c2871.md)|"*identyfikator*": przestrzeń nazw o tej nazwie nie istnieje.|  
|[C2872 błąd kompilatora](compiler-error-c2872.md)|"*identyfikator*": niejednoznaczny symbol|  
|[C2873 błąd kompilatora](compiler-error-c2873.md)|"*symbol*": symbol nie może zostać użyty w deklaracji using|  
|[C2874 błąd kompilatora](compiler-error-c2874.md)|Deklaracja Using powoduje wielokrotną deklarację "*identyfikator*"|  
|[C2875 błąd kompilatora](compiler-error-c2875.md)|Deklaracja Using powoduje wielokrotną deklarację "*klasy*::*identyfikator*"|  
|[C2876 błąd kompilatora](compiler-error-c2876.md)|"*klasy*::*elementu członkowskiego*": nie wszystkie przeciążenia są dostępne|  
|[C2877 błąd kompilatora](compiler-error-c2877.md)|"*elementu członkowskiego*"nie jest dostępny z"*klasy*"|  
|[C2878 błąd kompilatora](compiler-error-c2878.md)|"*identyfikator*": przestrzeń nazw lub klasa o tej nazwie nie istnieje|  
|[C2879 błąd kompilatora](compiler-error-c2879.md)|"*identyfikator*": tylko do istniejącej przestrzeni nazw można przypisać alternatywną nazwę poprzez definicję aliasu przestrzeni nazw|  
|C2880 błąd kompilatora|__swi lub __hvc wymaga prawidłowej stałej jako pierwszego argumentu (numer SWI)|  
|[C2881 błąd kompilatora](compiler-error-c2881.md)|"*identyfikator*": jest już używany jako alias '*klasy*"|  
|[C2882 błąd kompilatora](compiler-error-c2882.md)|"*identyfikator*": niedozwolone użycie identyfikatora przestrzeni nazw w wyrażeniu|  
|[C2883 błąd kompilatora](compiler-error-c2883.md)|"*funkcja*": deklaracja funkcji powoduje konflikt z "*identyfikator*" wynikające z deklaracją using|  
|[C2884 błąd kompilatora](compiler-error-c2884.md)|"*identyfikator*": wprowadzone za pomocą deklaracji Using powoduje konflikt z lokalną funkcją "*funkcja*"|  
|[C2885 błąd kompilatora](compiler-error-c2885.md)|"*klasy*::*identyfikator*": nie Nieprawidłowa deklaracja using w zakresie nieklasowym|  
|[C2886 błąd kompilatora](compiler-error-c2886.md)|"*klasy*::*identyfikator*": symbol nie można użyć w deklaracji elementu członkowskiego przy użyciu-|  
|C2887 błąd kompilatora|__swi lub __hvc nie może mieć więcej niż pięciu argumentów (liczba SWI, r0 – r3)|  
|[C2888 błąd kompilatora](compiler-error-c2888.md)|"*identyfikator*": symbol nie może być zdefiniowana w przestrzeni nazw "*przestrzeni nazw*"|  
|C2889 błąd kompilatora|"*klasy*": typ klasy managed WinRT nie może być wirtualną klasą podstawową|  
|[C2890 błąd kompilatora](compiler-error-c2890.md)|"*klasy*": klasa ref może mieć tylko jedną klasę podstawową niebędącą interfejsem|  
|[C2891 błąd kompilatora](compiler-error-c2891.md)|"*parametru*": nie można przyjąć adresu parametru szablonu|  
|[C2892 błąd kompilatora](compiler-error-c2892.md)|klasy lokalnej nie powinna posiadać szablonów elementu członkowskiego|  
|[C2893 błąd kompilatora](compiler-error-c2893.md)|Nie powiodła się specjalizacja szablonu funkcji '*szablonu*"|  
|[C2894 błąd kompilatora](compiler-error-c2894.md)|Nie można zadeklarować szablonów mieć powiązanie 'C'|  
|C2895 błąd kompilatora|"*deklaracji*": nie można jawnie utworzyć wystąpienia szablonu funkcji zadeklarowanej z dllimport|  
|[C2896 błąd kompilatora](compiler-error-c2896.md)|"*function1*": nie można użyć funkcji szablonu/ogólne "*function2*" jako argumentu funkcji|  
|[C2897 błąd kompilatora](compiler-error-c2897.md)|destruktor/finalizator nie może być szablonem funkcji|  
|[C2898 błąd kompilatora](compiler-error-c2898.md)|"*deklaracji*": Szablony funkcji Członkowskich nie może być wirtualny|  
|C2899 błąd kompilatora|Nieaktualne.|  
