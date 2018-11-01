---
title: Błędy kompilatora od C2900 C2999
ms.date: 11/17/2017
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
ms.openlocfilehash: 4d430d1d446147c662f7f6405185aee75d95bc0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466901"
---
# <a name="compiler-errors-c2900-through-c2999"></a>Błędy kompilatora od C2900 C2999

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|Kompilatora od C2900 do błędu|"*deklaratora*": Szablony funkcji składowych w klasach WinRT musi być "private", "internal" lub "protected private"|
|C2901 błąd kompilatora|"*identyfikator*": ogólny interfejs lub delegat nie może być publiczny|
|[Błąd kompilatora C2902](compiler-error-c2902.md)|"*tokenu*": nieoczekiwany token następujący "szablon/ogólne", oczekiwano identyfikatora|
|[Błąd kompilatora C2903](compiler-error-c2903.md)|"*identyfikator*": symbol nie jest szablon klasy/ogólnego ani funkcji szablonu/ogólne|
|[Błąd kompilatora C2904](compiler-error-c2904.md)|"*identyfikator*': nazwa już została użyta dla szablonu w bieżącym zakresie|
|C2905 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2906](compiler-error-c2906.md)|"*szablonu*": jawna specjalizacja wymaga "szablon <>"|
|C2907 błąd kompilatora|argument rejestru "*numer*" nie określa prawidłowy numer rejestru|
|[Błąd kompilatora C2908](compiler-error-c2908.md)|jawna specjalizacja; "*szablonu*" został już uruchomiony|
|[Błąd kompilatora C2909](compiler-error-c2909.md)|"*identyfikator*": jawne utworzenie wystąpienia szablonu funkcji wymaga typu zwracanego|
|[Błąd kompilatora C2910](compiler-error-c2910.md)|"*funkcja*": nie może być jawnie specjalizowany|
|[Błąd kompilatora C2911](compiler-error-c2911.md)|"*elementu członkowskiego*": nie może być zadeklarowane lub zdefiniowane w bieżącym zakresie|
|[Błąd kompilatora C2912](compiler-error-c2912.md)|jawna specjalizacja "*deklaracji*" nie jest specjalizacją szablonu funkcji|
|[Błąd kompilatora C2913](compiler-error-c2913.md)|jawna specjalizacja; "*deklaracji*" nie jest specjalizacją szablonu klasy|
|[Błąd kompilatora C2914](compiler-error-c2914.md)|"*identyfikator*": nie można wywnioskować argumentu szablonu/ogólne, gdyż argument funkcji jest niejednoznaczny|
|C2915 błąd kompilatora|"*identyfikator*": "*typu*" nie może być użyte bezpośrednio na publikowanej powierzchni typu WinRT. Użyj "Platform::Object ^" zamiast przekazywać ten typ|
|C2916 błąd kompilatora|"*identyfikator*": [FlagsAttribute] musi być określony (tylko) na publicznym typie wyliczeniowym z "unsigned int" typ podstawowy|
|[Błąd kompilatora C2917](compiler-error-c2917.md)|"*identyfikator*": nieprawidłowy parametr szablonu|
|[Błąd kompilatora C2918](compiler-error-c2918.md)|"*identyfikator*": nie można używać właściwości indeksowanych na publikowanej powierzchni typu WinRT|
|[Błąd kompilatora C2919](compiler-error-c2919.md)|"*typu*": nie można używać operatorów na publikowanej powierzchni typu WinRT|
|[Błąd kompilatora C2920](compiler-error-c2920.md)|Ponowna definicja: "*typu*": klasa szablonu/ogólne została już zadeklarowana jako*deklaracji*"|
|[Błąd kompilatora C2921](compiler-error-c2921.md)|Ponowna definicja: "*typu*": klasa szablonu/ogólne jest ponownie deklarowany jako*deklaracji*"|
|C2922 błąd kompilatora|"*interfejsu*": interfejs WinRT nie może zawierać statycznych elementów członkowskich|
|[Błąd kompilatora C2923](compiler-error-c2923.md)|"*typu*": "*identyfikator*"nie jest prawidłowy szablon/ogólne, typ argumentu dla parametru"*parametr*"|
|C2924 błąd kompilatora|argument procedury __declspec(Interrupt) nie w R2|
|C2925 błąd kompilatora|Procedura __declspec(Interrupt) nie może używać liczb zmiennoprzecinkowych|
|C2926 błąd kompilatora|"*identyfikator*": domyślny inicjator składowej nie jest dozwolona dla składowej anonimowej struktury w obrębie Unii|
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
|C2938 błąd kompilatora|"*identyfikator*": nie powiodło się specjalizowanie szablonu aliasu|
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
|C2949 błąd kompilatora|Element thread_local nie jest obsługiwany z/Kernel|
|C2950 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2951](compiler-error-c2951.md)|deklaracje szablonu/ogólne są dozwolone tylko w globalnym, przestrzeni nazw lub zakresie klasy|
|[Błąd kompilatora C2952](compiler-error-c2952.md)|"*deklaracji*": deklaracja szablonu/ogólne brakuje listy parametrów szablonu/ogólne|
|[Błąd kompilatora C2953](compiler-error-c2953.md)|"*typu*": szablon klasy została już zdefiniowana|
|C2954 błąd kompilatora|słowo argumentu instrukcji nie jest w zakresie|
|[Błąd kompilatora C2955](compiler-error-c2955.md)|"*typu*": użycie klasy szablonu/ogólne wymaga listy argumentów szablonu/ogólne|
|C2956 błąd kompilatora|powinny być wybierane wielkości dezalokacji funkcja "operator delete (void *, size_t)" jako funkcję dezalokacji umieszczania.|
|[Błąd kompilatora C2957](compiler-error-c2957.md)|"*tokenu*": Nieprawidłowy lewy ogranicznik: oczekiwano "<"|
|[Błąd kompilatora C2958](compiler-error-c2958.md)|po lewej stronie *ogranicznik* adrese "*pliku*(*line_number*)" nie został poprawnie dopasowany|
|[Błąd kompilatora C2959](compiler-error-c2959.md)|Ogólna klasa lub funkcja nie może być składowej szablonu|
|C2960 błąd kompilatora|Nieaktualne.|
|C2961 błąd kompilatora|"*funkcja*": niespójne jawne utworzenie wystąpień, poprzednie jawne utworzenie wystąpienia nie określiła "*argument*"|
|[Błąd kompilatora C2962](compiler-error-c2962.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji składowej klasy szablonu kończącej się znakiem "}"|
|C2963 błąd kompilatora|Nieaktualne.|
|C2964 błąd kompilatora|Nieaktualne.|
|C2965 błąd kompilatora|__declspec (*specyfikator*) nie jest obsługiwany z/Kernel|
|C2966 błąd kompilatora|"*identifier1*": musi mieć ten sam atrybut __declspec(code_seg(...)) jako swojej klasy bazowej*identifier2*"|
|C2967 błąd kompilatora|"*identyfikator*": przesłanianie funkcji wirtualnej musi mieć ten sam atrybut __declspec(code_seg(...)) jako przesłoniętej funkcji wirtualnych|
|C2968 błąd kompilatora|"*identyfikator*": deklaracja aliasu rekursywnego|
|[Błąd kompilatora C2969](compiler-error-c2969.md)|Błąd składniowy: "*tokenu*": Oczekiwano definicji funkcji składowej kończącej się znakiem "}"|
|[Błąd kompilatora C2970](compiler-error-c2970.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": wyrażenie obejmujące obiekty z wewnętrznym powiązaniem nie można użyć jako argument bez typu|
|[Błąd kompilatora C2971](compiler-error-c2971.md)|"*typu*": parametr szablonu "*parametru*": "*argument*": zmienna z okresem magazynu niestatycznych nie można użyć jako argument bez typu|
|C2972 błąd kompilatora|"*typu*": parametr szablonu "*parametr*": typ argumentu bez typu jest nieprawidłowy|
|[Błąd kompilatora C2973](compiler-error-c2973.md)|"*szablonu*": nieprawidłowy argument szablonu "*numer*"|
|[Błąd kompilatora C2974](compiler-error-c2974.md)|"*typu*": argument szablonu nieprawidłowy/ogólne "*parametr*", oczekiwano typu|
|[Błąd kompilatora C2975](compiler-error-c2975.md)|"*typu*": nieprawidłowy argument szablonu dla "*parametr*", oczekiwano stałego wyrażenia czasu kompilacji|
|[Błąd kompilatora C2976](compiler-error-c2976.md)|"*typu*": zbyt mało argumentów szablonu/ogólne|
|[Błąd kompilatora C2977](compiler-error-c2977.md)|"*typu*": zbyt wiele argumentów szablonu/ogólne|
|[Błąd kompilatora C2978](compiler-error-c2978.md)|Błąd składniowy: oczekiwano "*keyword1*"lub"*keyword2*"; znaleziono typ"*typu*"; -type parametry nie są obsługiwane w typach ogólnych|
|[Błąd kompilatora C2979](compiler-error-c2979.md)|jawne specjalizacje nie są obsługiwane w typach ogólnych|
|C2980 błąd kompilatora|Obsługa wyjątków języka C++ nie jest obsługiwany z/Kernel|
|C2981 błąd kompilatora|dynamiczny formularz "*— słowo kluczowe*" nie jest obsługiwany z/Kernel|
|C2982 błąd kompilatora|"*deklaracji*": użyto innego __declspec(code_seg(...)): został "*identifier1*"teraz"*identifier2*"|
|C2983 błąd kompilatora|"*deklaracji*": wszystkie deklaracje muszą mieć identyczne __declspec(code_seg(...))|
|C2984 błąd kompilatora|Nieaktualne.|
|C2985 błąd kompilatora|"*argument*": argument dla __declspec(code_seg(...)) musi być sekcją tekstu|
|C2986 błąd kompilatora|"*identyfikator*": __declspec(code_seg(...)) będzie stosowany tylko do klasy lub funkcji|
|C2987 błąd kompilatora|Deklaracja nie może mieć zarówno __declspec (code_seg ("*identyfikator*")) i __declspec (code_seg ("*wartość*"))|
|[Błąd kompilatora C2988](compiler-error-c2988.md)|Deklaracja/definicja szablonu nierozpoznawalną|
|[Błąd kompilatora C2989](compiler-error-c2989.md)|"*klasy*": klasa szablonu/ogólne została już zadeklarowana jako szablon/ogólnej klasy korporacyjnej|
|[Błąd kompilatora C2990](compiler-error-c2990.md)|"*klasy*": klasy korporacyjnej szablonu/ogólne został już zadeklarowany jako klasa szablonu/ogólne|
|[Błąd kompilatora C2991](compiler-error-c2991.md)|Ponowna definicja parametru szablonu/ogólne "*parametr*"|
|[Błąd kompilatora C2992](compiler-error-c2992.md)|"*klasy*": szablon/ogólne nieprawidłowa lub brakująca lista parametrów|
|[Błąd kompilatora C2993](compiler-error-c2993.md)|"*typu*": niedozwolony typ dla parametru szablonu bez typu "*identyfikator*"|
|[Błąd kompilatora C2994](compiler-error-c2994.md)|Klasa bez nazwy na liście parametrów szablonu|
|[Błąd kompilatora C2995](compiler-error-c2995.md)|"*deklaracji*": szablon funkcji został już zdefiniowany|
|[Błąd kompilatora C2996](compiler-error-c2996.md)|"*funkcja*": definicja szablonu funkcji cyklicznej|
|C2997 błąd kompilatora|"*funkcja*": granica tablicy nie można wywnioskować z domyślny inicjator składowej|
|[Błąd kompilatora C2998](compiler-error-c2998.md)|"*deklaratora*": nie może być definicją szablonu|
|C2999 błąd kompilatora|Nieznany błąd, wybierz polecenie Pomoc techniczna w Visual C++ menu Pomoc lub Otwórz plik pomocy technicznej, aby uzyskać więcej informacji|
