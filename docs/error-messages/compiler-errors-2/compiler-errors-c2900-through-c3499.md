---
title: "C2900 błędy kompilatora za pośrednictwem C2999 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
dev_langs:
- C++
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b5e2711b8517a03792cdef312e8cd8ee3b4fe72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c2900-through-c2999"></a>C2900 błędy kompilatora za pośrednictwem C2999

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|C2900 błąd kompilatora|"*deklarator*": Szablony funkcji Członkowskich w klasach WinRT musi być "private", "internal" lub "protected private"|
|C2901 błąd kompilatora|"*identyfikator*": ogólny interfejs lub delegat nie może być publiczny|
|[Błąd kompilatora C2902](compiler-error-c2902.md)|"*tokenu*": nieoczekiwany token następujący "szablonu/ogólne", oczekiwano identyfikatora|
|[Błąd kompilatora C2903](compiler-error-c2903.md)|"*identyfikator*": symbol nie jest szablon klasy/ogólnego ani funkcja szablonu/ogólnego|
|[Błąd kompilatora C2904](compiler-error-c2904.md)|"*identyfikator*": nazwa już została użyta dla szablonu w bieżącym zakresie|
|C2905 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2906](compiler-error-c2906.md)|"*szablonu*": jawna specjalizacja wymaga "szablonu <>"|
|C2907 błąd kompilatora|argument rejestru "*numer*" nie został określony prawidłowy numer rejestru|
|[Błąd kompilatora C2908](compiler-error-c2908.md)|jawna specjalizacja; "*szablonu*" utworzono już wystąpienie|
|[Błąd kompilatora C2909](compiler-error-c2909.md)|"*identyfikator*": jawne utworzenie wystąpienia szablonu funkcji wymaga typu zwracanego|
|[Błąd kompilatora C2910](compiler-error-c2910.md)|"*funkcja*": nie może być jawnie specjalizowany|
|[Błąd kompilatora C2911](compiler-error-c2911.md)|"*elementu członkowskiego*": nie może być zadeklarowane lub zdefiniowane w bieżącym zakresie|
|[Błąd kompilatora C2912](compiler-error-c2912.md)|jawna specjalizacja "*deklaracji*" nie jest specjalizacją szablonu funkcji|
|[Błąd kompilatora C2913](compiler-error-c2913.md)|jawna specjalizacja; "*deklaracji*" nie jest specjalizacją szablonu klasy|
|[Błąd kompilatora C2914](compiler-error-c2914.md)|"*identyfikator*": nie można wywnioskować argumentu szablonu/ogólny jako argument funkcji jest niejednoznaczny|
|C2915 błąd kompilatora|"*identyfikator*": "*typu*" nie może być użyte bezpośrednio na publikowanej powierzchni typu WinRT. Użyj "Platform::Object ^" zamiast przekazywać ten typ|
|C2916 błąd kompilatora|"*identyfikator*': [FlagsAttribute] \(tylko) muszą być określone na publicznym typie wyliczeniowym z typ podstawowy"unsigned int"|
|[Błąd kompilatora C2917](compiler-error-c2917.md)|"*identyfikator*": nieprawidłowy parametr szablonu|
|[Błąd kompilatora C2918](compiler-error-c2918.md)|"*identyfikator*": nie można używać właściwości indeksowanych na publikowanej powierzchni typu WinRT|
|[Błąd kompilatora C2919](compiler-error-c2919.md)|"*typu*": nie można używać operatorów na publikowanej powierzchni typu WinRT|
|[Błąd kompilatora C2920](compiler-error-c2920.md)|Ponowna definicja: "*typu*": klasa szablonu/ogólny został już zadeklarowany jako*deklaracji*"|
|[Błąd kompilatora C2921](compiler-error-c2921.md)|Ponowna definicja: "*typu*": klasa szablonu/rodzajowa jest ponownie deklarowany jako*deklaracji*"|
|C2922 błąd kompilatora|"*interfejsu*": interfejs WinRT nie może zawierać elementów statycznych|
|[Błąd kompilatora C2923](compiler-error-c2923.md)|"*typu*": "*identyfikator*"nie jest prawidłowy szablon/ogólny typ argumentu dla parametru"*parametru*"|
|C2924 błąd kompilatora|argument procedury __declspec(Interrupt) nie znajduje się w R2|
|C2925 błąd kompilatora|Procedura __declspec(Interrupt) nie może używać liczb zmiennoprzecinkowych|
|C2926 błąd kompilatora|"*identyfikator*": Inicjator elementu członkowskiego domyślnego nie jest dozwolona dla elementu członkowskiego struktury anonimowe w obrębie elementu union|
|[Błąd kompilatora C2927](compiler-error-c2927.md)|"*identyfikator*": szablon funkcji musi zostać wywołany z co najmniej jeden argument|
|[Błąd kompilatora C2928](compiler-error-c2928.md)|jawne utworzenie wystąpienia; "*identyfikator*"nie jest funkcją lub statyczny elementem członkowskim danych szablonu klasy"*klasy*"|
|[Błąd kompilatora C2929](compiler-error-c2929.md)|"*deklarator*": jawne utworzenie wystąpienia; nie można jawnie wymusić i ograniczyć utworzenia wystąpienia elementu członkowskiego szablonu klasy|
|[Błąd kompilatora C2930](compiler-error-c2930.md)|"*klasy*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako moduł wyliczający "enum *identyfikator*"|
|[Błąd kompilatora C2931](compiler-error-c2931.md)|"*class1*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako funkcję elementu członkowskiego "*class2*"|
|[Błąd kompilatora C2932](compiler-error-c2932.md)|"*typu*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako element członkowski danych klasy "*identyfikator*"|
|[Błąd kompilatora C2933](compiler-error-c2933.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako element członkowski typedef "*identyfikator*"|
|[Błąd kompilatora C2934](compiler-error-c2934.md)|"*typu*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako zagnieżdżoną "*elementu*"od"*identyfikator*"|
|[Błąd kompilatora C2935](compiler-error-c2935.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako funkcję globalną|
|[Błąd kompilatora C2936](compiler-error-c2936.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako globalną zmienną danych|
|[Błąd kompilatora C2937](compiler-error-c2937.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako globalny typedef|
|C2938 błąd kompilatora|"*identyfikator*": nie powiodło się specjalizowanie szablonu aliasu|
|[Błąd kompilatora C2939](compiler-error-c2939.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako lokalną zmienną danych|
|[Błąd kompilatora C2940](compiler-error-c2940.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako lokalny typedef|
|[Błąd kompilatora C2941](compiler-error-c2941.md)|"*typu*": identyfikator/generic — identyfikator szablonu ponownie zdefiniować jako lokalny "*elementu*"|
|[Błąd kompilatora C2942](compiler-error-c2942.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako formalny argument funkcji|
|[Błąd kompilatora C2943](compiler-error-c2943.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako argument typu szablonu|
|[Błąd kompilatora C2944](compiler-error-c2944.md)|"*typu*": przedefiniowano identyfikator/generic — identyfikator szablonu jako wartość argumentu szablonu|
|[Błąd kompilatora C2945](compiler-error-c2945.md)|jawne utworzenie wystąpienia nie odnosi się do specjalizacji szablonu klasy|
|[Błąd kompilatora C2946](compiler-error-c2946.md)|jawne utworzenie wystąpienia; "*typu*" nie jest specjalizacją szablonu klasy|
|[Błąd kompilatora C2947](compiler-error-c2947.md)|Oczekiwano znaku ">" zakończenie argumentów szablonu, znaleziono "*tokenu*"|
|[Błąd kompilatora C2948](compiler-error-c2948.md)|jawne utworzenie wystąpienia; Specyfikator klasy magazynu "*specyfikator*" nie jest dozwolone dla specjalizacji|
|C2949 błąd kompilatora|Element thread_local nie jest obsługiwany z/Kernel|
|C2950 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2951](compiler-error-c2951.md)|deklaracje szablonu/ogólne są dozwolone tylko w globalnej, przestrzeni nazw lub zakresie klasy|
|[Błąd kompilatora C2952](compiler-error-c2952.md)|"*deklaracji*": Brak listy parametrów szablonu/generic deklaracji szablonu/generic|
|[Błąd kompilatora C2953](compiler-error-c2953.md)|"*typu*": szablon klasy została już zdefiniowana.|
|C2954 błąd kompilatora|słowo argumentu instrukcji nie jest w zakresie|
|[Błąd kompilatora C2955](compiler-error-c2955.md)|"*typu*": użycie klasy szablonu/generic wymaga listy argumentów szablonu/generic|
|C2956 błąd kompilatora|cofania alokacji o rozmiarze funkcja "operator delete (void *, size_t)" zostałaby wybrana jako funkcja cofania alokacji położenia.|
|[Błąd kompilatora C2957](compiler-error-c2957.md)|"*tokenu*": Nieprawidłowy lewy ogranicznik: oczekiwano "<"|
|[Błąd kompilatora C2958](compiler-error-c2958.md)|po lewej stronie *ogranicznik* znaleźć pod adresem "*pliku*(*line_number*)" nie został poprawnie dopasowany|
|[Błąd kompilatora C2959](compiler-error-c2959.md)|Klasa generyczna lub funkcja nie może być elementem członkowskim szablonu|
|C2960 błąd kompilatora|Nieaktualne.|
|C2961 błąd kompilatora|"*funkcja*": niespójne jawne utworzenie wystąpień, poprzednie jawne utworzenie wystąpienia nie określa "*argument*"|
|[Błąd kompilatora C2962](compiler-error-c2962.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji członkowskiej klasy szablonu kończącej się "}"|
|C2963 błąd kompilatora|Nieaktualne.|
|C2964 błąd kompilatora|Nieaktualne.|
|C2965 błąd kompilatora|__declspec (*specyfikator*) nie jest obsługiwany z/Kernel|
|C2966 błąd kompilatora|"*identifier1*": muszą mieć ten sam __declspec(code_seg(...)) jako jego klasę podstawową*identifier2*"|
|C2967 błąd kompilatora|"*identyfikator*": przesłanianie wirtualnej funkcji musi mieć ten sam __declspec(code_seg(...)) jako przesłoniętą wirtualną funkcję|
|C2968 błąd kompilatora|"*identyfikator*": deklaracja aliasu rekursywnego|
|[Błąd kompilatora C2969](compiler-error-c2969.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji członkowskiej kończącej się "}"|
|[Błąd kompilatora C2970](compiler-error-c2970.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": wyrażenie obejmujące obiekty z wewnętrznym powiązaniem nie można użyć jako argument bez typu|
|[Błąd kompilatora C2971](compiler-error-c2971.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": zmienna z okresem magazynu niestatyczna nie można użyć jako argument bez typu|
|C2972 błąd kompilatora|"*typu*": parametr szablonu "*parametru*": typ argumentu bez typu jest nieprawidłowa|
|[Błąd kompilatora C2973](compiler-error-c2973.md)|"*szablonu*": nieprawidłowy argument szablonu "*numer*"|
|[Błąd kompilatora C2974](compiler-error-c2974.md)|"*typu*": argument nieprawidłowy szablon/ogólne "*parametru*", oczekiwano typu|
|[Błąd kompilatora C2975](compiler-error-c2975.md)|"*typu*": nieprawidłowy argument szablonu dla "*parametru*", oczekiwano stałego wyrażenia czasu kompilacji|
|[Błąd kompilatora C2976](compiler-error-c2976.md)|"*typu*": zbyt mało argumentów szablonu/generic|
|[Błąd kompilatora C2977](compiler-error-c2977.md)|"*typu*": zbyt wiele argumentów szablonu/generic|
|[Błąd kompilatora C2978](compiler-error-c2978.md)|Błąd składniowy: oczekiwano "*keyword1*"lub"*keyword2*"; znaleziono typ"*typu*'; typ innych niż parametry nie są obsługiwane w typach ogólnych|
|[Błąd kompilatora C2979](compiler-error-c2979.md)|jawne specjalizacje nie są obsługiwane w typach ogólnych|
|C2980 błąd kompilatora|C++, obsługa wyjątków nie jest obsługiwany z/Kernel|
|C2981 błąd kompilatora|dynamiczny formularz "*— słowo kluczowe*" nie jest obsługiwany z/Kernel|
|C2982 błąd kompilatora|"*deklaracji*": użyto innego __declspec(code_seg(...)): został "*identifier1*"teraz"*identifier2*"|
|C2983 błąd kompilatora|"*deklaracji*": wszystkie deklaracje muszą posiadać identyczne __declspec(code_seg(...))|
|C2984 błąd kompilatora|Nieaktualne.|
|C2985 błąd kompilatora|"*argument*": argument dla __declspec(code_seg(...)) musi być sekcją tekstu|
|C2986 błąd kompilatora|"*identyfikator*": __declspec(code_seg(...)) można stosować do klasy lub funkcji|
|C2987 błąd kompilatora|Deklaracja nie może mieć obu __declspec (code_seg ("*identyfikator*")) i __declspec (code_seg ("*wartość*"))|
|[Błąd kompilatora C2988](compiler-error-c2988.md)|Deklaracja/definicja szablonu nierozpoznawalną|
|[Błąd kompilatora C2989](compiler-error-c2989.md)|"*klasy*": klasy szablonu/ogólny został już zadeklarowany jako szablon bez klasy/ogólnego|
|[Błąd kompilatora C2990](compiler-error-c2990.md)|"*klasy*": klasy szablonu/ogólny został już zadeklarowany jako szablon klasy/ogólnego|
|[Błąd kompilatora C2991](compiler-error-c2991.md)|Ponowna definicja parametru szablonu/ogólne "*parametru*"|
|[Błąd kompilatora C2992](compiler-error-c2992.md)|"*klasy*": nieprawidłowy lub brakujący ogólny/szablonu listy parametrów|
|[Błąd kompilatora C2993](compiler-error-c2993.md)|"*typu*": niedozwolony typ dla parametru szablonu bez typu "*identyfikator*"|
|[Błąd kompilatora C2994](compiler-error-c2994.md)|Klasa bez nazwy na liście parametrów szablonu|
|[Błąd kompilatora C2995](compiler-error-c2995.md)|"*deklaracji*": szablon funkcji został już zdefiniowany.|
|[Błąd kompilatora C2996](compiler-error-c2996.md)|"*funkcja*": definicja szablonu funkcji cyklicznej|
|C2997 błąd kompilatora|"*funkcja*": granica tablicy nie można wywnioskować z domyślnego inicjator elementu członkowskiego|
|[Błąd kompilatora C2998](compiler-error-c2998.md)|"*deklarator*": nie może być definicją szablonu|
|C2999 błąd kompilatora|Nieznany błąd wybierz polecenie Pomoc techniczna w menu Pomoc programu Visual C++ lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
