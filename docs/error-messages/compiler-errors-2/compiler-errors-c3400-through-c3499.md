---
title: Błędy kompilatora — od C3400 do C3499
ms.date: 04/21/2019
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
ms.openlocfilehash: f4aff80178033d34cf051a14d89736b2b8347dd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446837"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Błędy kompilatora — od C3400 do C3499

W artykułach w tej sekcji dokumentacji wyjaśniono podzestaw komunikatów o błędach generowanych przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C3400](compiler-error-c3400.md)|cykliczna zależność ograniczenia obejmująca elementy "*Constraint1*" i "*constraint2*"|
|Błąd kompilatora C3401|"*specyfikator*": Nieprawidłowy specyfikator dostępu do zestawu — w szablonach klas dozwolony jest tylko element "Private"|
|Błąd kompilatora C3402|"*Function*": nie można rozpoznać przeciążenia z wyjątkiem tego w bieżącym zakresie|
|Błąd kompilatora C3403|nie można użyć thread_local z/CLR: Pure lub/CLR: Safe|
|Błąd kompilatora C3404|"*konstrukcja*": nieoczekiwany błąd składniowy|
|Błąd kompilatora C3405|"*Function*": nie można rozpoznać przeciążenia bez pełnego deskryptora|
|Błąd kompilatora C3406|*słowo kluczowe*": nie może być użyte w specyfikatorze typu złożonego|
|Błąd kompilatora C3407|nie można użyć elementu "*Type*" w tym kontekście|
|[Błąd kompilatora C3408](compiler-error-c3408.md)|"*Attribute*": atrybut nie jest dozwolony dla definicji szablonu|
|[Błąd kompilatora C3409](compiler-error-c3409.md)|pusty blok atrybutu jest niedozwolony|
|Błąd kompilatora C3410|"*Identyfikator*": typ jawnego utworzenia wystąpienia "*Type*" nie pasuje do typu szablonu zmiennej "*Type*"|
|Błąd kompilatora C3411|Typ "*Type*" jest nieprawidłowy, ponieważ rozmiar tablicy nie jest typem Integer|
|[Błąd kompilatora C3412](compiler-error-c3412.md)|"*specjalizacja*": nie można specjalizacji szablonu w bieżącym zakresie|
|[Błąd kompilatora C3413](compiler-error-c3413.md)|"*Template*": nieprawidłowe jawne utworzenie wystąpienia|
|[Błąd kompilatora C3414](compiler-error-c3414.md)|"*Function*": zaimportowana funkcja członkowska nie może być zdefiniowana|
|[Błąd kompilatora C3415](compiler-error-c3415.md)|znaleziono wiele sekcji "*Section*" z różnymi atrybutami ("0x*Value*")|
|Błąd kompilatora C3416|Nieaktualne.|
|[Błąd kompilatora C3417](compiler-error-c3417.md)|"*deklarator*": Typy wartościowe nie mogą zawierać specjalnych funkcji składowych zdefiniowanych przez użytkownika|
|[Błąd kompilatora C3418](compiler-error-c3418.md)|specyfikator dostępu "*specyfikator*" nie jest obsługiwany|
|Błąd kompilatora C3419|Nieaktualne.|
|[Błąd kompilatora C3420](compiler-error-c3420.md)|"*Function*": finalizator nie może być wirtualny|
|[Błąd kompilatora C3421](compiler-error-c3421.md)|"*Function*": nie można wywołać finalizatora dla tej klasy, ponieważ jest ona niedostępna lub nie istnieje|
|Błąd kompilatora C3422|"*Deklaracja*": niezgodne typy "*Type*" i "*Type*"|
|Błąd kompilatora C3423|Nieaktualne.|
|Błąd kompilatora C3424|"*Type*": Rzutowanie w stylu funkcji na typ tablicy jest niedozwolone|
|Błąd kompilatora C3425|nie można zgłosić wskaźnika do obiektu niekompletnego typu "*Type*"|
|Błąd kompilatora C3426|nie można zgłosić obiektu niekompletnego typu "*Type*"|
|Błąd kompilatora C3427|nie można użyć elementu "*Context*": "*keyword*" z layout_version (*Number*)|
|Błąd kompilatora C3428|"*Context*": "*słowo kluczowe*" może być stosowane tylko do deklaracji lub definicji klasy|
|Błąd kompilatora C3429|nie można zastosować elementu "*Context*": "*słowo kluczowe*" do Unii|
|Błąd kompilatora C3430|Wyliczenie w zakresie musi mieć nazwę|
|Błąd kompilatora C3431|"*Identyfikator*": *Type1* nie może być ponownie zadeklarowany jako *Type2*|
|Błąd kompilatora C3432|"*Identyfikator*": Deklaracja do przodu wyliczenia nienależącego do zakresu musi mieć typ podstawowy|
|Błąd kompilatora C3433|"*Identyfikator*": wszystkie deklaracje wyliczenia muszą mieć ten sam typ podstawowy, było "*Type1*" teraz "*Type2*"|
|Błąd kompilatora C3434|"*Context*": wartość modułu wyliczającego "*Number*" nie może być reprezentowana jako "*Type*", wartość to "*Number*"|
|Błąd kompilatora C3435|zestaw znaków "*name*" nie jest obsługiwany|
|Błąd kompilatora C3436|#pragma setlocaling nie jest obsługiwana, jeśli określono określono element/source-charset,/Execution-charset lub/UTF-8|
|Błąd kompilatora C3437|execution_character_set #pragma nie jest obsługiwana, jeśli określono określono element/source-charset,/Execution-charset lub/UTF-8|
|Błąd kompilatora C3438|nie można zastosować elementu "*Context*": "*Value*" do klasy Managed/WinRT|
|Błąd kompilatora C3439|layout_version (*Number*): nieprawidłowy numer wersji|
|Błąd kompilatora C3440|"*Deklaracja*": layout_version (*Number*) niezgodna z poprzednią deklaracją|
|Błąd kompilatora C3441|nie można zastosować*deklaracji*"Class": "*słowo kluczowe*" po zdefiniowaniu klasy|
|Błąd kompilatora C3442|Inicjowanie wielu składowych Unii: "*member1*" i "*member2*"|
|Błąd kompilatora C3443|Domyślny inicjator składowej "*Class*" jest cykliczny|
|Błąd kompilatora C3444|Pusta Klasa agregująca "*Class*" musi być zainicjowana przy użyciu "{}"|
|[Błąd kompilatora C3445](compiler-error-c3445.md)|podczas inicjowania listy*typu "Type*" nie można używać konstruktora jawnego|
|[Błąd kompilatora C3446](compiler-error-c3446.md)|"*Class*": domyślny inicjator składowej jest niedozwolony dla składowej klasy wartości|
|Błąd kompilatora C3447|Nieaktualne.|
|Błąd kompilatora C3448|Nieaktualne.|
|Błąd kompilatora C3449|Nieaktualne.|
|[Błąd kompilatora C3450](compiler-error-c3450.md)|"*Type*": nie jest atrybutem; nie można określić [System:: AttributeUsageAttribute]/[Windows:: Foundation:: Metadata:: AttributeUsageAttribute]|
|[Błąd kompilatora C3451](compiler-error-c3451.md)|"*Attribute*": nie można zastosować niezarządzanego atrybutu do "*Type*"|
|[Błąd kompilatora C3452](compiler-error-c3452.md)|członek argumentu listy nie jest stałą|
|[Błąd kompilatora C3453](compiler-error-c3453.md)|"*Attribute*": atrybut nie został zastosowany, ponieważ kwalifikator "*kwalifikator*" jest niezgodny|
|[Błąd kompilatora C3454](compiler-error-c3454.md)|[Attribute] nie jest dozwolony w deklaracji klasy|
|[Błąd kompilatora C3455](compiler-error-c3455.md)|"*Attribute*": żaden z konstruktorów atrybutu nie pasuje do argumentów|
|[Błąd kompilatora C3456](compiler-error-c3456.md)|[Źródło\_annotation_attribute] nie jest dozwolone dla deklaracji klasy zarządzanej/WinRT|
|[Błąd kompilatora C3457](compiler-error-c3457.md)|"*Attribute*": atrybut nie obsługuje nienazwanych argumentów|
|[Błąd kompilatora C3458](compiler-error-c3458.md)|"[*Attribute*]": atrybut "[*Attribute*]" jest już określony dla elementu "*Identifier*"|
|[Błąd kompilatora C3459](compiler-error-c3459.md)|"[*Attribute*]": atrybut dozwolony tylko w indeksatorze klasy (Właściwość indeksowana domyślnie)|
|[Błąd kompilatora C3460](compiler-error-c3460.md)|"*Type*": tylko typ zdefiniowany przez użytkownika może być przekazywany|
|[Błąd kompilatora C3461](compiler-error-c3461.md)|"*Type*": tylko typ zarządzany/WinRT może być przekazywany|
|[Błąd kompilatora C3462](compiler-error-c3462.md)|"*Type*": tylko typ importowany może być przekazywany|
|[Błąd kompilatora C3463](compiler-error-c3463.md)|"*Type*": typ nie jest dozwolony w atrybucie "Implements"|
|[Błąd kompilatora C3464](compiler-error-c3464.md)|Typ*type*zagnieżdżony nie może być przekazywany dalej|
|[Błąd kompilatora C3465](compiler-error-c3465.md)|Aby użyć typu "*Type*", należy odwołać się do zestawu "*Assembly*"|
|[Błąd kompilatora C3466](compiler-error-c3466.md)|"*Type*": specjalizacji klasy generycznej nie można przesłać dalej|
|[Błąd kompilatora C3467](compiler-error-c3467.md)|"*Type*": ten typ został już przekazany|
|[Błąd kompilatora C3468](compiler-error-c3468.md)|"*Type*": można tylko przesłać dalej typ do zestawu: "*Identifier*" nie jest zestawem|
|[Błąd kompilatora C3469](compiler-error-c3469.md)|"*Type*": nie można przesłać dalej klasy generycznej|
|[Błąd kompilatora C3470](compiler-error-c3470.md)|"*Class*": Klasa nie może posiadać zarówno indeksatora (Właściwość indeksowana domyślnie), jak i operatora []|
|Błąd kompilatora C3471|*Nazwa nowego modułu (ustawiona* w wierszu polecenia) powoduje konflikt z poprzednią *nazwą* nazwy|
|Błąd kompilatora C3472|Nowa nazwa pliku wyjściowego *filename* (ustawiona w wierszu polecenia) powoduje konflikt z poprzednią nazwą pliku *filename*|
|Błąd kompilatora C3473|nie określono ścieżki wyjściowej ani nazwy modułu.|
|Błąd kompilatora C3474|nie można otworzyć pliku wyjściowego "*filename*"|
|Błąd kompilatora C3475|Błąd składniowy w pliku wejściowym "*filename*"|
|Błąd kompilatora C3476|nie można otworzyć pliku "*filename*" dla danych wejściowych|
|Błąd kompilatora C3477|lambda nie mogą występować w nieoszacowanym kontekście|
|Błąd kompilatora C3478|"*Identyfikator*": tablica nie może zostać przechwycona przez kopię|
|Błąd kompilatora C3479|Adnotacje SAL w wyrażeniach lambda nie są obsługiwane|
|[Błąd kompilatora C3480](compiler-error-c3480.md)|"*zmienna*": zmienna przechwytywania lambda musi pochodzić z otaczającego zakresu funkcji|
|[Błąd kompilatora C3481](compiler-error-c3481.md)|"*Identyfikator*": nie znaleziono zmiennej przechwytywania lambda|
|[Błąd kompilatora C3482](compiler-error-c3482.md)|elementu "This" można użyć tylko jako przechwytywania lambda w obrębie niestatycznej funkcji składowej|
|[Błąd kompilatora C3483](compiler-error-c3483.md)|element "*Identifier*" jest już częścią listy przechwytywania lambda|
|[Błąd kompilatora C3484](compiler-error-c3484.md)|Błąd składniowy: oczekiwano "->" przed typem zwracanym|
|[Błąd kompilatora C3485](compiler-error-c3485.md)|Definicja lambda nie może mieć żadnych kwalifikatorów CV|
|Błąd kompilatora C3486|Nieaktualne.|
|[Błąd kompilatora C3487](compiler-error-c3487.md)|"*Type*": wszystkie wyrażenia Return muszą zostać wywnioskowane dla tego samego typu: poprzednio było "*Type*"|
|[Błąd kompilatora C3488](compiler-error-c3488.md)|element "&*Identifier*" jest niedozwolony, gdy domyślny tryb przechwytywania to-Reference|
|[Błąd kompilatora C3489](compiler-error-c3489.md)|element "&*Identifier*" jest wymagany, gdy domyślny tryb przechwytywania jest kopiowany|
|[Błąd kompilatora C3490](compiler-error-c3490.md)|nie można zmodyfikować elementu "*Identifier*", ponieważ jest on dostępny za pomocą obiektu const|
|[Błąd kompilatora C3491](compiler-error-c3491.md)|"*Identyfikator*": nie można zmodyfikować przechwycenia przez kopię w niemodyfikowalnym wyrażeniu lambda|
|[Błąd kompilatora C3492](compiler-error-c3492.md)|"*Identyfikator*": nie można przechwycić elementu członkowskiego Unii anonimowej|
|[Błąd kompilatora C3493](compiler-error-c3493.md)|nie można jawnie przechwycić*identyfikatora "identifier*", ponieważ nie określono żadnego domyślnego trybu przechwytywania|
|Błąd kompilatora C3494|nie można jawnie przechwycić elementu "This", ponieważ otaczający tryb przechwytywania nie zezwala na to|
|[Błąd kompilatora C3495](compiler-error-c3495.md)|"*Identyfikator*": identyfikator w przechwytywaniu musi być zmienną z automatycznym okresem magazynu zadeklarowaną w zasięgu do osiągnięcia wyrażenia lambda|
|[Błąd kompilatora C3496](compiler-error-c3496.md)|element "This" jest zawsze przechwytywany przez wartość: zignorowano element "&"|
|Błąd kompilatora C3497|nie można skonstruować wystąpienia wyrażenia lambda|
|[Błąd kompilatora C3498](compiler-error-c3498.md)|"*Identyfikator*": nie można przechwycić zmiennej, która ma typ zarządzany/WinRT|
|[Błąd kompilatora C3499](compiler-error-c3499.md)|lambda, która została określona jako zwracająca typ void nie może zwracać wartości|

## <a name="see-also"></a>Zobacz też

[Błędy iC++ ostrzeżenia narzędzi języka C/kompilatora i kompilacji](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora C2000-C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
