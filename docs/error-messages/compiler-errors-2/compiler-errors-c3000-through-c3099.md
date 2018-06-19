---
title: C3000 błędy kompilatora za pośrednictwem C3099 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
dev_langs:
- C++
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0941b2bd6b998e8beb18fa7e5960aa93beb6a80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284722"
---
# <a name="compiler-errors-c3000-through-c3099"></a>C3000 błędy kompilatora za pośrednictwem C3099

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|C3000 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3001](compiler-error-c3001.md)|"*komunikat*": Oczekiwano nazwy dyrektywy OpenMP|
|[Błąd kompilatora C3002](compiler-error-c3002.md)|"*Nazwa1* *Nazwa2*": wielokrotne nazwy dyrektyw OpenMP|
|[Błąd kompilatora C3003](compiler-error-c3003.md)|"*dyrektywy*": Nazwa dyrektywy OpenMP nie jest dozwolona po klauzulach dyrektywy|
|[Błąd kompilatora C3004](compiler-error-c3004.md)|"*klauzuli*": nie jest prawidłowa w OpenMP — klauzula "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3005](compiler-error-c3005.md)|"*komunikat*": Napotkano nieoczekiwany token w OpenMP "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3006](compiler-error-c3006.md)|"*klauzuli*": klauzula w OpenMP "*dyrektywy*" dyrektywy brakuje oczekiwanego argumentu|
|[Błąd kompilatora C3007](compiler-error-c3007.md)|"*klauzuli*": klauzula w OpenMP "*dyrektywy*" dyrektywy nie przyjmuje argumentu|
|[Błąd kompilatora C3008](compiler-error-c3008.md)|"*argument*": argumencie brakuje zamykającego ")" na OpenMP "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3009](compiler-error-c3009.md)|"*etykiety*": skok do strukturalnego bloku OpenMP jest niedozwolony|
|[Błąd kompilatora C3010](compiler-error-c3010.md)|"*etykiety*": wyskok ze strukturalnego bloku OpenMP jest niedozwolony|
|[Błąd kompilatora C3011](compiler-error-c3011.md)|wbudowany zestaw nie jest dozwolone bezpośrednio w ramach równoległego regionu|
|[Błąd kompilatora C3012](compiler-error-c3012.md)|"*funkcja*": wewnętrzna funkcja nie jest dozwolona bezpośrednio w ramach równoległego regionu|
|[Błąd kompilatora C3013](compiler-error-c3013.md)|"*klauzuli*": klauzula może występować tylko raz na OpenMP "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3014](compiler-error-c3014.md)|Oczekiwano pętli for po OpenMP "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3015](compiler-error-c3015.md)|inicjujące instrukcji "for" OpenMP posiada niewłaściwy formularz|
|[Błąd kompilatora C3016](compiler-error-c3016.md)|"*identyfikator*": zmienna index w OpenMP instrukcji "for" musi posiadać podpisany typ całkowity|
|[Błąd kompilatora C3017](compiler-error-c3017.md)|test końcowy w OpenMP instrukcji "for" posiada niewłaściwy formularz|
|[Błąd kompilatora C3018](compiler-error-c3018.md)|"*identyfikator*": OpenMP "for" test lub inkrementacja musi użyć zmiennej index "*zmiennej*"|
|[Błąd kompilatora C3019](compiler-error-c3019.md)|inkrementacja w OpenMP instrukcji "for" posiada niewłaściwy formularz|
|[Błąd kompilatora C3020](compiler-error-c3020.md)|"*zmiennej*": zmienna index OpenMP pętli "for" nie może być modyfikowana w ciele pętli|
|[Błąd kompilatora C3021](compiler-error-c3021.md)|"*argument*": argument jest pusty w OpenMP "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3022](compiler-error-c3022.md)|"*dyrektywy*": nieprawidłowy harmonogramie typu z "*dyrektywy*"na OpenMP"*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3023](compiler-error-c3023.md)|"*argument*": Napotkano nieoczekiwany token w argumencie OpenMP "*dyrektywy*" klauzuli|
|[Błąd kompilatora C3024](compiler-error-c3024.md)|"schedule(runtime)": wyrażenie chunk_size nie jest dozwolone.|
|[Błąd kompilatora C3025](compiler-error-c3025.md)|"*klauzuli*": Oczekiwano wyrażenia typu całkowitego|
|[Błąd kompilatora C3026](compiler-error-c3026.md)|"*klauzuli*": stałe wyrażenie musi być dodatnią|
|[Błąd kompilatora C3027](compiler-error-c3027.md)|"*klauzuli*": Oczekiwano wyrażenia arytmetycznego lub wskaźnikowego|
|[Błąd kompilatora C3028](compiler-error-c3028.md)|"*elementu członkowskiego*": tylko członek zmienna lub statyczny danych mogą być używane w klauzuli udostępniania danych|
|[Błąd kompilatora C3029](compiler-error-c3029.md)|"*symbol*": może wystąpić tylko raz w udostępnianie danych klauzule OpenMP — dyrektywa|
|[Błąd kompilatora C3030](compiler-error-c3030.md)|"*identyfikator*": zmienna w "*dyrektywy*" klauzuli/dyrektywie nie może mieć typu referencyjnego|
|[Błąd kompilatora C3031](compiler-error-c3031.md)|"*identyfikator*": zmienna w klauzuli "reduction" musi mieć typ arytmetyczny skalarne|
|[Błąd kompilatora C3032](compiler-error-c3032.md)|"*identyfikator*": zmienna w "*klauzuli*"klauzuli nie może posiadać niekompletnego typu"*typu*"|
|[Błąd kompilatora C3033](compiler-error-c3033.md)|"*identyfikator*": zmienna w "*klauzuli*" klauzuli nie może mieć kwalifikowanego typu const|
|[Błąd kompilatora C3034](compiler-error-c3034.md)|OpenMP "*dyrektywy*" dyrektywy nie może być bezpośrednio zagnieżdżony w"*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3035](compiler-error-c3035.md)|OpenMP "ordered" "For" lub "parallel for" OpenMP musi powiązać bezpośrednio do dyrektywy z klauzulą "ordered"|
|[Błąd kompilatora C3036](compiler-error-c3036.md)|"*klauzuli*": nieprawidłowy token operatora w klauzuli "Reduction" OpenMP|
|[Błąd kompilatora C3037](compiler-error-c3037.md)|"*identyfikator*": zmienna w "*klauzuli*" klauzuli musi być udostępniona w załączonym kontekście|
|[Błąd kompilatora C3038](compiler-error-c3038.md)|"*identyfikator*": zmienna w klauzuli "private" nie może być zmienną redukcyjną w załączonym kontekście|
|[Błąd kompilatora C3039](compiler-error-c3039.md)|"*identyfikator*": zmienna index w OpenMP instrukcji "for" nie może być zmienną redukcyjną|
|[Błąd kompilatora C3040](compiler-error-c3040.md)|"*identyfikator*": typ zmiennej w klauzuli "reduction" jest niezgodny z operatorem redukcji "*operator*"|
|[Błąd kompilatora C3041](compiler-error-c3041.md)|"*identyfikator*": zmienna w klauzuli "copyprivate" musi być prywatna w załączonym kontekście|
|[Błąd kompilatora C3042](compiler-error-c3042.md)|klauzule "copyprivate" i "nowait" nie może występować razem w OpenMP "*dyrektywy*" — dyrektywa|
|[Błąd kompilatora C3043](compiler-error-c3043.md)|Dyrektywa "critical" OpenMP nie może być zagnieżdżone w dyrektywie "critical" o tej samej nazwie|
|[Błąd kompilatora C3044](compiler-error-c3044.md)|"section": dozwolona tylko bezpośrednio zagnieżdżona pod dyrektywą "sections" OpenMP|
|[Błąd kompilatora C3045](compiler-error-c3045.md)|Oczekiwano złożonej instrukcji po dyrektywie "Sections" OpenMP. Brakuje "{"|
|[Błąd kompilatora C3046](compiler-error-c3046.md)|Brak bloku strukturalnego w regionie "#pragma omp sections" OpenMP|
|[Błąd kompilatora C3047](compiler-error-c3047.md)|Blok strukturalny w regionie "sections" musi być poprzedzony przez "#pragma omp section" OpenMP|
|[Błąd kompilatora C3048](compiler-error-c3048.md)|Wyrażenie po "#pragma omp niepodzielny" posiada niewłaściwy formularz|
|[Błąd kompilatora C3049](compiler-error-c3049.md)|"*argument*": nieprawidłowy argument w klauzuli "default" OpenMP|
|[Błąd kompilatora C3050](compiler-error-c3050.md)|"*klasy*": klasa ref nie może dziedziczyć po "*identyfikator*"|
|C3051 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3052](compiler-error-c3052.md)|"*identyfikator*": zmienna nie pojawia się w klauzuli udostępniania danych pod klauzulą default(none)|
|[Błąd kompilatora C3053](compiler-error-c3053.md)|"*identyfikator*": "threadprivate" jest prawidłowy tylko dla globalnych lub statycznych elementów danych|
|[Błąd kompilatora C3054](compiler-error-c3054.md)|"#pragma omp parallel" nie jest obecnie obsługiwane w generycznej klasie lub funkcji|
|[Błąd kompilatora C3055](compiler-error-c3055.md)|"*identyfikator*": symbol nie może być przywoływany przed jego użyciem w dyrektywie "threadprivate"|
|[Błąd kompilatora C3056](compiler-error-c3056.md)|"*identyfikator*": symbol nie jest w tym samym zakresie z dyrektywą "threadprivate"|
|[Błąd kompilatora C3057](compiler-error-c3057.md)|"*identyfikator*": dynamiczna Inicjalizacja symboli "threadprivate" nie jest obecnie obsługiwany.|
|[Błąd kompilatora C3058](compiler-error-c3058.md)|"*identyfikator*": symbol niezadeklarowany jako "threadprivate" przed jego użyciem w klauzuli "copyin"|
|[Błąd kompilatora C3059](compiler-error-c3059.md)|"*identyfikator*": symbol "threadprivate" nie może być używany w "*klauzuli*" klauzuli|
|[Błąd kompilatora C3060](compiler-error-c3060.md)|"*identyfikator*": funkcja zaprzyjaźniona nie może być zdefiniowana wewnątrz klasy przy użyciu nazwy kwalifikowanej (go może być tylko zadeklarowana)|
|C3061 błąd kompilatora|operator "*operator*": nie jest dozwolony w wyliczeniu '*typu*"z typem bazowym"*typu*"|
|[Błąd kompilatora C3062](compiler-error-c3062.md)|"*identyfikator*': moduł wyliczający wymaga wartości, ponieważ podstawowy typ to"*typu*"|
|[Błąd kompilatora C3063](compiler-error-c3063.md)|operator "*operator*": wszystkie operandy muszą posiadać ten sam typ wyliczeniowy|
|C3064 błąd kompilatora|"*identyfikator*": musi być typu prostego lub rozwiązania do jednego|
|[Błąd kompilatora C3065](compiler-error-c3065.md)|Deklaracja właściwości w zakresie nieklasowym nie jest dozwolone.|
|[Błąd kompilatora C3066](compiler-error-c3066.md)|istnieje wiele sposobów, że obiekt tego typu może być wywoływana z tymi argumentami|
|C3067 błąd kompilatora|Lista inicjalizatora nie można używać z wbudowanym operatorem]|
|[Błąd kompilatora C3068](compiler-error-c3068.md)|"*identyfikator*": funkcja "naked" nie może zawierać obiekty, które wymagałyby rozwinięcia gdy wystąpi wyjątek C++|
|[Błąd kompilatora C3069](compiler-error-c3069.md)|operator "*operator*": niedozwolone dla typu wyliczenia|
|[Błąd kompilatora C3070](compiler-error-c3070.md)|"*identyfikator*": właściwość ma metodę "set"|
|[Błąd kompilatora C3071](compiler-error-c3071.md)|operator "*operator*" może być stosowany tylko do wystąpienia klasy ref lub typu wartościowego|
|[Błąd kompilatora C3072](compiler-error-c3072.md)|operator "*operator*" nie można zastosować do wystąpienia klasy operatora jednoargumentowego "%" by skonwertować wystąpienie ref dla typu uchwytu korzystania z klasy ref|
|[Błąd kompilatora C3073](compiler-error-c3073.md)|"*identyfikator*": klasa ref nie ma konstruktora kopiującego zdefiniowane przez użytkownika|
|C3074 błąd kompilatora|Nie można zainicjować tablicy za pomocą inicjalizatora w nawiasach okrągłych|
|[Błąd kompilatora C3075](compiler-error-c3075.md)|"*identyfikator*": nie można osadzić wystąpienia typu referencyjnego "*typu*", w typie wartości|
|[Błąd kompilatora C3076](compiler-error-c3076.md)|"*identyfikator*": nie można osadzić wystąpienia typu referencyjnego "*typu*", w typie natywnym|
|[Błąd kompilatora C3077](compiler-error-c3077.md)|"*identyfikator*": finalizator może być tylko elementem członkowskim typu referencyjnego|
|C3078 błąd kompilatora|w nowych wyrażeniach należy określić rozmiar tablicy|
|C3079 błąd kompilatora|Lista inicjalizatora nie może służyć jako prawy argument operacji operatora przypisania|
|[Błąd kompilatora C3080](compiler-error-c3080.md)|"*finalizator*": finalizator nie może mieć — Specyfikator klasy magazynu-|
|C3081 błąd kompilatora|Nieaktualne.|
|C3082 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3083](compiler-error-c3083.md)|"*identyfikator*": symbol po lewej '::' musi być typem|
|[Błąd kompilatora C3084](compiler-error-c3084.md)|"*identyfikator*": destruktor/finalizator nie może być "*— słowo kluczowe*"|
|[Błąd kompilatora C3085](compiler-error-c3085.md)|"*identyfikator*": Konstruktor nie może być "*— słowo kluczowe*"|
|C3086 błąd kompilatora|Nie można odnaleźć "std::initializer_list": należy #include < initializer_list >|
|[Błąd kompilatora C3087](compiler-error-c3087.md)|"*identyfikator*": wywołanie "*deklaracji*" już inicjalizuje ten element członkowski|
|C3088 błąd kompilatora|"*klasy*": atrybut konstruktora musi posiadać nazwane argumenty formalne|
|C3089 błąd kompilatora|"*identyfikator*": Nazwa parametru jest niezgodna z nazwą każdy członek danych|
|C3090 błąd kompilatora|"*klasy*": atrybut klasy nie może być szablonem|
|C3091 błąd kompilatora|"*klasy*": atrybut klasy nie może mieć klas podstawowych|
|C3092 błąd kompilatora|"*klasy*": element członkowski klasy atrybutu nie może być nieco pola, "static" lub "const"|
|C3093 błąd kompilatora|"*typu*": typ nie jest dozwolony dla atrybutu klasy elementu członkowskiego "*elementu członkowskiego*"|
|[Błąd kompilatora C3094](compiler-error-c3094.md)|"*atrybutu*": anonimowe użycie nie jest dozwolone|
|[Błąd kompilatora C3095](compiler-error-c3095.md)|"*atrybutu*": atrybut nie może powtarzać|
|[Błąd kompilatora C3096](compiler-error-c3096.md)|"*atrybutu*": atrybut jest dozwolony w elementach członkowskich danych atrybutu klas|
|[Błąd kompilatora C3097](compiler-error-c3097.md)|"*atrybutu*": atrybut musi być do zakresu "zestawu:" lub "module:"|
|C3098 błąd kompilatora|"*identyfikator*": atrybut nie ma konstruktorów zdefiniowanych przez użytkownika|
|[Błąd kompilatora C3099](compiler-error-c3099.md)|"*— słowo kluczowe*": Użyj [System::AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] dla atrybutów managed WinRT|
