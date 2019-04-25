---
title: Błędy kompilatora od C3100 do C3199
ms.date: 04/21/2019
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: efa3207a9fdfb81a52bf319a1cbc2da84084b6cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281658"
---
# <a name="compiler-errors-c3100-through-c3199"></a>Błędy kompilatora od C3100 do C3199

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C3100](compiler-error-c3100.md)|"*identyfikator*": nieznany kwalifikator atrybutu|
|[Błąd kompilatora C3101](compiler-error-c3101.md)|Niedozwolone wyrażenie nazwanego argumentu atrybutu "*identyfikator*"|
|Błąd kompilatora C3102|Nieaktualne.|
|[Błąd kompilatora C3103](compiler-error-c3103.md)|"*identyfikator*": powtarzający się nazwany argument|
|[Błąd kompilatora C3104](compiler-error-c3104.md)|Niedozwolony argument atrybutu|
|Błąd kompilatora C3105|"*symbol*": nie można użyć jako atrybutu|
|[Błąd kompilatora C3106](compiler-error-c3106.md)|"*atrybut*": nienazwane argumenty muszą poprzedzać nazwane argumenty|
|Błąd kompilatora C3107|"*atrybut*": funkcje składowe atrybutów natywnych nie może być zdefiniowana|
|Błąd kompilatora C3108|Nie można określić typu, ponieważ lista inicjalizatora nie jest wyrażeniem|
|Błąd kompilatora C3109|"*identyfikator*": metody interfejsu muszą używać "__stdcall" lub "__cdecl" konwencji wywoływania|
|[Błąd kompilatora C3110](compiler-error-c3110.md)|"*funkcja*": nie można przeciążyć metody interfejsu COM|
|Błąd kompilatora C3111|Nie można użyć listy inicjalizatora jako domyślnego argumentu dla parametru szablonu|
|Błąd kompilatora C3112|"*interfejsu*": interfejs może zostać zadeklarowany globalnie lub zakresie przestrzeni nazw|
|[Błąd kompilatora C3113](compiler-error-c3113.md)|"interfejs/enum" nie może być szablon/ogólne|
|[Błąd kompilatora C3114](compiler-error-c3114.md)|"*identyfikator*": nie jest prawidłowym argumentem nazwanego atrybutu|
|[Błąd kompilatora C3115](compiler-error-c3115.md)|"*atrybut*": ten atrybut nie jest dozwolona na "*konstruowania*"|
|[Błąd kompilatora C3116](compiler-error-c3116.md)|"*specyfikator*": nieprawidłowa klasa magazynu dla metody interfejsu|
|[Błąd kompilatora C3117](compiler-error-c3117.md)|"*interfejsu*": interfejs może mieć tylko jedną klasę bazową|
|[Błąd kompilatora C3118](compiler-error-c3118.md)|"*interfejsu*": interfejsy nie obsługują wirtualnego dziedziczenia|
|Błąd kompilatora C3119|Funkcja alignas(void) jest niedozwolona|
|[Błąd kompilatora C3120](compiler-error-c3120.md)|"*identyfikator*": metody interfejsu nie może mieć zmiennej listy argumentów|
|[Błąd kompilatora C3121](compiler-error-c3121.md)|Nie można zmienić identyfikatora GUID dla klasy*klasy*"|
|Błąd kompilatora C3122|"*interfejsu*": ogólny interfejs WinRT nie może mieć identyfikatora GUID|
|Błąd kompilatora C3123|Generyczny interfejs WinRT nie może mieć ograniczeń|
|Błąd kompilatora C3124|"signed char" nie jest prawidłowym typem danych WinRT. Zamiast tego użyj "unsigned char", "wchar_t" lub "signed short".|
|Błąd kompilatora C3125|"*typu*": typ nie może bezpośrednio ani pośrednio dziedziczyć po "Platform::Exception"|
|[Błąd kompilatora C3126](compiler-error-c3126.md)|Nie można zdefiniować związku "*Unii*"wewnątrz typu zarządzanego WinRT"*typu*"|
|Błąd kompilatora C3127|"*typu*": "*cech*" cech należy używać tylko w klasie ref WinRT|
|Błąd kompilatora C3128|"*typu*"nie ma wartości vtable, która została wprowadzona przez"*typu*"|
|Błąd kompilatora C3129|"*typu*": __default_vptr_for_base należy używać tylko na lokalnie zdefiniowanych typach polimorficznych i podstawowych|
|[Błąd kompilatora C3130](compiler-error-c3130.md)|Błąd wewnętrzny kompilatora: nie można zapisać wstrzykniętego bloku kodu do PDB|
|[Błąd kompilatora C3131](compiler-error-c3131.md)|Projekt musi mieć atrybut "module" z właściwością "name"|
|[Błąd kompilatora C3132](compiler-error-c3132.md)|"*parametr*": tablice parametrów można stosować tylko do formalnego argumentu typu Jednowymiarowa tablica zarządzana WinRT|
|[Błąd kompilatora C3133](compiler-error-c3133.md)|Nie można zastosować atrybutów do C++ varargs|
|[Błąd kompilatora C3134](compiler-error-c3134.md)|"*wartość*": wartość argumentu atrybutu "*argument*"nie ma prawidłowego typu"*typu*"|
|[Błąd kompilatora C3135](compiler-error-c3135.md)|"*identyfikator*": właściwość nie może mieć typu "const" lub "volatile" wpisz|
|[Błąd kompilatora C3136](compiler-error-c3136.md)|"*interfejsu*": interfejs COM może dziedziczyć tylko z innego interfejsu COM "*interfejsu*" nie jest interfejsem COM|
|[Błąd kompilatora C3137](compiler-error-c3137.md)|"*identyfikator*": nie można zainicjować właściwości|
|[Błąd kompilatora C3138](compiler-error-c3138.md)|"*identyfikator*": "*atrybut*" interfejs musi dziedziczyć z interfejsu IDispatch lub interfejs, który dziedziczy z IDispatch|
|[Błąd kompilatora C3139](compiler-error-c3139.md)|"*typu*": nie można eksportować UDT bez składowych|
|[Błąd kompilatora C3140](compiler-error-c3140.md)|nie może mieć wiele atrybutów "module" w tej samej jednostce kompilacyjnej|
|[Błąd kompilatora C3141](compiler-error-c3141.md)|"*interfejsu*": interfejsy obsługują tylko publiczne dziedziczenie|
|[Błąd kompilatora C3142](compiler-error-c3142.md)|"*właściwość*": nie można przyjąć adresu właściwości|
|Błąd kompilatora C3143|"*argument*": argument atrybutu nie może mieć wiele wartości|
|Błąd kompilatora C3144|"*atrybut*": atrybut wymaga jawnych argumentów "*argument*" jest bez nazwy|
|[Błąd kompilatora C3145](compiler-error-c3145.md)|"*identyfikator*": zmienną globalną lub statyczną nie może być typu zarządzanego WinRT "*typu*"|
|Błąd kompilatora C3146|Nieaktualne.|
|Błąd kompilatora C3147|Nieaktualne.|
|Błąd kompilatora C3148|Nieaktualne.|
|[Błąd kompilatora C3149](compiler-error-c3149.md)|"*typu*": nie można użyć tego typu, w tym miejscu bez najwyższego poziomu "*tokenu*"|
|[Błąd kompilatora C3150](compiler-error-c3150.md)|"*konstruowania*": "*atrybut*" mogą być stosowane tylko do klasy, struktury, interfejsu, tablicy lub wskaźnika|
|Błąd kompilatora C3151|Nieaktualne.|
|[Błąd kompilatora C3152](compiler-error-c3152.md)|"*funkcja*": "*— słowo kluczowe*" mogą być stosowane tylko do klasy, struktury lub wirtualnej funkcji składowej|
|[Błąd kompilatora C3153](compiler-error-c3153.md)|"*interfejsu*": nie można utworzyć instancji interfejsu|
|[Błąd kompilatora C3154](compiler-error-c3154.md)|Oczekiwano "," przed wielokropkiem. Non-przecinkami wielokropka nie jest obsługiwany przez funkcje tablicy parametrów.|
|[Błąd kompilatora C3155](compiler-error-c3155.md)|atrybuty nie są dozwolone w właściwości indeksatora|
|[Błąd kompilatora C3156](compiler-error-c3156.md)|"*klasy*": nie można posiadać lokalnej definicji typu zarządzanego WinRT|
|[Błąd kompilatora C3157](compiler-error-c3157.md)|Atrybut ParamArray można stosować tylko do ostatniego parametru|
|Błąd kompilatora C3158|"*funkcja*": "*— słowo kluczowe*" może być stosowany tylko do wirtualnej funkcji składowej|
|[Błąd kompilatora C3159](compiler-error-c3159.md)|"*identyfikator*": nie można zadeklarować tablicy wskaźników do typu wartościowego|
|[Błąd kompilatora C3160](compiler-error-c3160.md)|"*typu*": składowa danych klasy zarządzane WinRT nie może mieć tego typu|
|[Błąd kompilatora C3161](compiler-error-c3161.md)|"*interfejsu*": zagnieżdżanie klasy, struktury lub interfejsu w interfejsie jest niedozwolone; zagnieżdżanie interfejsu w klasie lub strukturze jest niedozwolone|
|[Błąd kompilatora C3162](compiler-error-c3162.md)|"*typu*": typ odwołania, który ma destruktor nie można użyć jako typu statycznej składowej danych "*elementu członkowskiego*"|
|[Błąd kompilatora C3163](compiler-error-c3163.md)|"*klasy*": atrybuty niespójne z poprzednią deklaracją|
|Błąd kompilatora C3164|Nieaktualne.|
|Błąd kompilatora C3165|"*wartość*": nie można przekonwertować na wartość całkowitą lub zmiennoprzecinkową|
|[Błąd kompilatora C3166](compiler-error-c3166.md)|Nieaktualne. "*typu*": składowa danych klasy zarządzane WinRT nie może mieć typu "*pointer_type* do wnętrza *managed_pointer_type*"|
|[Błąd kompilatora C3167](compiler-error-c3167.md)|Nie można zainicjalizować .NET Framework: Upewnij się, że jest zainstalowany|
|[Błąd kompilatora C3168](compiler-error-c3168.md)|"*typu*": niedozwolony typ podstawowy dla wyliczenia|
|Błąd kompilatora C3169|"*typu*": nie można ustalić typu "auto" z "*typu*"|
|[Błąd kompilatora C3170](compiler-error-c3170.md)|nie może posiadać innych identyfikatorów modułu w projekcie|
|[Błąd kompilatora C3171](compiler-error-c3171.md)|"*modułu*": nie można określić innych atrybutów modułu w projekcie|
|[Błąd kompilatora C3172](compiler-error-c3172.md)|"*identyfikator*": nie można określić innych atrybutów idl_module w projekcie|
|[Błąd kompilatora C3173](compiler-error-c3173.md)|Niezgodność wersji w scaleniu idl|
|[Błąd kompilatora C3174](compiler-error-c3174.md)|Moduł atrybut nie został określony.|
|[Błąd kompilatora C3175](compiler-error-c3175.md)|"*funkcja*": nie można wywołać metody typu zarządzanego z niezarządzanej funkcji "*funkcja*"|
|[Błąd kompilatora C3176](compiler-error-c3176.md)|"*typu*": nie można zadeklarować lokalnego typu wartościowego|
|Błąd kompilatora C3177|nie może mieć funkcji konwersji do typu zawierającego "*typu*"|
|Błąd kompilatora C3178|"*typu*": nie można używać ParamArray w funkcji z argumentami domyślnymi|
|[Błąd kompilatora C3179](compiler-error-c3179.md)|Nienazwany typ zarządzany WinRT nie jest dozwolony|
|[Błąd kompilatora C3180](compiler-error-c3180.md)|"*typu*': nazwa przekracza limit meta-data"*numer*"znaków|
|[Błąd kompilatora C3181](compiler-error-c3181.md)|"*typu*": nieprawidłowy operand dla *— operator*|
|[Błąd kompilatora C3182](compiler-error-c3182.md)|"*typu*": elementu członkowskiego deklaracji using lub deklaracja dostępu jest niedozwolona w ramach typu zarządzanego WinRT|
|[Błąd kompilatora C3183](compiler-error-c3183.md)|Nie można zdefiniować nienazwanej klasy, struktury lub związku wewnątrz typu zarządzanego WinRT "*klasy*"|
|Błąd kompilatora C3184|Nieaktualne.|
|[Błąd kompilatora C3185](compiler-error-c3185.md)|"typeid": używany na typie managed WinRT "*typu*", użyj "*operator*" zamiast niego|
|Błąd kompilatora C3186|Nieaktualne.|
|[Błąd kompilatora C3187](compiler-error-c3187.md)|"*identyfikator*": jest dostępny tylko w treści funkcji|
|Błąd kompilatora C3188|Nieaktualne.|
|[Błąd kompilatora C3189](compiler-error-c3189.md)|"typeid <*deklaratora*>": Ta składnia nie jest już obsługiwane, w niej użyć:: TypeID zamiast tego|
|[Błąd kompilatora C3190](compiler-error-c3190.md)|"*deklaratora*"z argumentami podanymi przez szablon nie jest jawnym utworzeniem wystąpienia jakiejkolwiek funkcji składowej"*typu*"|
|Błąd kompilatora C3191|Nieaktualne.|
|[Błąd kompilatora C3192](compiler-error-c3192.md)|Błąd składniowy: "^" nie jest operatorem prefiksowym (Czy chodziło Ci o "*"?)|
|Błąd kompilatora C3193|"*konstruowania*": wymaga "/ clr" lub "/ ZW" opcja wiersza polecenia|
|[Błąd kompilatora C3194](compiler-error-c3194.md)|"*typu*": typ wartościowy nie może mieć operatora przypisania|
|[Błąd kompilatora C3195](compiler-error-c3195.md)|"*— słowo kluczowe*": jest zarezerwowany i nie można użyć jako elementem członkowskim klasy lub wartości typu ref. CLR/WinRT operatory muszą być zdefiniowane przy użyciu słowa kluczowego 'operator'|
|[Błąd kompilatora C3196](compiler-error-c3196.md)|"*identyfikator*": użyto więcej niż raz|
|[Błąd kompilatora C3197](compiler-error-c3197.md)|"*— słowo kluczowe*": należy używać tylko w definicjach|
|[Błąd kompilatora C3198](compiler-error-c3198.md)|Nieprawidłowe użycie zmiennoprzecinkowych pragm: fenv_access pragma działa tylko w trybie ścisłym|
|[Błąd kompilatora C3199](compiler-error-c3199.md)|Nieprawidłowe użycie zmiennoprzecinkowych pragm: wyjątki nie są obsługiwane w trybie ścisłym|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
