---
title: Błędy kompilatora od C3300 do C3399
ms.date: 11/17/2017
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
ms.openlocfilehash: 22964c9482d87c466665949ad4b340d43b3a5622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652702"
---
# <a name="compiler-errors-c3300-through-c3399"></a>Błędy kompilatora od C3300 do C3399

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|Kompilatora od C3300 do błędu|"*symbol*": niewłaściwy format języka IDL "*wartość*"|
|C3301 błąd kompilatora|"*coclass*": klasa coclass nie może być "*symbol*" interfejsu|
|C3302 błąd kompilatora|"*identyfikator*": identyfikator ma więcej niż *numer* znaków|
|[Błąd kompilatora C3303](compiler-error-c3303.md)|"*atrybut*": atrybut może być używany tylko na "*typu*"|
|C3304 błąd kompilatora|Nieaktualne.|
|C3305 błąd kompilatora|Nieaktualne.|
|C3306 błąd kompilatora|"*szablonu*": klasa Nienazwana szablonu/ogólne nie jest dozwolona|
|C3307 błąd kompilatora|"*modułu*": nie można utworzyć modułu IDL|
|C3308 błąd kompilatora|" *funkcja*": bezpośrednie wywołanie za pomocą zaimportowanej klasy nie jest obsługiwane.|
|[Błąd kompilatora C3309](compiler-error-c3309.md)|"*— makro*/*— słowo kluczowe*': Nazwa modułu nie może być makrem lub słowem kluczowym|
|C3310 błąd kompilatora|"*identyfikator*": konflikt nazwy modułu|
|C3311 błąd kompilatora|Atrybut modułu musi być zdefiniowany w zakresie globalnym|
|C3312 błąd kompilatora|nie wywoływalnej "*identyfikator*"Funkcja znaleziono dla typu"*typu*"|
|C3313 błąd kompilatora|"*identyfikator*": zmienna nie może mieć typu "*typu*"|
|C3314 błąd kompilatora|"*symbol*": nie obsługiwany typ modułu IDL|
|C3315 błąd kompilatora|" *funkcja*": musi być funkcją składową|
|C3316 błąd kompilatora|"*typu*": tablica o nieznanym rozmiarze nie można używać w opartej na zakresie for, instrukcja|
|C3317 błąd kompilatora|"*identyfikator*": przeciążona funkcja nie może służyć jako wyrażenie w opartej na zakresie for, instrukcja|
|C3318 błąd kompilatora|"*typu*": tablica nie może zawierać typu elementu, który zawiera "auto"|
|C3319 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3320](compiler-error-c3320.md)|"*typu*": typ nie może mieć taką samą nazwę jak właściwość modułu "name"|
|C3321 błąd kompilatora|Lista inicjalizatora jest nieoczekiwana w tym kontekście|
|[Błąd kompilatora C3322](compiler-error-c3322.md)|"*właściwość*": nie jest prawidłową właściwością dla atrybutu "*atrybut*"|
|C3323 błąd kompilatora|"alignas" i "__declspec(align)" nie są dozwolone w deklaracjach funkcji|
|C3324 błąd kompilatora|"*właściwość*": właściwość występuje więcej niż jeden raz w atrybucie "*atrybut*"|
|C3325 błąd kompilatora|"*atrybut*": atrybut ma za dużo argumentów|
|C3326 błąd kompilatora|"*wartość*": nie jest prawidłową wartością dla właściwości "*właściwość*"atrybutu"*atrybut*"|
|C3327 błąd kompilatora|"*właściwość*": należy określić wartość dla właściwości atrybutu "*atrybut*"|
|C3328 błąd kompilatora|"*atrybut*": atrybut nie ma wystarczającej liczby argumentów|
|C3329 błąd kompilatora|Błąd składniowy: oczekiwano "*token1*"not"*token2*"|
|C3330 błąd kompilatora|" *funkcja*": funkcja nie może zwracać tablicy "*typu*"|
|C3331 błąd kompilatora|"*identyfikator*": atrybuty w parametrach są dozwolone tylko dla interfejsów COM i klas coclass|
|C3332 błąd kompilatora|"*właściwość*": właściwość niespójna, gramatyka "*właściwość*" jest zarówno wymagana oraz ma wartość domyślną|
|[Błąd kompilatora C3333](compiler-error-c3333.md)|"*biblioteki*": nie można #import biblioteki uszkodzonego typu|
|[Błąd kompilatora C3334](compiler-error-c3334.md)|Nie można #import uszkodzony wpisz biblioteki|
|C3335 błąd kompilatora|"*identyfikator*": może być co najwyżej jeden domyślny interfejs dla klasy coclass*klasy*"|
|C3336 błąd kompilatora|Ta operacja odbywa się w zakresie klasy|
|C3337 błąd kompilatora|"*identyfikator*": defaultvtable musi być źródłem zdarzenia dla klasy coclass*klasy*"|
|C3338 błąd kompilatora|"*identyfikator*": może mieć co najwyżej jeden domyślny interfejs, który jest również źródłem zdarzenia dla klasy coclass*klasy*"|
|C3339 błąd kompilatora|Parametr szablonu szablon wymaga "class" lub "typename" po liście parametrów|
|[Błąd kompilatora C3340](compiler-error-c3340.md)|"*identyfikator*": interfejs nie może być zarówno "restricted" i "default" w klasie coclass*klasy*"|
|C3341 błąd kompilatora|"*interfejsu*": interfejs defaultvtable musi być "dual" albo "custom"|
|[Błąd kompilatora C3342](compiler-error-c3342.md)|"*identyfikator*": niejednoznaczny atrybut|
|C3343 błąd kompilatora|"*klasy*::*nazwa*": identyfikator atrybutu ma zbyt wiele znaków|
|C3344 błąd kompilatora|Nie można zdefiniować jawnej specjalizacji ani częściowej specjalizacji elementu "*symbol*"|
|[Błąd kompilatora C3345](compiler-error-c3345.md)|"*nazwa*": nieprawidłowy identyfikator dla nazwy modułu|
|C3346 błąd kompilatora|wyeksportowana deklaracja w zakresie innym niż przestrzeń nazw|
|[Błąd kompilatora C3347](compiler-error-c3347.md)|"*argument*": wymagany argument nie zostanie określony w atrybucie *asttribute*|
|C3348 błąd kompilatora|wyeksportowane szablony nie są częścią bieżących standardów języka C++|
|C3349 błąd kompilatora|"*klasy*::*elementu członkowskiego*": atrybut multiemisji został już dokonany przez dostawcę *dostawcy*|
|[Błąd kompilatora C3350](compiler-error-c3350.md)|" *funkcja*": Konstruktor delegata oczekuje *numer* następującej liczby argumentów:|
|[Błąd kompilatora C3351](compiler-error-c3351.md)|" *funkcja*": w przypadku przekazania wystąpienia obiektu NULL do konstruktora delegata należy również przekazać adres statycznej funkcji członkowskiej|
|[Błąd kompilatora C3352](compiler-error-c3352.md)|"*funkcja*": określona funkcja nie jest zgodny z typem delegata "*typu*"|
|[Błąd kompilatora C3353](compiler-error-c3353.md)|"*identyfikator*": delegat można tworzyć tylko z globalnej funkcji lub funkcji składowej typu zarządzanego WinRT|
|[Błąd kompilatora C3354](compiler-error-c3354.md)|"*identyfikator*": funkcja używana do utworzenia delegata nie może posiadać typu zwracanego "*typu*"|
|C3355 błąd kompilatora|"*klasy*::*elementu członkowskiego*": atrybut multiemisji nasłuchuje dostawcę "*provider1*", ale jest implementowana przez dostawcę "*provider2*"|
|[Błąd kompilatora C3356](compiler-error-c3356.md)|"*identyfikator*": nie można wywołać atrybutu multiemisji z w pełni kwalifikowana nazwa|
|C3357 błąd kompilatora|"*atrybut*": atrybut jest niejednoznaczny, należy użyć w pełni kwalifikowana nazwa|
|[Błąd kompilatora C3358](compiler-error-c3358.md)|"*symbol*": nie odnaleziono symbolu|
|C3359 błąd kompilatora|"*specjalizacji*": nie można specjalizować szablonu|
|[Błąd kompilatora C3360](compiler-error-c3360.md)|"*ciąg*": nie można utworzyć *nazwy*|
|C3361 błąd kompilatora|Brak kontekstu, w której ma zostać *akcji*|
|C3362 błąd kompilatora|"*klasy*::*elementu członkowskiego*": atrybut multiemisji nie została zaimplementowana.|
|[Błąd kompilatora C3363](compiler-error-c3363.md)|"*identyfikator*": "typeid" można stosować tylko do typu|
|[Błąd kompilatora C3364](compiler-error-c3364.md)|" *funkcja*": nieprawidłowy argument dla konstruktora delegata; miejsce docelowe musi być wskaźnikiem do funkcji składowej|
|[Błąd kompilatora C3365](compiler-error-c3365.md)|operator "*operator*": operandy typu "*typu*"i"*typu*"|
|[Błąd kompilatora C3366](compiler-error-c3366.md)|"*elementu członkowskiego*": statyczne składowe danych typów zarządzanych/WinRT musi być zdefiniowany w ramach definicji klasy|
|[Błąd kompilatora C3367](compiler-error-c3367.md)|" *funkcja*": nie można użyć statycznej funkcji by utworzyć niezwiązanego delegata|
|[Błąd kompilatora C3368](compiler-error-c3368.md)|"*deklaratora*": Nieprawidłowa konwencja wywoływania dla języka IDL|
|[Błąd kompilatora C3369](compiler-error-c3369.md)|"*modułu*": idl_module już zdefiniowany|
|[Błąd kompilatora C3370](compiler-error-c3370.md)|"*modułu*": idl_module jeszcze nie jest zdefiniowana|
|[Błąd kompilatora C3371](compiler-error-c3371.md)|"idl_module": tylko właściwość "name" jest dozwolony w tym miejscu|
|[Błąd kompilatora C3372](compiler-error-c3372.md)|należy określić co najmniej 1 interfejs dla atrybutu "*atrybut*" coclass|
|[Błąd kompilatora C3373](compiler-error-c3373.md)|atrybut "*atrybut*" nie przyjmuje żadnych argumentów z wyjątkiem coclass|
|[Błąd kompilatora C3374](compiler-error-c3374.md)|Nie można przyjąć adresu " *funkcja*" chyba że podczas tworzenia wystąpienia delegata|
|[Błąd kompilatora C3375](compiler-error-c3375.md)|"*funkcja*": niejednoznaczna funkcja delegata|
|C3376 błąd kompilatora|"*szablonu*": dozwolone są tylko szablony statycznych składowych danych|
|C3377 błąd kompilatora|elementu "decltype(auto)" nie jest dozwolona w nowe wyrażenie|
|C3378 błąd kompilatora|deklarację można eksportować tylko z jednostki interfejsu modułu|
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
