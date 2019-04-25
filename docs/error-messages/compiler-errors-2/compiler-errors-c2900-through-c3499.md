---
title: Błędy kompilatora od C2900 do C2999
ms.date: 04/21/2019
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
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
ms.openlocfilehash: 5d443153582921775a72e5af647d65b102b80b0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281680"
---
# <a name="compiler-errors-c2900-through-c2999"></a>Błędy kompilatora od C2900 do C2999

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|Błąd kompilatora od C2900|"*deklaratora*": Szablony funkcji składowych w klasach WinRT musi być "private", "internal" lub "protected private"|
|Błąd kompilatora C2901|"*identyfikator*": Ogólny interfejs lub delegat nie może być publiczny|
|[Compiler error C2902](compiler-error-c2902.md)|"*tokenu*": nieoczekiwany token następujący "szablon/ogólne", oczekiwano identyfikatora|
|[Błąd kompilatora C2903](compiler-error-c2903.md)|"*identyfikator*": symbol nie jest szablon klasy/ogólnego ani funkcji szablonu/ogólne|
|[Błąd kompilatora C2904](compiler-error-c2904.md)|"*identyfikator*': nazwa już została użyta dla szablonu w bieżącym zakresie|
|Błąd kompilatora C2905|Nieaktualne.|
|[Compiler error C2906](compiler-error-c2906.md)|"*szablonu*": jawna specjalizacja wymaga "szablon <>"|
|Błąd kompilatora C2907|argument rejestru "*numer*" nie określa prawidłowy numer rejestru|
|[Compiler error C2908](compiler-error-c2908.md)|jawna specjalizacja; "*szablonu*" został już uruchomiony|
|[Compiler error C2909](compiler-error-c2909.md)|"*identyfikator*": jawne utworzenie wystąpienia szablonu funkcji wymaga typu zwracanego|
|[Błąd kompilatora C2910](compiler-error-c2910.md)|"*funkcja*": nie może być jawnie specjalizowany|
|[Błąd kompilatora C2911](compiler-error-c2911.md)|"*elementu członkowskiego*": nie może być zadeklarowane lub zdefiniowane w bieżącym zakresie|
|[Błąd kompilatora C2912](compiler-error-c2912.md)|jawna specjalizacja "*deklaracji*" nie jest specjalizacją szablonu funkcji|
|[Błąd kompilatora C2913](compiler-error-c2913.md)|jawna specjalizacja; "*deklaracji*" nie jest specjalizacją szablonu klasy|
|[Błąd kompilatora C2914](compiler-error-c2914.md)|"*identyfikator*": nie można wywnioskować argumentu szablonu/ogólne, gdyż argument funkcji jest niejednoznaczny|
|Błąd kompilatora C2915|"*identyfikator*": "*typu*" nie może być użyte bezpośrednio na publikowanej powierzchni typu WinRT. Użyj "Platform::Object ^" zamiast przekazywać ten typ|
|Błąd kompilatora C2916|"*identyfikator*": [FlagsAttribute] musi być określony (tylko) na publicznym typie wyliczeniowym z "unsigned int" typ podstawowy|
|[Błąd kompilatora C2917](compiler-error-c2917.md)|"*identyfikator*": nieprawidłowy parametr szablonu|
|[Błąd kompilatora C2918](compiler-error-c2918.md)|"*identyfikator*": Nie można używać właściwości indeksowanych na publikowanej powierzchni typu WinRT|
|[Błąd kompilatora C2919](compiler-error-c2919.md)|"*typu*": Nie można używać operatorów na publikowanej powierzchni typu WinRT|
|[Błąd kompilatora C2920](compiler-error-c2920.md)|Ponowna definicja: "*typu*": klasa szablonu/ogólne została już zadeklarowana jako*deklaracji*"|
|[Błąd kompilatora C2921](compiler-error-c2921.md)|Ponowna definicja: "*typu*": klasa szablonu/ogólne jest ponownie deklarowany jako*deklaracji*"|
|Błąd kompilatora C2922|"*interfejsu*": Interfejs WinRT nie może zawierać statycznych elementów członkowskich|
|[Błąd kompilatora C2923](compiler-error-c2923.md)|"*typu*": "*identyfikator*"nie jest prawidłowy szablon/ogólne, typ argumentu dla parametru"*parametr*"|
|Błąd kompilatora C2924|argument procedury __declspec(Interrupt) nie w R2|
|Błąd kompilatora C2925|Procedura __declspec(Interrupt) nie może używać liczb zmiennoprzecinkowych|
|Błąd kompilatora C2926|"*identyfikator*": domyślny inicjator składowej nie jest dozwolona dla składowej anonimowej struktury w obrębie Unii|
|[Błąd kompilatora C2927](compiler-error-c2927.md)|"*identyfikator*": szablon funkcji musi zostać wywołany z co najmniej jednego argumentu|
|[Błąd kompilatora C2928](compiler-error-c2928.md)|jawne wystąpienie; "*identyfikator*"nie jest funkcją lub statyczną składową danych szablonu klasy"*klasy*"|
|[Błąd kompilatora C2929](compiler-error-c2929.md)|"*deklaratora*": jawne utworzenie wystąpienia; nie można jawnie wymusić i ograniczyć utworzenia wystąpienia składowej klasy szablonu|
|[Błąd kompilatora C2930](compiler-error-c2930.md)|"*klasy*": szablon identyfikator/generic-id zostało ponownie zdefiniowane jako moduł wyliczający "enum *identyfikator*"|
|[Błąd kompilatora C2931](compiler-error-c2931.md)|"*klasa1*":-id/ogólne — identyfikator szablonu ponownie definiowana jako funkcji składowej typu "*klasa2*"|
|[Błąd kompilatora C2932](compiler-error-c2932.md)|"*typu*": szablon identyfikator/generic-id ponownie definiowana jako składowa danych klasy "*identyfikator*"|
|[Błąd kompilatora C2933](compiler-error-c2933.md)|"*typu*":-id/ogólne — identyfikator szablonu zostało ponownie zdefiniowane jako członek typedef "*identyfikator*"|
|[Błąd kompilatora C2934](compiler-error-c2934.md)|"*typu*": szablon identyfikator/generic-id zostało ponownie zdefiniowane jako zagnieżdżoną "*elementu*"z"*identyfikator*"|
|[Błąd kompilatora C2935](compiler-error-c2935.md)|"*typu*": szablon identyfikator/generic-id zostało ponownie zdefiniowane jako funkcję globalną|
|[Błąd kompilatora C2936](compiler-error-c2936.md)|"*typu*": szablon identyfikator/generic-id ponownie definiowana jako zmienna danych globalnych|
|[Błąd kompilatora C2937](compiler-error-c2937.md)|"*typu*": szablon identyfikator/generic-id ponownie definiowana jako globalne — typedef|
|Błąd kompilatora C2938|"*identyfikator*": Nie powiodło się specjalizowanie szablonu aliasu|
|[Błąd kompilatora C2939](compiler-error-c2939.md)|"*typu*":-id/ogólne — identyfikator szablonu ponownie definiowana jako zmienna danych lokalnych|
|[Błąd kompilatora C2940](compiler-error-c2940.md)|"*typu*":-id/ogólne — identyfikator szablonu ponownie definiowana jako lokalne — typedef|
|[Błąd kompilatora C2941](compiler-error-c2941.md)|"*typu*": szablon identyfikator/generic-id zostało ponownie zdefiniowane jako lokalną "*elementu*"|
|[Błąd kompilatora C2942](compiler-error-c2942.md)|"*typu*":-id/ogólne — identyfikator szablonu ponownie definiowana jako argument formalny funkcji|
|[Błąd kompilatora C2943](compiler-error-c2943.md)|"*typu*": szablon identyfikator/generic-id zostało ponownie zdefiniowane jako argument typu szablonu|
|[Błąd kompilatora C2944](compiler-error-c2944.md)|"*typu*": szablon identyfikator/generic-id ponownie definiowana jako wartość argumentu szablonu|
|[Błąd kompilatora C2945](compiler-error-c2945.md)|jawne utworzenie wystąpienia nie odnosi się do specjalizacji szablonu klasy|
|[Błąd kompilatora C2946](compiler-error-c2946.md)|jawne wystąpienie; "*typu*" nie jest specjalizacją szablonu klasy|
|[Błąd kompilatora C2947](compiler-error-c2947.md)|Oczekiwano ">" zakończenie argumentów szablonu, znaleziono "*tokenu*"|
|[Błąd kompilatora C2948](compiler-error-c2948.md)|jawne wystąpienie; Specyfikator klasy magazynu "*specyfikator*" nie jest dozwolona dla specjalizacji|
|Błąd kompilatora C2949|Element thread_local nie jest obsługiwany z/Kernel|
|Błąd kompilatora C2950|Nieaktualne.|
|[Compiler error C2951](compiler-error-c2951.md)|deklaracje szablonu/ogólne są dozwolone tylko w globalnym, przestrzeni nazw lub zakresie klasy|
|[Compiler error C2952](compiler-error-c2952.md)|"*deklaracji*": deklaracja szablonu/ogólne brakuje listy parametrów szablonu/ogólne|
|[Compiler error C2953](compiler-error-c2953.md)|"*typu*": szablon klasy została już zdefiniowana|
|Błąd kompilatora C2954|słowo argumentu instrukcji nie jest w zakresie|
|[Błąd kompilatora C2955](compiler-error-c2955.md)|"*typu*": użycie klasy szablonu/ogólne wymaga listy argumentów szablonu/ogólne|
|Błąd kompilatora C2956|powinny być wybierane wielkości dezalokacji funkcja "operator delete (void *, size_t)" jako funkcję dezalokacji umieszczania.|
|[Błąd kompilatora C2957](compiler-error-c2957.md)|"*tokenu*": Nieprawidłowy lewy ogranicznik: oczekiwano "<"|
|[Błąd kompilatora C2958](compiler-error-c2958.md)|po lewej stronie *ogranicznik* adrese "*pliku*(*line_number*)" nie został poprawnie dopasowany|
|[Błąd kompilatora C2959](compiler-error-c2959.md)|Ogólna klasa lub funkcja nie może być składowej szablonu|
|Błąd kompilatora C2960|Nieaktualne.|
|Błąd kompilatora C2961|"*funkcja*": niespójne jawne utworzenie wystąpień, poprzednie jawne utworzenie wystąpienia nie określiła "*argument*"|
|[Compiler error C2962](compiler-error-c2962.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji składowej klasy szablonu kończącej się znakiem "}"|
|Błąd kompilatora C2963|Nieaktualne.|
|Błąd kompilatora C2964|Nieaktualne.|
|Błąd kompilatora C2965|__declspec (*specyfikator*) nie jest obsługiwany z/Kernel|
|Błąd kompilatora C2966|"*identifier1*": musi mieć ten sam atrybut __declspec(code_seg(...)) jako swojej klasy bazowej*identifier2*"|
|Błąd kompilatora C2967|"*identyfikator*": przesłanianie funkcji wirtualnej musi mieć ten sam atrybut __declspec(code_seg(...)) jako przesłoniętej funkcji wirtualnych|
|Compiler error C2968|"*identyfikator*": deklaracja aliasu rekursywnego|
|[Compiler error C2969](compiler-error-c2969.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji składowej kończącej się znakiem "}"|
|[Błąd kompilatora C2970](compiler-error-c2970.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": wyrażenie obejmujące obiekty z wewnętrznym powiązaniem nie można użyć jako argument bez typu|
|[Błąd kompilatora C2971](compiler-error-c2971.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": zmienna z okresem magazynu niestatycznych nie można użyć jako argument bez typu|
|Błąd kompilatora C2972|"*typu*": parametr szablonu "*parametr*": typ argumentu bez typu jest nieprawidłowy|
|[Błąd kompilatora C2973](compiler-error-c2973.md)|"*szablonu*": nieprawidłowy argument szablonu "*numer*"|
|[Błąd kompilatora C2974](compiler-error-c2974.md)|"*typu*": argument szablonu nieprawidłowy/ogólne "*parametr*", oczekiwano typu|
|[Błąd kompilatora C2975](compiler-error-c2975.md)|"*typu*": nieprawidłowy argument szablonu dla "*parametr*", oczekiwano stałego wyrażenia czasu kompilacji|
|[Błąd kompilatora C2976](compiler-error-c2976.md)|"*typu*": zbyt mało argumentów szablonu/ogólne|
|[Błąd kompilatora C2977](compiler-error-c2977.md)|"*typu*": zbyt wiele argumentów szablonu/ogólne|
|[Błąd kompilatora C2978](compiler-error-c2978.md)|Błąd składniowy: oczekiwano "*keyword1*"lub"*keyword2*"; znaleziono typ"*typu*"; -type parametry nie są obsługiwane w typach ogólnych|
|[Błąd kompilatora C2979](compiler-error-c2979.md)|jawne specjalizacje nie są obsługiwane w typach ogólnych|
|Błąd kompilatora C2980|Obsługa wyjątków języka C++ nie jest obsługiwany z/Kernel|
|Błąd kompilatora C2981|dynamiczny formularz "*— słowo kluczowe*" nie jest obsługiwany z/Kernel|
|Błąd kompilatora C2982|"*deklaracji*": użyto innego __declspec(code_seg(...)): został "*identifier1*"teraz"*identifier2*"|
|Błąd kompilatora C2983|"*deklaracji*": wszystkie deklaracje muszą mieć identyczne __declspec(code_seg(...))|
|Błąd kompilatora C2984|Nieaktualne.|
|Błąd kompilatora C2985|"*argument*": argument dla __declspec(code_seg(...)) musi być sekcją tekstu|
|Błąd kompilatora C2986|"*identyfikator*": __declspec(code_seg(...)) będzie stosowany tylko do klasy lub funkcji|
|Błąd kompilatora C2987|Deklaracja nie może mieć zarówno __declspec (code_seg ("*identyfikator*")) i __declspec (code_seg ("*wartość*"))|
|[Błąd kompilatora C2988](compiler-error-c2988.md)|Deklaracja/definicja szablonu nierozpoznawalną|
|[Compiler error C2989](compiler-error-c2989.md)|"*klasy*": klasa szablonu/ogólne została już zadeklarowana jako szablon/ogólnej klasy korporacyjnej|
|[Błąd kompilatora C2990](compiler-error-c2990.md)|"*klasy*": klasy korporacyjnej szablonu/ogólne został już zadeklarowany jako klasa szablonu/ogólne|
|[Compiler error C2991](compiler-error-c2991.md)|Ponowna definicja parametru szablonu/ogólne "*parametr*"|
|[Błąd kompilatora C2992](compiler-error-c2992.md)|"*klasy*": szablon/ogólne nieprawidłowa lub brakująca lista parametrów|
|[Błąd kompilatora C2993](compiler-error-c2993.md)|"*typu*": niedozwolony typ dla parametru szablonu bez typu "*identyfikator*"|
|[Błąd kompilatora C2994](compiler-error-c2994.md)|Klasa bez nazwy na liście parametrów szablonu|
|[Błąd kompilatora C2995](compiler-error-c2995.md)|"*deklaracji*": szablon funkcji został już zdefiniowany|
|[Compiler error C2996](compiler-error-c2996.md)|"*funkcja*": definicja szablonu funkcji cyklicznej|
|Błąd kompilatora C2997|"*funkcja*": granica tablicy nie można wywnioskować z domyślny inicjator składowej|
|[Compiler error C2998](compiler-error-c2998.md)|"*deklaratora*": nie może być definicją szablonu|
|Błąd kompilatora C2999|Nieznany błąd, wybierz polecenie Pomoc techniczna w Visual C++ menu Pomoc lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
