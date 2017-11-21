---
title: "C2900 błędy kompilatora za pośrednictwem C2999 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
helpviewer_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
dev_langs: C++
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 535a1d42d9d43022bbf513b72bac18dd5accad82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2900-through-c2999"></a>C2900 błędy kompilatora za pośrednictwem C2999
Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.  
  
> [!NOTE]
>  Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).  
  
|Błąd|Komunikat|  
|-----------|-------------|  
|C2900 błąd kompilatora|"*deklarator*": Szablony funkcji Członkowskich w klasach WinRT musi być "private", "internal" lub "protected private"|  
|C2901 błąd kompilatora|"*identyfikator*": ogólny interfejs lub delegat nie może być publiczny|  
|[C2902 błąd kompilatora](compiler-error-c2902.md)|"*tokenu*": nieoczekiwany token następujący "szablonu/ogólne", oczekiwano identyfikatora|  
|[C2903 błąd kompilatora](compiler-error-c2903.md)|"*identyfikator*": symbol nie jest szablon klasy/ogólnego ani funkcja szablonu/ogólnego|  
|[C2904 błąd kompilatora](compiler-error-c2904.md)|"*identyfikator*": nazwa już została użyta dla szablonu w bieżącym zakresie|  
|C2905 błąd kompilatora|Nieaktualne.|  
|[C2906 błąd kompilatora](compiler-error-c2906.md)|"*szablonu*": jawna specjalizacja wymaga "szablonu <>"|  
|C2907 błąd kompilatora|argument rejestru "*numer*" nie został określony prawidłowy numer rejestru|  
|[C2908 błąd kompilatora](compiler-error-c2908.md)|jawna specjalizacja; "*szablonu*" utworzono już wystąpienie|  
|[C2909 błąd kompilatora](compiler-error-c2909.md)|"*identyfikator*": jawne utworzenie wystąpienia szablonu funkcji wymaga typu zwracanego|  
|[C2910 błąd kompilatora](compiler-error-c2910.md)|"*funkcja*": nie może być jawnie specjalizowany|  
|[C2911 błąd kompilatora](compiler-error-c2911.md)|"*elementu członkowskiego*": nie może być zadeklarowane lub zdefiniowane w bieżącym zakresie|  
|[C2912 błąd kompilatora](compiler-error-c2912.md)|jawna specjalizacja "*deklaracji*" nie jest specjalizacją szablonu funkcji|  
|[C2913 błąd kompilatora](compiler-error-c2913.md)|jawna specjalizacja; "*deklaracji*" nie jest specjalizacją szablonu klasy|  
|[C2914 błąd kompilatora](compiler-error-c2914.md)|"*identyfikator*": nie można wywnioskować argumentu szablonu/ogólny jako argument funkcji jest niejednoznaczny|  
|C2915 błąd kompilatora|"*identyfikator*": "*typu*" nie może być użyte bezpośrednio na publikowanej powierzchni typu WinRT. Użyj "Platform::Object ^" zamiast przekazywać ten typ|  
|C2916 błąd kompilatora|"*identyfikator*': [FlagsAttribute] (tylko) muszą być określone na publicznym typie wyliczeniowym z typ podstawowy"unsigned int"|  
|[C2917 błąd kompilatora](compiler-error-c2917.md)|"*identyfikator*": nieprawidłowy parametr szablonu|  
|[C2918 błąd kompilatora](compiler-error-c2918.md)|"*identyfikator*": nie można używać właściwości indeksowanych na publikowanej powierzchni typu WinRT|  
|[C2919 błąd kompilatora](compiler-error-c2919.md)|"*typu*": nie można używać operatorów na publikowanej powierzchni typu WinRT|  
|[C2920 błąd kompilatora](compiler-error-c2920.md)|Ponowna definicja: "*typu*": klasa szablonu/ogólny został już zadeklarowany jako*deklaracji*"|  
|[C2921 błąd kompilatora](compiler-error-c2921.md)|Ponowna definicja: "*typu*": klasa szablonu/rodzajowa jest ponownie deklarowany jako*deklaracji*"|  
|C2922 błąd kompilatora|"*interfejsu*": interfejs WinRT nie może zawierać elementów statycznych|  
|[C2923 błąd kompilatora](compiler-error-c2923.md)|"*typu*": "*identyfikator*"nie jest prawidłowy szablon/ogólny typ argumentu dla parametru"*parametru*"|  
|C2924 błąd kompilatora|argument procedury __declspec(Interrupt) nie znajduje się w R2|  
|C2925 błąd kompilatora|Procedura __declspec(Interrupt) nie może używać liczb zmiennoprzecinkowych|  
|C2926 błąd kompilatora|"*identyfikator*": Inicjator elementu członkowskiego domyślnego nie jest dozwolona dla elementu członkowskiego struktury anonimowe w obrębie elementu union|  
|[C2927 błąd kompilatora](compiler-error-c2927.md)|"*identyfikator*": szablon funkcji musi zostać wywołany z co najmniej jeden argument|  
|[C2928 błąd kompilatora](compiler-error-c2928.md)|jawne utworzenie wystąpienia; "*identyfikator*"nie jest funkcją lub statyczny elementem członkowskim danych szablonu klasy"*klasy*"|  
|[C2929 błąd kompilatora](compiler-error-c2929.md)|"*deklarator*": jawne utworzenie wystąpienia; nie można jawnie wymusić i ograniczyć utworzenia wystąpienia elementu członkowskiego szablonu klasy|  
|[C2930 błąd kompilatora](compiler-error-c2930.md)|"*klasy*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako moduł wyliczający "enum *identyfikator*"|  
|[C2931 błąd kompilatora](compiler-error-c2931.md)|"*class1*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako funkcję elementu członkowskiego "*class2*"|  
|[C2932 błąd kompilatora](compiler-error-c2932.md)|"*typu*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako element członkowski danych klasy "*identyfikator*"|  
|[C2933 błąd kompilatora](compiler-error-c2933.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako element członkowski typedef "*identyfikator*"|  
|[C2934 błąd kompilatora](compiler-error-c2934.md)|"*typu*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako zagnieżdżoną "*elementu*"od"*identyfikator*"|  
|[C2935 błąd kompilatora](compiler-error-c2935.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako funkcję globalną|  
|[C2936 błąd kompilatora](compiler-error-c2936.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako globalną zmienną danych|  
|[C2937 błąd kompilatora](compiler-error-c2937.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako globalny typedef|  
|C2938 błąd kompilatora|"*identyfikator*": nie powiodło się specjalizowanie szablonu aliasu|  
|[C2939 błąd kompilatora](compiler-error-c2939.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako lokalną zmienną danych|  
|[C2940 błąd kompilatora](compiler-error-c2940.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako lokalny typedef|  
|[C2941 błąd kompilatora](compiler-error-c2941.md)|"*typu*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako lokalny "*elementu*"|  
|[C2942 błąd kompilatora](compiler-error-c2942.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako formalny argument funkcji|  
|[C2943 błąd kompilatora](compiler-error-c2943.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako argument typu szablonu|  
|[C2944 błąd kompilatora](compiler-error-c2944.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako wartość argumentu szablonu|  
|[C2945 błąd kompilatora](compiler-error-c2945.md)|jawne utworzenie wystąpienia nie odnosi się do specjalizacji szablonu klasy|  
|[C2946 błąd kompilatora](compiler-error-c2946.md)|jawne utworzenie wystąpienia; "*typu*" nie jest specjalizacją szablonu klasy|  
|[C2947 błąd kompilatora](compiler-error-c2947.md)|Oczekiwano znaku ">" zakończenie argumentów szablonu, znaleziono "*tokenu*"|  
|[C2948 błąd kompilatora](compiler-error-c2948.md)|jawne utworzenie wystąpienia; Specyfikator klasy magazynu "*specyfikator*" nie jest dozwolone dla specjalizacji|  
|C2949 błąd kompilatora|Element thread_local nie jest obsługiwany z/Kernel|  
|C2950 błąd kompilatora|Nieaktualne.|  
|[C2951 błąd kompilatora](compiler-error-c2951.md)|deklaracje szablonu/ogólne są dozwolone tylko w globalnej, przestrzeni nazw lub zakresie klasy|  
|[C2952 błąd kompilatora](compiler-error-c2952.md)|"*deklaracji*": Brak listy parametrów szablonu/generic deklaracji szablonu/generic|  
|[C2953 błąd kompilatora](compiler-error-c2953.md)|"*typu*": szablon klasy została już zdefiniowana.|  
|C2954 błąd kompilatora|słowo argumentu instrukcji nie jest w zakresie|  
|[C2955 błąd kompilatora](compiler-error-c2955.md)|"*typu*": użycie klasy szablonu/generic wymaga listy argumentów szablonu/generic|  
|C2956 błąd kompilatora|cofania alokacji o rozmiarze funkcja "operator delete (void *, size_t)" zostałaby wybrana jako funkcja cofania alokacji położenia.|  
|[C2957 błąd kompilatora](compiler-error-c2957.md)|"*tokenu*": Nieprawidłowy lewy ogranicznik: oczekiwano "<"|  
|[C2958 błąd kompilatora](compiler-error-c2958.md)|po lewej stronie *ogranicznik* znaleźć pod adresem "*pliku*(*line_number*)" nie został poprawnie dopasowany|  
|[C2959 błąd kompilatora](compiler-error-c2959.md)|Klasa generyczna lub funkcja nie może być elementem członkowskim szablonu|  
|C2960 błąd kompilatora|Nieaktualne.|  
|C2961 błąd kompilatora|"*funkcja*": niespójne jawne utworzenie wystąpień, poprzednie jawne utworzenie wystąpienia nie określa "*argument*"|  
|[C2962 błąd kompilatora](compiler-error-c2962.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji członkowskiej klasy szablonu kończącej się "}"|  
|C2963 błąd kompilatora|Nieaktualne.|  
|C2964 błąd kompilatora|Nieaktualne.|  
|C2965 błąd kompilatora|__declspec (*specyfikator*) nie jest obsługiwany z/Kernel|  
|C2966 błąd kompilatora|"*identifier1*": muszą mieć ten sam __declspec(code_seg(...)) jako jego klasę podstawową*identifier2*"|  
|C2967 błąd kompilatora|"*identyfikator*": przesłanianie wirtualnej funkcji musi mieć ten sam __declspec(code_seg(...)) jako przesłoniętą wirtualną funkcję|  
|C2968 błąd kompilatora|"*identyfikator*": deklaracja aliasu rekursywnego|  
|[C2969 błąd kompilatora](compiler-error-c2969.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji członkowskiej kończącej się "}"|  
|[C2970 błąd kompilatora](compiler-error-c2970.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": wyrażenie obejmujące obiekty z wewnętrznym powiązaniem nie można użyć jako argument bez typu|  
|[C2971 błąd kompilatora](compiler-error-c2971.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": zmienna z okresem magazynu niestatyczna nie można użyć jako argument bez typu|  
|C2972 błąd kompilatora|"*typu*": parametr szablonu "*parametru*": typ argumentu bez typu jest nieprawidłowa|  
|[C2973 błąd kompilatora](compiler-error-c2973.md)|"*szablonu*": nieprawidłowy argument szablonu "*numer*"|  
|[C2974 błąd kompilatora](compiler-error-c2974.md)|"*typu*": argument nieprawidłowy szablon/ogólne "*parametru*", oczekiwano typu|  
|[C2975 błąd kompilatora](compiler-error-c2975.md)|"*typu*": nieprawidłowy argument szablonu dla "*parametru*", oczekiwano stałego wyrażenia czasu kompilacji|  
|[C2976 błąd kompilatora](compiler-error-c2976.md)|"*typu*": zbyt mało argumentów szablonu/generic|  
|[C2977 błąd kompilatora](compiler-error-c2977.md)|"*typu*": zbyt wiele argumentów szablonu/generic|  
|[C2978 błąd kompilatora](compiler-error-c2978.md)|Błąd składniowy: oczekiwano "*keyword1*"lub"*keyword2*"; znaleziono typ"*typu*'; typ innych niż parametry nie są obsługiwane w typach ogólnych|  
|[C2979 błąd kompilatora](compiler-error-c2979.md)|jawne specjalizacje nie są obsługiwane w typach ogólnych|  
|C2980 błąd kompilatora|C++, obsługa wyjątków nie jest obsługiwany z/Kernel|  
|C2981 błąd kompilatora|dynamiczny formularz "*— słowo kluczowe*" nie jest obsługiwany z/Kernel|  
|C2982 błąd kompilatora|"*deklaracji*": użyto innego __declspec(code_seg(...)): został "*identifier1*"teraz"*identifier2*"|  
|C2983 błąd kompilatora|"*deklaracji*": wszystkie deklaracje muszą posiadać identyczne __declspec(code_seg(...))|  
|C2984 błąd kompilatora|Nieaktualne.|  
|C2985 błąd kompilatora|"*argument*": argument dla __declspec(code_seg(...)) musi być sekcją tekstu|  
|C2986 błąd kompilatora|"*identyfikator*": __declspec(code_seg(...)) można stosować do klasy lub funkcji|  
|C2987 błąd kompilatora|Deklaracja nie może mieć obu __declspec (code_seg ("*identyfikator*")) i __declspec (code_seg ("*wartość*"))|  
|[C2988 błąd kompilatora](compiler-error-c2988.md)|Deklaracja/definicja szablonu nierozpoznawalną|  
|[C2989 błąd kompilatora](compiler-error-c2989.md)|"*klasy*": klasy szablonu/ogólny został już zadeklarowany jako szablon bez klasy/ogólnego|  
|[C2990 błąd kompilatora](compiler-error-c2990.md)|"*klasy*": klasy szablonu/ogólny został już zadeklarowany jako szablon klasy/ogólnego|  
|[C2991 błąd kompilatora](compiler-error-c2991.md)|Ponowna definicja parametru szablonu/ogólne "*parametru*"|  
|[C2992 błąd kompilatora](compiler-error-c2992.md)|"*klasy*": nieprawidłowy lub brakujący ogólny/szablonu listy parametrów|  
|[C2993 błąd kompilatora](compiler-error-c2993.md)|"*typu*": niedozwolony typ dla parametru szablonu bez typu "*identyfikator*"|  
|[C2994 błąd kompilatora](compiler-error-c2994.md)|Klasa bez nazwy na liście parametrów szablonu|  
|[C2995 błąd kompilatora](compiler-error-c2995.md)|"*deklaracji*": szablon funkcji został już zdefiniowany.|  
|[C2996 błąd kompilatora](compiler-error-c2996.md)|"*funkcja*": definicja szablonu funkcji cyklicznej|  
|C2997 błąd kompilatora|"*funkcja*": granica tablicy nie można wywnioskować z domyślnego inicjator elementu członkowskiego|  
|[C2998 błąd kompilatora](compiler-error-c2998.md)|"*deklarator*": nie może być definicją szablonu|  
|C2999 błąd kompilatora|Nieznany błąd wybierz polecenie Pomoc techniczna w menu Pomoc programu Visual C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|  
