---
title: "C3100 błędy kompilatora za pośrednictwem C3199 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
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
dev_langs:
- C++
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3cc05c482c112753ffeb52d49b1badcfcab549cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-errors-c3100-through-c3199"></a>C3100 błędy kompilatora za pośrednictwem C3199

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C3100](compiler-error-c3100.md)|"*identyfikator*': nieznany kwalifikator atrybutu|
|[Błąd kompilatora C3101](compiler-error-c3101.md)|Niedozwolone wyrażenie nazwanego argumentu atrybutu "*identyfikator*"|
|C3102 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3103](compiler-error-c3103.md)|"*identyfikator*": powtarzający się nazwany argument|
|[Błąd kompilatora C3104](compiler-error-c3104.md)|argument atrybutu niedozwolony|
|C3105 błąd kompilatora|"*symbol*": nie można użyć jako atrybutu|
|[Błąd kompilatora C3106](compiler-error-c3106.md)|"*atrybutu*": nienazwane argumenty muszą poprzedzać nazwane argumenty|
|C3107 błąd kompilatora|"*atrybutu*": funkcje Członkowskie atrybutów natywnych nie może być zdefiniowana|
|C3108 błąd kompilatora|Nie można określić typu, ponieważ lista inicjalizatora nie jest wyrażeniem|
|C3109 błąd kompilatora|"*identyfikator*": metody interfejsu muszą używać "__stdcall" lub "__cdecl" konwencji wywoływania|
|[Błąd kompilatora C3110](compiler-error-c3110.md)|"*funkcja*": nie można przeciążyć metody interfejsu COM|
|C3111 błąd kompilatora|Nie można użyć listy inicjalizatora jako domyślnego argumentu dla parametru szablonu|
|C3112 błąd kompilatora|"*interfejsu*": interfejs mogą być deklarowane tylko globalnie lub zakresie przestrzeni nazw|
|[Błąd kompilatora C3113](compiler-error-c3113.md)|"interfejsu/enum" nie może być szablonu/generic|
|[Błąd kompilatora C3114](compiler-error-c3114.md)|"*identyfikator*": nie jest prawidłowym argumentem nazwanego atrybutu|
|[Błąd kompilatora C3115](compiler-error-c3115.md)|"*atrybutu*": ten atrybut nie jest dozwolona w "*skonstruować*"|
|[Błąd kompilatora C3116](compiler-error-c3116.md)|"*specyfikator*": nieprawidłowa klasa magazynu dla metody interfejsu|
|[Błąd kompilatora C3117](compiler-error-c3117.md)|"*interfejsu*": interfejs może mieć tylko jedną klasę podstawową|
|[Błąd kompilatora C3118](compiler-error-c3118.md)|"*interfejsu*": interfejsy nie obsługują wirtualnego dziedziczenia|
|C3119 błąd kompilatora|alignas(void) jest niedozwolone.|
|[Błąd kompilatora C3120](compiler-error-c3120.md)|"*identyfikator*": metody interfejsu nie może mieć zmiennej listy argumentów|
|[Błąd kompilatora C3121](compiler-error-c3121.md)|Nie można zmienić identyfikatora GUID dla klasy*klasy*"|
|C3122 błąd kompilatora|"*interfejsu*": generyczny interfejs WinRT nie może mieć identyfikatora GUID|
|C3123 błąd kompilatora|Generyczny interfejs WinRT nie może mieć ograniczeń|
|C3124 błąd kompilatora|"signed char" nie jest prawidłowym typem danych WinRT. Zamiast tego użyj "unsigned char", "wchar_t" lub "signed short".|
|C3125 błąd kompilatora|"*typu*": typ nie może bezpośrednio ani pośrednio dziedziczyć po "Platform::Exception"|
|[Błąd kompilatora C3126](compiler-error-c3126.md)|Nie można zdefiniować związku "*Unii*"wewnątrz typu managed WinRT"*typu*"|
|C3127 błąd kompilatora|"*typu*": "*cechy*" cechy można używać tylko w klasie ref WinRT|
|C3128 błąd kompilatora|"*typu*"nie ma wartości vtable, która została wprowadzona przez"*typu*"|
|C3129 błąd kompilatora|"*typu*": __default_vptr_for_base można używać tylko na lokalnie zdefiniowanych typach polimorficznych i podstawowych|
|[Błąd kompilatora C3130](compiler-error-c3130.md)|Wewnętrzny błąd kompilatora: nie można zapisać wstrzykniętego bloku kodu do PDB|
|[Błąd kompilatora C3131](compiler-error-c3131.md)|Projekt musi mieć atrybut "module" z właściwością "name"|
|[Błąd kompilatora C3132](compiler-error-c3132.md)|"*parametru*": tablice parametrów można stosować tylko do formalnego argumentu typu "tablicy jednowymiarowej managed WinRT"|
|[Błąd kompilatora C3133](compiler-error-c3133.md)|Nie można zastosować atrybutów do C++ varargs|
|[Błąd kompilatora C3134](compiler-error-c3134.md)|"*wartość*": wartość argumentu atrybutu "*argument*"nie ma prawidłowego typu"*typu*"|
|[Błąd kompilatora C3135](compiler-error-c3135.md)|"*identyfikator*": właściwość nie może mieć typu "const" lub "volatile" wpisz|
|[Błąd kompilatora C3136](compiler-error-c3136.md)|"*interfejsu*": interfejs COM może dziedziczyć tylko z innego interfejsu COM "*interfejsu*" nie jest interfejsem COM|
|[Błąd kompilatora C3137](compiler-error-c3137.md)|"*identyfikator*": nie można zainicjować właściwości|
|[Błąd kompilatora C3138](compiler-error-c3138.md)|"*identyfikator*": "*atrybutu*" interfejs musi dziedziczyć z IDispatch lub interfejsu, który dziedziczy z IDispatch|
|[Błąd kompilatora C3139](compiler-error-c3139.md)|"*typu*": nie można eksportować UDT bez członków|
|[Błąd kompilatora C3140](compiler-error-c3140.md)|nie może mieć wiele atrybutów "module" w tej samej jednostce kompilacyjnej|
|[Błąd kompilatora C3141](compiler-error-c3141.md)|"*interfejsu*": interfejsy obsługują tylko publiczne dziedziczenie|
|[Błąd kompilatora C3142](compiler-error-c3142.md)|"*właściwości*": nie można przyjąć adresu właściwości|
|C3143 błąd kompilatora|"*argument*": argument atrybutu nie może mieć wielu wartości|
|C3144 błąd kompilatora|"*atrybutu*": atrybut wymaga jawnych argumentów "*argument*" jest bez nazwy|
|[Błąd kompilatora C3145](compiler-error-c3145.md)|"*identyfikator*": zmienną globalną lub statyczną nie może być typu zarządzanego WinRT "*typu*"|
|C3146 błąd kompilatora|Nieaktualne.|
|C3147 błąd kompilatora|Nieaktualne.|
|C3148 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3149](compiler-error-c3149.md)|"*typu*": nie można użyć tego typu, w tym miejscu bez najwyższego poziomu "*tokenu*"|
|[Błąd kompilatora C3150](compiler-error-c3150.md)|"*skonstruować*": "*atrybutu*" można stosować do klasy, struktury, interfejsu, tablicy lub wskaźnika|
|C3151 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3152](compiler-error-c3152.md)|"*funkcja*": "*— słowo kluczowe*" można stosować do klasy, struktury lub wirtualnej funkcji członkowskiej|
|[Błąd kompilatora C3153](compiler-error-c3153.md)|"*interfejsu*": nie można utworzyć wystąpienia interfejsu|
|[Błąd kompilatora C3154](compiler-error-c3154.md)|Oczekiwano "," przed wielokropka. Non-przecinkami wielokropka nie są obsługiwane w przypadku funkcji tablicy parametrów.|
|[Błąd kompilatora C3155](compiler-error-c3155.md)|atrybuty nie są dozwolone w właściwości indeksatora|
|[Błąd kompilatora C3156](compiler-error-c3156.md)|"*klasy*": nie można posiadać lokalnej definicji typu zarządzanego WinRT|
|[Błąd kompilatora C3157](compiler-error-c3157.md)|Atrybut ParamArray można stosować tylko do ostatniego parametru|
|C3158 błąd kompilatora|"*funkcja*": "*— słowo kluczowe*" może być stosowany tylko do wirtualnej funkcji członkowskiej|
|[Błąd kompilatora C3159](compiler-error-c3159.md)|"*identyfikator*": nie można zadeklarować tablicy wskaźników do typu wartość|
|[Błąd kompilatora C3160](compiler-error-c3160.md)|"*typu*": element członkowski danych klasy managed WinRT nie może posiadać tego typu|
|[Błąd kompilatora C3161](compiler-error-c3161.md)|"*interfejsu*": zagnieżdżanie klasy, struktury lub interfejsu w interfejsie jest niedozwolone; zagnieżdżanie interfejsu w klasie lub strukturze jest niedozwolone|
|[Błąd kompilatora C3162](compiler-error-c3162.md)|"*typu*": Typ referencyjny, który posiada destruktor nie może służyć jako typ elementu członkowskiego danych statycznych "*elementu członkowskiego*"|
|[Błąd kompilatora C3163](compiler-error-c3163.md)|"*klasy*": atrybuty niespójne z poprzednią deklaracją|
|C3164 błąd kompilatora|Nieaktualne.|
|C3165 błąd kompilatora|"*wartość*": nie można przekonwertować na wartość całkowitą lub zmiennoprzecinkową|
|[Błąd kompilatora C3166](compiler-error-c3166.md)|Nieaktualne. "*typu*": element członkowski danych klasy managed WinRT nie może mieć typu "*pointer_type* do wnętrza *managed_pointer_type*"|
|[Błąd kompilatora C3167](compiler-error-c3167.md)|Nie można zainicjalizować .NET Framework: Upewnij się, że jest zainstalowany|
|[Błąd kompilatora C3168](compiler-error-c3168.md)|"*typu*": niedozwolony typ podstawowy dla wyliczenia|
|C3169 błąd kompilatora|"*typu*": nie można wywnioskować typu "Auto" z "*typu*"|
|[Błąd kompilatora C3170](compiler-error-c3170.md)|Nie można posiadać innych identyfikatorów modułu w projekcie|
|[Błąd kompilatora C3171](compiler-error-c3171.md)|"*modułu*": nie można określić innych atrybutów modułu w projekcie|
|[Błąd kompilatora C3172](compiler-error-c3172.md)|"*identyfikator*": nie można określić innych atrybutów idl_module w projekcie|
|[Błąd kompilatora C3173](compiler-error-c3173.md)|Niezgodność wersji w scaleniu idl|
|[Błąd kompilatora C3174](compiler-error-c3174.md)|Atrybut modułu nie została określona.|
|[Błąd kompilatora C3175](compiler-error-c3175.md)|"*funkcja*": nie można wywołać metody typu zarządzanego z niezarządzanej funkcji "*funkcja*"|
|[Błąd kompilatora C3176](compiler-error-c3176.md)|"*typu*": nie można zadeklarować lokalnego typu wartościowego|
|C3177 błąd kompilatora|Nie można umieścić funkcji konwersji do typu, który zawiera "*typu*"|
|C3178 błąd kompilatora|"*typu*": nie można używać ParamArray w funkcji z argumentami domyślnymi|
|[Błąd kompilatora C3179](compiler-error-c3179.md)|bez nazwy typu zarządzanego WinRT nie jest dozwolona.|
|[Błąd kompilatora C3180](compiler-error-c3180.md)|"*typu*": nazwa przekracza limit meta-data "*numer*' znaków|
|[Błąd kompilatora C3181](compiler-error-c3181.md)|"*typu*": nieprawidłowy operand dla *— operator*|
|[Błąd kompilatora C3182](compiler-error-c3182.md)|"*typu*": deklaracja deklaracja using lub dostępu elementu członkowskiego jest niedozwolony w ramach typu managed WinRT|
|[Błąd kompilatora C3183](compiler-error-c3183.md)|Nie można zdefiniować nienazwanej klasy, struktury lub związku wewnątrz typu zarządzanego WinRT "*klasy*"|
|C3184 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3185](compiler-error-c3185.md)|"typeid": używany na typie managed WinRT "*typu*", użyj "*operator*" zamiast tego|
|C3186 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3187](compiler-error-c3187.md)|"*identyfikator*": jest dostępna tylko w treści funkcji|
|C3188 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3189](compiler-error-c3189.md)|"typeid <*deklarator*>": Ta składnia nie jest już obsługiwana, należy zamiast tego|
|[Błąd kompilatora C3190](compiler-error-c3190.md)|"*deklarator*"z argumentami podanymi przez szablon nie jest jawnym utworzeniem wystąpienia jakiegokolwiek funkcji członkowskiej"*typu*"|
|C3191 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C3192](compiler-error-c3192.md)|Błąd składniowy: "^" nie jest operatorem prefiksowym (Czy chodziło o "*"?)|
|C3193 błąd kompilatora|"*skonstruować*": wymaga "/ clr" lub "/ ZW" opcji wiersza polecenia|
|[Błąd kompilatora C3194](compiler-error-c3194.md)|"*typu*": typ wartościowy nie może mieć operatora przypisania|
|[Błąd kompilatora C3195](compiler-error-c3195.md)|"*— słowo kluczowe*": jest zarezerwowany i nie można użyć jako element członkowski typu klasy lub wartość ref. Operatory CLR i WinRT musi być zdefiniowana przy użyciu słowa kluczowego "operator"|
|[Błąd kompilatora C3196](compiler-error-c3196.md)|"*identyfikator*": użyty więcej niż raz|
|[Błąd kompilatora C3197](compiler-error-c3197.md)|"*— słowo kluczowe*": można używać tylko w definicjach|
|[Błąd kompilatora C3198](compiler-error-c3198.md)|Nieprawidłowe użycie zmiennoprzecinkowych pragm: fenv_access pragma działa tylko w trybie ścisłym|
|[Błąd kompilatora C3199](compiler-error-c3199.md)|Nieprawidłowe użycie zmiennoprzecinkowych pragm: wyjątki nie są obsługiwane w trybie ścisłym|
