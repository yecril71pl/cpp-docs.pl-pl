---
title: Błędy kompilatora od C3400 do C3499
ms.date: 11/17/2017
f1_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3445
- C3446
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
helpviewer_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3445
- C3446
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
ms.assetid: a5651dfb-c402-4e01-b3ae-28f371e51d6a
ms.openlocfilehash: 24915a52bffb6826599e4d64d60a3ece6bee7675
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576725"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Błędy kompilatora od C3400 do C3499

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C3400](compiler-error-c3400.md)|ograniczenie cykliczne zależności obejmujące "*constraint1*"i"*constraint2*"|
|C3401 błąd kompilatora|"*specyfikator*": specyfikator dostępu nieprawidłowy zestawu - tylko "private" jest dozwolona dla szablonów klas|
|C3402 błąd kompilatora|"*funkcja*": nie można rozpoznać przeciążenia z wyjątkiem w bieżącym zakresie|
|C3403 błąd kompilatora|Element thread_local nie może być użyty z/CLR: pure lub/CLR: Safe|
|C3404 błąd kompilatora|"*konstruowania*": nieoczekiwany błąd składni|
|C3405 błąd kompilatora|"*funkcja*": nie można rozpoznać przeciążenia bez pełnego deskryptora|
|C3406 błąd kompilatora|"*— słowo kluczowe*": nie można używać w specyfikatorze typu|
|C3407 błąd kompilatora|"*typu*" nie można użyć w tym kontekście|
|[Błąd kompilatora C3408](compiler-error-c3408.md)|"*atrybut*": atrybut nie jest dozwolony dla definicji szablonu|
|[Błąd kompilatora C3409](compiler-error-c3409.md)|pusty blok atrybutu nie jest dozwolone.|
|C3410 błąd kompilatora|"*identyfikator*": typ jawnego utworzenia wystąpienia "*typu*"nie jest zgodny z typem zmiennej szablonu"*typu*"|
|C3411 błąd kompilatora|"*typu*" jest nieprawidłowa w przypadku rozmiaru tablicy, ponieważ nie jest typu całkowitego|
|[Błąd kompilatora C3412](compiler-error-c3412.md)|"*specjalizacji*": nie można specjalizować szablonu w bieżącym zakresie|
|[Błąd kompilatora C3413](compiler-error-c3413.md)|"*szablonu*": nieprawidłowe jawne utworzenie wystąpienia|
|[Błąd kompilatora C3414](compiler-error-c3414.md)|"*funkcja*": nie można zdefiniować importowanej funkcji składowej|
|[Błąd kompilatora C3415](compiler-error-c3415.md)|wiele "*sekcji*" znaleziono sekcji z różnymi atrybutami ("0 x*wartość*")|
|C3416 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3417](compiler-error-c3417.md)|"*deklaratora*": typy wartości nie może zawierać funkcji specjalnych elementów członkowskich zdefiniowanych przez użytkownika|
|[Błąd kompilatora C3418](compiler-error-c3418.md)|Specyfikator dostępu "*specyfikator*" nie jest obsługiwana|
|C3419 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3420](compiler-error-c3420.md)|"*funkcja*": finalizator nie może być wirtualny|
|[Błąd kompilatora C3421](compiler-error-c3421.md)|"*funkcja*": nie można wywołać finalizatora dla tej klasy, ponieważ jest on niedostępny lub nie istnieje|
|C3422 błąd kompilatora|"*deklaracji*": niezgodne typy*typu*"i"*typu*"|
|C3423 błąd kompilatora|Nieaktualne.|
|C3424 błąd kompilatora|"*typu*": niedozwolone Rzutowanie na typ tablicy stylu funkcji|
|C3425 błąd kompilatora|Nie można zgłosić wskaźnika do obiektu niekompletnego typu "*typu*"|
|C3426 błąd kompilatora|Nie można zgłosić obiektu niekompletnego typu "*typu*"|
|C3427 błąd kompilatora|"*kontekstu*": "*— słowo kluczowe*" nie można używać z layout_version (*numer*)|
|C3428 błąd kompilatora|"*kontekstu*": "*— słowo kluczowe*" mogą być stosowane tylko do deklaracji lub definicji klasy|
|C3429 błąd kompilatora|"*kontekstu*": "*— słowo kluczowe*" nie można zastosować dla Unii|
|C3430 błąd kompilatora|wyliczenie w zakresie musi mieć nazwę|
|C3431 błąd kompilatora|"*identyfikator*": *type1* nie może być ponownie zadeklarowany jako *Typ2*|
|C3432 błąd kompilatora|"*identyfikator*": deklaracja zapowiadająca wyliczenia nieobjętego zakresem musi być typu podstawowego|
|C3433 błąd kompilatora|"*identyfikator*": wszystkie deklaracje wyliczenia muszą mieć ten sam typ podstawowy, została "*type1*"teraz"*type2*"|
|C3434 błąd kompilatora|"*kontekstu*": moduł wyliczający wartość "*numer*"nie może być reprezentowany jako"*typu*", wartość to"*numer*"|
|C3435 błąd kompilatora|zestaw znaków "*nazwa*" nie jest obsługiwana|
|C3436 błąd kompilatora|#pragma setlocale nie jest obsługiwana, gdy określono/Source-Charset, / Execution-Charset lub/UTF-8|
|C3437 błąd kompilatora|#pragma execution_character_set nie jest obsługiwana, gdy określono/Source-Charset, / Execution-Charset lub/UTF-8|
|C3438 błąd kompilatora|"*kontekstu*": "*wartość*" nie można zastosować do klasy zarządzane/WinRT|
|C3439 błąd kompilatora|layout_version (*numer*): nieprawidłowy numer wersji|
|C3440 błąd kompilatora|"*deklaracji*": layout_version (*numer*) niezgodny z wcześniejszą deklaracją|
|C3441 błąd kompilatora|"*deklaracji*": "*— słowo kluczowe*" nie można zastosować po zdefiniowaniu klasy|
|C3442 błąd kompilatora|Inicjowanie wielu składowych Unii: "*Członek1*"i"*członek2*"|
|C3443 błąd kompilatora|Domyślny inicjator składowej "*klasy*" jest rekursywny|
|C3444 błąd kompilatora|Pusta klasa agregacji*klasy*"musi zostać zainicjowany z"{}"|
|[Błąd kompilatora C3445](compiler-error-c3445.md)|Kopiuj list-initialization elementu "*typu*" nie może używać konstruktora jawnego|
|[Błąd kompilatora C3446](compiler-error-c3446.md)|"*klasy*": domyślny inicjator składowej nie jest dozwolona dla składowej klasy wartości|
|C3447 błąd kompilatora|Nieaktualne.|
|C3448 błąd kompilatora|Nieaktualne.|
|C3449 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3450](compiler-error-c3450.md)|"*typu*": nie jest atrybutem; nie można określić [System::AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute]|
|[Błąd kompilatora C3451](compiler-error-c3451.md)|"*atrybut*": nie można zastosować niezarządzanego atrybutu do "*typu*"|
|[Błąd kompilatora C3452](compiler-error-c3452.md)|składowa listy argumentów nie jest stałą|
|[Błąd kompilatora C3453](compiler-error-c3453.md)|"*atrybut*": atrybut nie zastosowany, ponieważ kwalifikator "*kwalifikator*" jest niezgodny|
|[Błąd kompilatora C3454](compiler-error-c3454.md)|[attribute] nie jest dozwolony dla deklaracji klasy|
|[Błąd kompilatora C3455](compiler-error-c3455.md)|"*atrybut*": żaden z konstruktorów atrybutu odpowiada tym argumentom|
|[Błąd kompilatora C3456](compiler-error-c3456.md)|[źródło\_annotation_attribute] nie jest dozwolony dla deklaracji klasy zarządzane/WinRT|
|[Błąd kompilatora C3457](compiler-error-c3457.md)|"*atrybut*": atrybut nie obsługuje nienazwanych argumentów|
|[Błąd kompilatora C3458](compiler-error-c3458.md)|"[*atrybut*]": atrybut "[*atrybut*]" już określonym dla "*identyfikator*"|
|[Błąd kompilatora C3459](compiler-error-c3459.md)|"[*atrybut*]": atrybut dozwolone tylko w indeksatorze klasy (Właściwość indeksowana domyślnie)|
|[Błąd kompilatora C3460](compiler-error-c3460.md)|"*typu*": tylko typ zdefiniowany przez użytkownika może być przekazywany|
|[Błąd kompilatora C3461](compiler-error-c3461.md)|"*typu*": tylko typ zarządzany WinRT może być przekazywany|
|[Błąd kompilatora C3462](compiler-error-c3462.md)|"*typu*": tylko typu zaimportowany może być przekazywany|
|[Błąd kompilatora C3463](compiler-error-c3463.md)|"*typu*": typ nie jest dozwolony w atrybucie "implements"|
|[Błąd kompilatora C3464](compiler-error-c3464.md)|"*typu*" nie można przesłać dalej typu zagnieżdżonego|
|[Błąd kompilatora C3465](compiler-error-c3465.md)|Aby użyć typu "*typu*"można odwoływać się do zestawu"*zestawu*"|
|[Błąd kompilatora C3466](compiler-error-c3466.md)|"*typu*": specjalizacji klasy generycznej nie może być przekazywany|
|[Błąd kompilatora C3467](compiler-error-c3467.md)|"*typu*": ten typ został już przekazany|
|[Błąd kompilatora C3468](compiler-error-c3468.md)|"*typu*": można tylko przekazać dalej typ do zestawu: "*identyfikator*" nie jest zestawem|
|[Błąd kompilatora C3469](compiler-error-c3469.md)|"*typu*": nie można przesłać dalej klasy ogólnej|
|[Błąd kompilatora C3470](compiler-error-c3470.md)|"*klasy*": klasa nie może posiadać zarówno indeksatora (właściwość domyślnie indeksowana) i operatora]|
|C3471 błąd kompilatora|Nowa nazwa modułu *nazwa* (ustawiona w wierszu polecenia) jest w konflikcie z poprzednią nazwą *nazwy*|
|C3472 błąd kompilatora|Nowa nazwa pliku wyjściowego *filename* (ustawiona w wierszu polecenia) jest w konflikcie z poprzednią nazwą pliku *nazwy pliku*|
|C3473 błąd kompilatora|nie danych wyjściowych nazwy ścieżki lub moduł określono nazwy.|
|C3474 błąd kompilatora|Nie można otworzyć pliku wyjściowego "*filename*"|
|C3475 błąd kompilatora|Błąd składni w pliku wejściowym "*filename*"|
|C3476 błąd kompilatora|Nie można otworzyć pliku "*filename*" dla danych wejściowych|
|C3477 błąd kompilatora|wyrażenia lambda nie może występować w nieznanym kontekście|
|C3478 błąd kompilatora|"*identyfikator*": tablica nie może zostać przechwycona przez kopię|
|C3479 błąd kompilatora|Adnotacje SAL w lambdach nie są obsługiwane.|
|[Błąd kompilatora C3480](compiler-error-c3480.md)|"*zmiennej*": zmienna przechwytująca lambdę musi być z otaczającego zakresu funkcji|
|[Błąd kompilatora C3481](compiler-error-c3481.md)|"*identyfikator*": zmienna przechwytująca lambdę nie znaleziono|
|[Błąd kompilatora C3482](compiler-error-c3482.md)|"this" należy używać tylko jako przechwyt lambdy w obrębie funkcji niestatycznego elementu członkowskiego|
|[Błąd kompilatora C3483](compiler-error-c3483.md)|"*identyfikator*" jest już częścią listy przechwytów lambdy|
|[Błąd kompilatora C3484](compiler-error-c3484.md)|Błąd składniowy: oczekiwano "->" przed zwracanym typem|
|[Błąd kompilatora C3485](compiler-error-c3485.md)|Definicja lambdy nie może mieć żadnych kwalifikatorów cv|
|C3486 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3487](compiler-error-c3487.md)|"*typu*": wszystkie zwracać wyrażenia muszą być ustalane do tego samego typu: wcześniej było to "*typu*"|
|[Błąd kompilatora C3488](compiler-error-c3488.md)|"&*identyfikator*" nie jest dozwolone, gdy domyślny tryb przechwytywania to przez odwołanie|
|[Błąd kompilatora C3489](compiler-error-c3489.md)|"&*identyfikator*" jest wymagana, gdy domyślny tryb przechwytywania to przez kopiowanie|
|[Błąd kompilatora C3490](compiler-error-c3490.md)|"*identyfikator*" nie można zmodyfikować, ponieważ jest on dostępny za pośrednictwem obiekt const|
|[Błąd kompilatora C3491](compiler-error-c3491.md)|"*identyfikator*": przez skopiowanie przechwytywania nie można modyfikować w niemodyfikowalnym wyrażeniu lambda|
|[Błąd kompilatora C3492](compiler-error-c3492.md)|"*identyfikator*": nie można dokonać przechwytu składowej z anonimowej Unii|
|[Błąd kompilatora C3493](compiler-error-c3493.md)|"*identyfikator*" nie może być niejawnie przechwycone, ponieważ nie podano żadnego domyślnego trybu przechwytywania|
|C3494 błąd kompilatora|"this" nie można jawnie przechwycić, ponieważ nie zezwala na to otaczający tryb przechwytywania|
|[Błąd kompilatora C3495](compiler-error-c3495.md)|"*identyfikator*": identyfikator w przechwytywaniu musi być zmienną z automatycznym okresem magazynu zadeklarowaną w obejmującym zasięgu lambdy|
|[Błąd kompilatora C3496](compiler-error-c3496.md)|"this" jest zawsze przechwytywany przez wartość: "&" jest ignorowany|
|C3497 błąd kompilatora|Nie można skonstruować wystąpienia lambdy|
|[Błąd kompilatora C3498](compiler-error-c3498.md)|"*identyfikator*": nie można dokonać przechwytu zmiennej, która ma typ zarządzany WinRT|
|[Błąd kompilatora C3499](compiler-error-c3499.md)|lambda, która została określona ma zwracać typ void nie może zwracać wartości|

