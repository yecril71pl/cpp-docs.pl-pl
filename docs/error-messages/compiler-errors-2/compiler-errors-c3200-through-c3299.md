---
title: C3200 błędy kompilatora za pośrednictwem C3299 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
helpviewer_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
dev_langs:
- C++
ms.assetid: 6b3104f6-63bc-4823-b6f3-b8a16be4b87f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 831f51981ff72a67a55698693514dce0a3d87535
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-errors-c3200-through-c3299"></a>C3200 błędy kompilatora za pośrednictwem C3299

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C3200](compiler-error-c3200.md)|"*typu*": nieprawidłowy argument szablonu dla parametru szablonu "*parametru*", oczekiwano szablonu klasy|
|[Błąd kompilatora C3201](compiler-error-c3201.md)|Lista parametrów szablonu dla szablonu klasy "*szablonu*"nie odpowiada liście parametrów szablonu dla parametru szablonu"*parametru*"|
|[Błąd kompilatora C3202](compiler-error-c3202.md)|"*identyfikator*": nieprawidłowy domyślny argument, oczekiwano szablonu klasy|
|[Błąd kompilatora C3203](compiler-error-c3203.md)|"*identyfikator*": klasy niespecjalizowanej klasy szablonu/ogólny nie może służyć jako argument szablonu/ogólnego parametru szablonu/ogólne "*parametru*", oczekiwano typu rzeczywistego|
|[Błąd kompilatora C3204](compiler-error-c3204.md)|"*funkcja*" nie może zostać wywołane z wnętrza bloku catch|
|[Błąd kompilatora C3205](compiler-error-c3205.md)|Lista argumentów dla szablonu parametru szablonu "*identyfikator*" Brak|
|[Błąd kompilatora C3206](compiler-error-c3206.md)|"*funkcja*": argument nieprawidłowy szablon/ogólne "*szablonu*", brakuje listy argumentów szablonu/ogólnej klasy szablonu/ogólnego "*typu*"|
|[Błąd kompilatora C3207](compiler-error-c3207.md)|"*funkcja*": nieprawidłowy argument szablonu dla "*parametru*", oczekiwano szablonu klasy|
|[Błąd kompilatora C3208](compiler-error-c3208.md)|"*funkcja*": lista parametrów szablonu dla szablonu klasy "*szablonu*"nie odpowiada liście parametrów szablonu dla szablonu parametru szablonu"*parametru*"|
|[Błąd kompilatora C3209](compiler-error-c3209.md)|"*typu*": klasa generyczna musi być klasą managed WinRT|
|[Błąd kompilatora C3210](compiler-error-c3210.md)|"*identyfikator*": deklaracja dostępu można stosować tylko do elementu członkowskiego klasy podstawowej|
|[Błąd kompilatora C3211](compiler-error-c3211.md)|"*funkcja*": jawna specjalizacja używa składni częściowej specjalizacji, użyj szablonu <>|
|[Błąd kompilatora C3212](compiler-error-c3212.md)|"*funkcja*": jawna specjalizacja szablonu elementu członkowskiego musi być elementem członkowskim jawnej specjalizacji|
|[Błąd kompilatora C3213](compiler-error-c3213.md)|Klasa podstawowa*klasy*"jest mniej dostępny niż"*derived_class*"|
|[Błąd kompilatora C3214](compiler-error-c3214.md)|"*argument*": nieprawidłowy typ argumentu dla parametru ogólnego "*parametru*"z ogólnego"*typu*", nie spełnia ograniczenia "*ograniczenia*'|
|[Błąd kompilatora C3215](compiler-error-c3215.md)|"*constraint1*": parametr typu generycznego już ograniczony przez "*constraint2*"|
|[Błąd kompilatora C3216](compiler-error-c3216.md)|ograniczenie musi być parametrem generycznym, nie "*typu*"|
|[Błąd kompilatora C3217](compiler-error-c3217.md)|"*parametru*": parametr generyczny nie ograniczony w tej deklaracji|
|[Błąd kompilatora C3218](compiler-error-c3218.md)|"*typu*": typ nie jest dozwolony jako ograniczenia|
|[Błąd kompilatora C3219](compiler-error-c3219.md)|"*parametru*": parametr ogólny nie może zostać ograniczony przez wiele elementów niebędących interfejsami: "*typu*"|
|C3220 błąd kompilatora|"*interfejsu*": interfejs nie może mieć identyfikatora progid|
|C3221 błąd kompilatora|"*elementu członkowskiego*": wiele "default" i "case" atrybuty nie są dozwolone dla elementu członkowskiego|
|[Błąd kompilatora C3222](compiler-error-c3222.md)|"*funkcja*": nie można zadeklarować domyślnych argumentów dla elementu członkowskiego ogólnego lub funkcji typu zarządzanego WinRT|
|[Błąd kompilatora C3223](compiler-error-c3223.md)|"*właściwości*": nie można zastosować "typeid" do właściwości|
|[Błąd kompilatora C3224](compiler-error-c3224.md)|"*typu*": nie ma przeciążonej klasy generycznej*numer*"argumenty typu ogólnego|
|[Błąd kompilatora C3225](compiler-error-c3225.md)|argument typu generycznego dla "*argument*nie może być*typu*", musi być typem wartościowym lub uchwytem do typu odwołania|
|[Błąd kompilatora C3226](compiler-error-c3226.md)|Deklaracja szablonu nie jest dozwolona wewnątrz deklaracji ogólnej|
|[Błąd kompilatora C3227](compiler-error-c3227.md)|"*typu*": nie można użyć "*operator*" przydzielić typu ogólnego|
|[Błąd kompilatora C3228](compiler-error-c3228.md)|"*funkcja*": argument Typ generycznego dla "*argument*nie może być*typu*", musi być typem wartości lub typ dojścia|
|[Błąd kompilatora C3229](compiler-error-c3229.md)|"*typu*": operatory pośrednie dla parametru typu generycznego nie są dozwolone.|
|[Błąd kompilatora C3230](compiler-error-c3230.md)|"*funkcja*": argument typu szablonu dla "*argument*" nie może zawierać parametru typu ogólnego: "*typu*"|
|[Błąd kompilatora C3231](compiler-error-c3231.md)|"*typu*": argument typu szablonu nie można użyć parametru typu ogólnego|
|[Błąd kompilatora C3232](compiler-error-c3232.md)|"*parametru*": nie można użyć parametru typu ogólnego w kwalifikowanej nazwie|
|[Błąd kompilatora C3233](compiler-error-c3233.md)|"*typu*": parametr typu generycznego już ograniczony|
|[Błąd kompilatora C3234](compiler-error-c3234.md)|Klasa generyczna nie może pochodzić z parametru typu ogólnego|
|[Błąd kompilatora C3235](compiler-error-c3235.md)|"*specjalizacji*": jawna lub częściowa specjalizacja klasy generycznej jest niedozwolona.|
|[Błąd kompilatora C3236](compiler-error-c3236.md)|jawne utworzenie wystąpienia generycznego jest niedozwolone.|
|[Błąd kompilatora C3237](compiler-error-c3237.md)|"*klasy*": klasa generyczna nie może być atrybutem niestandardowym|
|[Błąd kompilatora C3238](compiler-error-c3238.md)|"*typu*": typ o tej nazwie już został przesłany dalej do zestawu "*zestawu*"|
|[Błąd kompilatora C3239](compiler-error-c3239.md)|"*typu*": wskaźnik do wskaźnika wnętrza/pin jest niedozwolony przez środowisko uruchomieniowe języka wspólnego|
|[Błąd kompilatora C3240](compiler-error-c3240.md)|"*identyfikator*": musi być nieprzeciążoną abstrakcyjną funkcją członkowską "*typu*"|
|[Błąd kompilatora C3241](compiler-error-c3241.md)|"*elementu członkowskiego*": Ta metoda nie została wprowadzona przez "*interfejsu*"|
|[Błąd kompilatora C3242](compiler-error-c3242.md)|"*funkcja*": tylko jawnie można przesłonić funkcje wirtualne|
|[Błąd kompilatora C3243](compiler-error-c3243.md)|żadna z funkcji przeciążonych nie została wprowadzona przez "*interfejsu*"|
|[Błąd kompilatora C3244](compiler-error-c3244.md)|"*elementu członkowskiego*": Ta metoda została wprowadzona przez "*interface1*"nie przez"*interface2*"|
|C3245 błąd kompilatora|"*funkcja*": użycie szablonu zmiennej wymaga listy argumentów szablonu|
|[Błąd kompilatora C3246](compiler-error-c3246.md)|"*klasy*": nie może dziedziczyć po "*base_class*"ponieważ został on zadeklarowany jako"*dziedziczenia*"|
|[Błąd kompilatora C3247](compiler-error-c3247.md)|"*coclass*": klasa coclass nie może dziedziczyć po innej klasie coclass*base_class*"|
|[Błąd kompilatora C3248](compiler-error-c3248.md)|Nieaktualne. "*funkcja*": funkcja zadeklarowana jako "sealed" nie może być zastąpione przez "*funkcja*"|
|C3249 błąd kompilatora|Niedozwolona instrukcja lub Podwyrażenie dla funkcji "constexpr"|
|C3250 błąd kompilatora|"*deklaracji*": deklaracja nie jest dozwolona w treści funkcji "constexpr"|
|[Błąd kompilatora C3251](compiler-error-c3251.md)|Nie można wywołać metody klasy podstawowej dla instancji typu wartościowego|
|[Błąd kompilatora C3252](compiler-error-c3252.md)|"*funkcja*": nie można zredukować dostępności wirtualnej metody w typie managed WinRT|
|[Błąd kompilatora C3253](compiler-error-c3253.md)|"*funkcja*": błąd z jawnym przesłanianiem|
|[Błąd kompilatora C3254](compiler-error-c3254.md)|"*funkcja*": klasa zawiera jawne przesłonięcie "*funkcja*", ale nie pochodzi z interfejsu, który zawiera deklarację funkcji|
|[Błąd kompilatora C3255](compiler-error-c3255.md)|"*typu*": nie można dynamicznie przydzielić tego obiektu typu wartościowego na natywnej stercie|
|C3256 błąd kompilatora|"*funkcja*": użycie zmiennej nie tworzy wyrażenie stałe|
|C3257 błąd kompilatora|Nieaktualne.|
|C3258 błąd kompilatora|Nieaktualne.|
|C3259 błąd kompilatora|funkcje "constexpr" może mieć tylko jedną instrukcję return|
|C3260 błąd kompilatora|"*tokenu*": pomijanie nieoczekiwanych tokenów przed treścią operatora lambda|
|C3261 błąd kompilatora|funkcja zwracająca tablicę managed WinRT musi mieć nawiasy kwadratowe na końcu deklaracji: "*identyfikator*(...) []'|
|[Błąd kompilatora C3262](compiler-error-c3262.md)|Nieprawidłowe indeksowanie tablicy: *numer* wymiar(y) określony(e) dla *numer*-wymiarowej "*typu*"|
|C3263 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3264](compiler-error-c3264.md)|"*identyfikator*": konstruktor klasy nie może posiadać typu zwracanego|
|[Błąd kompilatora C3265](compiler-error-c3265.md)|Nie można zadeklarować zarządzanego "*managed_construct*"w niezarządzanych"*unmanaged_construct*"|
|[Błąd kompilatora C3266](compiler-error-c3266.md)|"*funkcja*": konstruktor klasy musi mieć listę parametrów "void"|
|C3267 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3268](compiler-error-c3268.md)|"*funkcja*": funkcja generyczna lub funkcja członkowska klasy generycznej nie może mieć zmiennej listy parametrów|
|[Błąd kompilatora C3269](compiler-error-c3269.md)|"*funkcja*": nie można zadeklarować funkcji członkowskiej typu zarządzanego WinRT z "..."|
|[Błąd kompilatora C3270](compiler-error-c3270.md)|"*pola*": atrybut FieldOffset może być używany tylko w kontekście StructLayout(LayoutKind::Explicit)|
|[Błąd kompilatora C3271](compiler-error-c3271.md)|"*pola*": Nieprawidłowa wartość "*numer*" atrybutu FieldOffset|
|[Błąd kompilatora C3272](compiler-error-c3272.md)|"*symbol*": symbol wymaga FieldOffset, ponieważ jest elementem członkowskim klasy/struktury *type_name* zdefiniowanym przez StructLayout(LayoutKind::Explicit)|
|[Błąd kompilatora C3273](compiler-error-c3273.md)|"*— słowo kluczowe*": niedozwolone w bloku try C++|
|[Błąd kompilatora C3274](compiler-error-c3274.md)|na koniec /&#95;&#95;finally bez pasującego spróbuj|
|[Błąd kompilatora C3275](compiler-error-c3275.md)|"*identyfikator*": nie można użyć tego symbolu bez kwalifikatora|
|[Błąd kompilatora C3276](compiler-error-c3276.md)|"*— słowo kluczowe*": przejście poza koniec /&#95;&#95;koniec bloku ma niezdefiniowane zachowanie podczas obsługi zakończenia|
|[Błąd kompilatora C3277](compiler-error-c3277.md)|Nie można zdefiniować niezarządzanego wyliczenia "*wyliczenie*"wewnątrz zarządzanego"*typu*"|
|[Błąd kompilatora C3278](compiler-error-c3278.md)|bezpośrednie wywołanie interfejsu lub czystej metody "*funkcja*" zakończy się niepowodzeniem w czasie wykonywania|
|[Błąd kompilatora C3279](compiler-error-c3279.md)|częściowe i jawne specjalizacje jak również jawne utworzenia wystąpień szablonów klasy zadeklarowany w przestrzeni nazw cli są niedozwolone.|
|[Błąd kompilatora C3280](compiler-error-c3280.md)|"*funkcja*": funkcja członkowska typu zarządzanego nie można skompilować jako funkcji niezarządzanej|
|C3281 błąd kompilatora|"*funkcja*": globalny operator nie może mieć typu zarządzanego WinRT "*typu*" w sygnaturze|
|[Błąd kompilatora C3282](compiler-error-c3282.md)|listy generyczne parametrów mogą występować tylko w managed WinRT klasy, struktury lub funkcje|
|[Błąd kompilatora C3283](compiler-error-c3283.md)|"*interfejsu*": interfejs nie może posiadać konstruktora wystąpień|
|[Błąd kompilatora C3284](compiler-error-c3284.md)|ograniczenia dla parametru ogólnego "*parametru*"funkcji"*deklarator*"musi być zgodne z ograniczeniami dla parametru ogólnego"*parametru*"funkcji"*deklarator*"|
|[Błąd kompilatora C3285](compiler-error-c3285.md)|dla każdej instrukcji nie może działać na zmiennych typu "*typu*"|
|[Błąd kompilatora C3286](compiler-error-c3286.md)|"*specyfikator*": Zmienna iteracji nie może mieć żadnych specyfikatory klasy magazynowania|
|[Błąd kompilatora C3287](compiler-error-c3287.md)|Typ "*typu*" (typ zwrotny z GetEnumerator) musi mieć odpowiednie publicznego funkcję członkowską MoveNext oraz publiczną właściwość Current|
|[Błąd kompilatora C3288](compiler-error-c3288.md)|"*typu*": niedozwolone anulowanie odwołania do typu uchwytu|
|[Błąd kompilatora C3289](compiler-error-c3289.md)|"*identyfikator*": właściwość prosta nie może być indeksowany.|
|[Błąd kompilatora C3290](compiler-error-c3290.md)|"*typu*": właściwość prosta nie może mieć typu referencyjnego|
|[Błąd kompilatora C3291](compiler-error-c3291.md)|"default": nie może być nazwą właściwości prostej|
|[Błąd kompilatora C3292](compiler-error-c3292.md)|Nie można ponownie otworzyć przestrzeni nazw cli|
|[Błąd kompilatora C3293](compiler-error-c3293.md)|"*identyfikator*": umożliwia dostęp do domyślnej właściwości (indeksator) dla klasy "default"*klasy*"|
|C3294 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3295](compiler-error-c3295.md)|"#pragma *specyfikator*" można używać tylko globalnie lub zakresie przestrzeni nazw|
|[Błąd kompilatora C3296](compiler-error-c3296.md)|"*identyfikator*": właściwość o tej nazwie już istnieje.|
|[Błąd kompilatora C3297](compiler-error-c3297.md)|" *constraint2*": nie można użyć " *constraint1*" jako ograniczenia ponieważ " *constraint1*' posiada wartość ograniczenia|
|[Błąd kompilatora C3298](compiler-error-c3298.md)|" *constraint1*": nie można użyć " *constraint2*" jako ograniczenia ponieważ " *constraint2*" ma ograniczenie ref oraz " *constraint1*" ma wartość ograniczenia|
|[Błąd kompilatora C3299](compiler-error-c3299.md)|" *funkcja*": nie można określić ograniczeń, są one dziedziczone z metody podstawowej|
