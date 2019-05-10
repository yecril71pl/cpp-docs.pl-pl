---
title: Błędy kompilatora — od C3300 do C3399
ms.date: 04/21/2019
f1_keywords:
- C3300
- C3301
- C3302
- C3304
- C3305
- C3306
- C3307
- C3308
- C3310
- C3311
- C3312
- C3313
- C3314
- C3315
- C3316
- C3317
- C3318
- C3319
- C3321
- C3323
- C3324
- C3325
- C3326
- C3327
- C3328
- C3329
- C3330
- C3331
- C3332
- C3335
- C3336
- C3337
- C3338
- C3339
- C3341
- C3343
- C3344
- C3346
- C3348
- C3349
- C3355
- C3357
- C3359
- C3361
- C3362
- C3376
- C3377
- C3378
helpviewer_keywords:
- C3300
- C3301
- C3302
- C3304
- C3305
- C3306
- C3307
- C3308
- C3310
- C3311
- C3312
- C3313
- C3314
- C3315
- C3316
- C3317
- C3318
- C3319
- C3321
- C3323
- C3324
- C3325
- C3326
- C3327
- C3328
- C3329
- C3330
- C3331
- C3332
- C3335
- C3336
- C3337
- C3338
- C3339
- C3341
- C3343
- C3344
- C3346
- C3348
- C3349
- C3355
- C3357
- C3359
- C3361
- C3362
- C3376
- C3377
- C3378
ms.assetid: 190b7d29-ffe6-4261-921d-140da1935d00
ms.openlocfilehash: ca55e19534f722a7231a1d30c63e2dbb77d25ec7
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857723"
---
# <a name="compiler-errors-c3300-through-c3399"></a>Błędy kompilatora — od C3300 do C3399

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Message|
|-----------|-------------|
|Błąd kompilatora od C3300|"*symbol*": niewłaściwy format języka IDL "*wartość*"|
|Błąd kompilatora C3301|"*coclass*": klasa coclass nie może być "*symbol*" interfejsu|
|Błąd kompilatora C3302|"*identyfikator*": identyfikator ma więcej niż *numer* znaków|
|[Błąd kompilatora C3303](compiler-error-c3303.md)|"*atrybut*": atrybut może być używany tylko na "*typu*"|
|Błąd kompilatora C3304|Nieaktualne.|
|Błąd kompilatora C3305|Nieaktualne.|
|Błąd kompilatora C3306|"*szablonu*": klasa Nienazwana szablonu/ogólne nie jest dozwolona|
|Błąd kompilatora C3307|"*modułu*": nie można utworzyć modułu IDL|
|Błąd kompilatora C3308|" *funkcja*": bezpośrednie wywołanie za pomocą zaimportowanej klasy nie jest obsługiwane.|
|[Błąd kompilatora C3309](compiler-error-c3309.md)|"*— makro*/*— słowo kluczowe*': Nazwa modułu nie może być makrem lub słowem kluczowym|
|Błąd kompilatora C3310|"*identyfikator*": konflikt nazwy modułu|
|Błąd kompilatora C3311|Atrybut modułu musi być zdefiniowany w zakresie globalnym|
|Błąd kompilatora C3312|nie wywoływalnej "*identyfikator*"Funkcja znaleziono dla typu"*typu*"|
|Błąd kompilatora C3313|"*identyfikator*": zmienna nie może mieć typu "*typu*"|
|Błąd kompilatora C3314|"*symbol*": nie obsługiwany typ modułu IDL|
|Błąd kompilatora C3315|" *funkcja*": musi być funkcją składową|
|Błąd kompilatora C3316|"*typu*": tablica o nieznanym rozmiarze nie można używać w opartej na zakresie for, instrukcja|
|Błąd kompilatora C3317|"*identyfikator*": przeciążona funkcja nie może służyć jako wyrażenie w opartej na zakresie for, instrukcja|
|Błąd kompilatora C3318|"*typu*": tablica nie może zawierać typu elementu, który zawiera "auto"|
|Błąd kompilatora C3319|Nieaktualne.|
|[Błąd kompilatora C3320](compiler-error-c3320.md)|"*typu*": typ nie może mieć taką samą nazwę jak właściwość modułu "name"|
|Błąd kompilatora C3321|Lista inicjalizatora jest nieoczekiwana w tym kontekście|
|[Błąd kompilatora C3322](compiler-error-c3322.md)|"*właściwość*": nie jest prawidłową właściwością dla atrybutu "*atrybut*"|
|Błąd kompilatora C3323|"alignas" i "__declspec(align)" nie są dozwolone w deklaracjach funkcji|
|Błąd kompilatora C3324|"*właściwość*": właściwość występuje więcej niż jeden raz w atrybucie "*atrybut*"|
|Błąd kompilatora C3325|"*atrybut*": atrybut ma za dużo argumentów|
|Błąd kompilatora C3326|"*wartość*": nie jest prawidłową wartością dla właściwości "*właściwość*"atrybutu"*atrybut*"|
|Błąd kompilatora C3327|"*właściwość*": należy określić wartość dla właściwości atrybutu "*atrybut*"|
|Błąd kompilatora C3328|"*atrybut*": atrybut nie ma wystarczającej liczby argumentów|
|Błąd kompilatora C3329|Błąd składniowy: oczekiwano "*token1*"not"*token2*"|
|Błąd kompilatora C3330|" *funkcja*": funkcja nie może zwracać tablicy "*typu*"|
|Błąd kompilatora C3331|"*identyfikator*": atrybuty w parametrach są dozwolone tylko dla interfejsów COM i klas coclass|
|Błąd kompilatora C3332|"*właściwość*": właściwość niespójna, gramatyka "*właściwość*" jest zarówno wymagana oraz ma wartość domyślną|
|[Błąd kompilatora C3333](compiler-error-c3333.md)|"*biblioteki*": nie można #import biblioteki uszkodzonego typu|
|[Błąd kompilatora C3334](compiler-error-c3334.md)|Nie można #import uszkodzony wpisz biblioteki|
|Błąd kompilatora C3335|"*identyfikator*": Może być co najwyżej jeden domyślny interfejs dla klasy coclass*klasy*"|
|Błąd kompilatora C3336|Ta operacja odbywa się w zakresie klasy|
|Błąd kompilatora C3337|"*identyfikator*": defaultvtable musi być źródłem zdarzenia dla klasy coclass*klasy*"|
|Błąd kompilatora C3338|"*identyfikator*": Może być co najwyżej jeden domyślny interfejs, który jest również źródłem zdarzenia dla klasy coclass*klasy*"|
|Błąd kompilatora C3339|Parametr szablonu szablon wymaga "class" lub "typename" po liście parametrów|
|[Błąd kompilatora C3340](compiler-error-c3340.md)|"*identyfikator*": interfejs nie może być zarówno "restricted" i "default" w klasie coclass*klasy*"|
|Błąd kompilatora C3341|"*interfejsu*": interfejs defaultvtable musi być "dual" albo "custom"|
|[Błąd kompilatora C3342](compiler-error-c3342.md)|"*identyfikator*": niejednoznaczny atrybut|
|Błąd kompilatora C3343|"*klasy*::*nazwa*": identyfikator atrybutu ma zbyt wiele znaków|
|Błąd kompilatora C3344|Nie można zdefiniować jawnej specjalizacji ani częściowej specjalizacji elementu "*symbol*"|
|[Błąd kompilatora C3345](compiler-error-c3345.md)|"*nazwa*": nieprawidłowy identyfikator dla nazwy modułu|
|Błąd kompilatora C3346|wyeksportowana deklaracja w zakresie innym niż przestrzeń nazw|
|[Błąd kompilatora C3347](compiler-error-c3347.md)|"*argument*": wymagany argument nie zostanie określony w atrybucie *asttribute*|
|Błąd kompilatora C3348|wyeksportowane szablony nie są częścią bieżących standardów języka C++|
|Błąd kompilatora C3349|"*klasy*::*elementu członkowskiego*": atrybut multiemisji został już dokonany przez dostawcę *dostawcy*|
|[Błąd kompilatora C3350](compiler-error-c3350.md)|" *funkcja*": Konstruktor delegata oczekuje *numer* następującej liczby argumentów:|
|[Błąd kompilatora C3351](compiler-error-c3351.md)|" *funkcja*": w przypadku przekazania wystąpienia obiektu NULL do konstruktora delegata należy również przekazać adres statycznej funkcji członkowskiej|
|[Błąd kompilatora C3352](compiler-error-c3352.md)|"*funkcja*": określona funkcja nie jest zgodny z typem delegata "*typu*"|
|[Błąd kompilatora C3353](compiler-error-c3353.md)|"*identyfikator*": delegat można tworzyć tylko z globalnej funkcji lub funkcji składowej typu zarządzanego WinRT|
|[Błąd kompilatora C3354](compiler-error-c3354.md)|"*identyfikator*": funkcja używana do utworzenia delegata nie może posiadać typu zwracanego "*typu*"|
|Błąd kompilatora C3355|"*klasy*::*elementu członkowskiego*": atrybut multiemisji nasłuchuje dostawcę "*provider1*", ale jest implementowana przez dostawcę "*provider2*"|
|[Błąd kompilatora C3356](compiler-error-c3356.md)|"*identyfikator*": nie można wywołać atrybutu multiemisji z w pełni kwalifikowana nazwa|
|Błąd kompilatora C3357|"*atrybut*": atrybut jest niejednoznaczny, należy użyć w pełni kwalifikowana nazwa|
|[Błąd kompilatora C3358](compiler-error-c3358.md)|"*symbol*": nie odnaleziono symbolu|
|Błąd kompilatora C3359|"*specjalizacji*": nie można specjalizować szablonu|
|[Błąd kompilatora C3360](compiler-error-c3360.md)|"*ciąg*": nie można utworzyć *nazwy*|
|Błąd kompilatora C3361|Brak kontekstu, w której ma zostać *akcji*|
|Błąd kompilatora C3362|"*klasy*::*elementu członkowskiego*": atrybut multiemisji nie została zaimplementowana.|
|[Błąd kompilatora C3363](compiler-error-c3363.md)|"*identyfikator*": "typeid" można stosować tylko do typu|
|[Błąd kompilatora C3364](compiler-error-c3364.md)|" *funkcja*": nieprawidłowy argument dla konstruktora delegata; miejsce docelowe musi być wskaźnikiem do funkcji składowej|
|[Błąd kompilatora C3365](compiler-error-c3365.md)|operator "*operator*": operandy typu "*typu*"i"*typu*"|
|[Błąd kompilatora C3366](compiler-error-c3366.md)|"*elementu członkowskiego*": statyczne składowe danych typów zarządzanych/WinRT musi być zdefiniowany w ramach definicji klasy|
|[Błąd kompilatora C3367](compiler-error-c3367.md)|" *funkcja*": nie można użyć statycznej funkcji by utworzyć niezwiązanego delegata|
|[Błąd kompilatora C3368](compiler-error-c3368.md)|"*deklaratora*": Nieprawidłowa konwencja wywoływania dla języka IDL|
|[Compiler error C3369](compiler-error-c3369.md)|"*modułu*": idl_module już zdefiniowany|
|[Błąd kompilatora C3370](compiler-error-c3370.md)|"*modułu*": idl_module jeszcze nie jest zdefiniowana|
|[Błąd kompilatora C3371](compiler-error-c3371.md)|"idl_module": tylko właściwość "name" jest dozwolony w tym miejscu|
|[Błąd kompilatora C3372](compiler-error-c3372.md)|należy określić co najmniej 1 interfejs dla atrybutu "*atrybut*" coclass|
|[Błąd kompilatora C3373](compiler-error-c3373.md)|atrybut "*atrybut*" nie przyjmuje żadnych argumentów z wyjątkiem coclass|
|[Błąd kompilatora C3374](compiler-error-c3374.md)|Nie można przyjąć adresu " *funkcja*" chyba że podczas tworzenia wystąpienia delegata|
|[Błąd kompilatora C3375](compiler-error-c3375.md)|"*funkcja*": niejednoznaczna funkcja delegata|
|Błąd kompilatora C3376|"*szablonu*": dozwolone są tylko szablony statycznych składowych danych|
|Błąd kompilatora C3377|elementu "decltype(auto)" nie jest dozwolona w nowe wyrażenie|
|Błąd kompilatora C3378|deklarację można eksportować tylko z jednostki interfejsu modułu|
|[Błąd kompilatora C3379](compiler-error-c3379.md)|"*klasy*": zagnieżdżona klasa nie może mieć specyfikatora dostępu do zestawu jako części swojej deklaracji|
|[Błąd kompilatora C3380](compiler-error-c3380.md)|"*specyfikator*": Nieprawidłowy specyfikator dostępu do zestawu - tylko "public" lub "private" są dozwolone|
|[Błąd kompilatora C3381](compiler-error-c3381.md)|"*specyfikator*": specyfikatory dostępu do zestawu są dostępne tylko w kodzie skompilowanym z opcją/CLR|
|[Błąd kompilatora C3382](compiler-error-c3382.md)|"sizeof" nie jest obsługiwany z/CLR: Safe|
|[Błąd kompilatora C3383](compiler-error-c3383.md)|"operator new" nie jest obsługiwany z/CLR: Safe|
|[Błąd kompilatora C3384](compiler-error-c3384.md)|"*typu*": wartość ograniczenia i ograniczenie ref wzajemnie się wykluczają|
|[Błąd kompilatora C3385](compiler-error-c3385.md)|" *funkcja*": funkcja, która ma niestandardowy atrybut DllImport nie może zwrócić wystąpienia klasy|
|[Błąd kompilatora C3386](compiler-error-c3386.md)|"*typu*": __declspec(dllexport)/__declspec(dllimport) nie można zastosować do typu zarządzanego WinRT|
|[Błąd kompilatora C3387](compiler-error-c3387.md)|"*elementu członkowskiego*": __declspec(dllexport)/__declspec(dllimport) nie można zastosować do składowej typu zarządzanego WinRT|
|[Błąd kompilatora C3388](compiler-error-c3388.md)|"*tokenu*": niedozwolone jako ograniczenie, przy założeniu "*wartość*' Aby kontynuować analizowanie|
|[Błąd kompilatora C3389](compiler-error-c3389.md)|__declspec (*specyfikator*) nie może być użyty z/CLR: pure lub/CLR: Safe|
|[Błąd kompilatora C3390](compiler-error-c3390.md)|"*typu*": nieprawidłowy typ argumentu dla parametru ogólnego "*parametru*"z ogólnego"*generic_type*", musi być typem referencyjnym|
|[Błąd kompilatora C3391](compiler-error-c3391.md)|"*typu*": nieprawidłowy typ argumentu dla parametru ogólnego "*parametru*"z ogólnego"*generic_type*", musi być typem wartości niedopuszczającym wartości|
|[Błąd kompilatora C3392](compiler-error-c3392.md)|"*typu*": nieprawidłowy typ argumentu dla parametru ogólnego "*parametru*"z ogólnego"*generic_type*", musi mieć publicznego konstruktora bez parametrów|
|[Błąd kompilatora C3393](compiler-error-c3393.md)|Błąd składni w klauzuli ograniczenia: "*identyfikator*" nie jest typem|
|[Błąd kompilatora C3394](compiler-error-c3394.md)|Błąd składni w klauzuli ograniczenia: znaleziono "*symbol*" Oczekiwano typu|
|[Błąd kompilatora C3395](compiler-error-c3395.md)|" *funkcja*": __declspec(dllexport) nie można zastosować do funkcji w Konwencji wywołania __clrcall|
|[Błąd kompilatora C3396](compiler-error-c3396.md)|"*klasy*. *element członkowski*": atrybut niestandardowy nie znaleziono w"*przestrzeni nazw*"|
|[Błąd kompilatora C3397](compiler-error-c3397.md)|Inicjalizacja agregacji jest niedozwolona w domyślnych argumentów|
|[Błąd kompilatora C3398](compiler-error-c3398.md)|"*operator*": nie można konwertować z "*typu*"to"*typu*". Wyrażenie źródłowe musi być symbolem funkcji|
|[Błąd kompilatora C3399](compiler-error-c3399.md)|"*typu*": nie można udostępnić argumentów podczas tworzenia wystąpienia parametru generycznego|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
