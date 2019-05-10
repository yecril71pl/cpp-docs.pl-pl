---
title: Błędy kompilatora — od C2300 do C2399
ms.date: 04/21/2019
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 28ab73857b46fed29e2ba8d7bc051ffb81b54bb3
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857367"
---
# <a name="compiler-errors-c2300-through-c2399"></a>Błędy kompilatora — od C2300 do C2399

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Message|
|-----------|-------------|
|[Błąd kompilatora od C2300](compiler-error-c2300.md)|"*klasy*": klasa nie ma wywołania destruktora "~*klasy*"|
|[Błąd kompilatora C2301](compiler-error-c2301.md)|po lewej "-> ~*identyfikator*" musi wskazywać na klasy/struct/union|
|[Błąd kompilatora C2302](compiler-error-c2302.md)|po lewej ". ~*identyfikator*" musi mieć typ klasy/struct/union|
|Błąd kompilatora C2303|Obsługa wyjątków strukturalnych nie można używać w procedurze wspólnej|
|Błąd kompilatora C2304|"*— słowo kluczowe*" nie można używać wewnątrz bloku catch|
|Błąd kompilatora C2305|"*pliku*" nie zawiera informacji o debugowaniu dla tego modułu|
|Błąd kompilatora C2306|"*pliku*" nie zawiera ostatnich informacji o debugowaniu dla tego modułu|
|[Błąd kompilatora C2307](compiler-error-c2307.md)|pragma *dyrektywy* należy przenieść poza funkcji, jeśli włączono kompilacji przyrostowej|
|[Błąd kompilatora C2308](compiler-error-c2308.md)|konkatenacja niedopasowanych ciągów znaków|
|[Błąd kompilatora C2309](compiler-error-c2309.md)|przy obsłudze catch Oczekiwano deklaracji wyjątku ujętego w nawiasy|
|[Błąd kompilatora C2310](compiler-error-c2310.md)|bloki catch muszą określać jeden typ|
|[Błąd kompilatora C2311](compiler-error-c2311.md)|"*typu*": zostanie przechwycony przez "..." w wierszu *numer*|
|[Błąd kompilatora C2312](compiler-error-c2312.md)|"*type1*": zostanie przechwycony przez "*type2*" w wierszu *numer*|
|[Błąd kompilatora C2313](compiler-error-c2313.md)|"*type1*": zostanie przechwycony przez odwołanie ("*type2*") w wierszu *numer*|
|Błąd kompilatora C2314|— słowo kluczowe "*keyword1*" jest przestarzałe: Użyj "*keyword2*" zamiast niego|
|[Błąd kompilatora C2315](compiler-error-c2315.md)|"*type1*": odwołanie zostało przechwycone przez "*type2*" w wierszu *numer*|
|[Błąd kompilatora C2316](compiler-error-c2316.md)|"*typu*": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub zostały usunięte|
|[Błąd kompilatora C2317](compiler-error-c2317.md)|począwszy od linii bloku "try" "*numer*" nie ma obsługi catch|
|[Błąd kompilatora C2318](compiler-error-c2318.md)|nie try blok skojarzonych z tym obsługi catch|
|[Błąd kompilatora C2319](compiler-error-c2319.md)|"try/catch" musi następować instrukcja złożona. Brak "{"|
|[Błąd kompilatora C2320](compiler-error-c2320.md)|Oczekiwano ":" Aby po specyfikatorze dostępu "*specyfikator*"|
|Błąd kompilatora C2321|"*identyfikator*" jest słowem kluczowym i nie można używać w tym kontekście|
|[Błąd kompilatora C2322](compiler-error-c2322.md)|"*identyfikator*": adres importu dllimport "*identyfikator*" nie jest statyczna|
|Błąd kompilatora C2323|"*identyfikator*": operator składowej nowego ani funkcje delete nie mogą być deklarowane statyczne lub w przestrzeni nazw, innym niż globalna przestrzeń nazw|
|[Błąd kompilatora C2324](compiler-error-c2324.md)|"*identyfikator*": nieoczekiwany po prawej stronie ":: ~"|
|[Błąd kompilatora C2325](compiler-error-c2325.md)|"*type1*": nieoczekiwany typ po prawej stronie "-> ~": oczekiwano "*type2*"|
|[Błąd kompilatora C2326](compiler-error-c2326.md)|"*deklaratora*": funkcja nie ma dostępu do "*identyfikator*"|
|[Błąd kompilatora C2327](compiler-error-c2327.md)|"*identyfikator*": Brak nazwy typu, statycznym lub modułu wyliczającego|
|Błąd kompilatora C2328|"*— słowo kluczowe*": słowo kluczowe nie jest jeszcze obsługiwana.|
|Błąd kompilatora C2329|"*identyfikator*": __ptr64 nie jest dostępny dla wskaźników do funkcji|
|Błąd kompilatora C2330|"implementation_key()" jest prawidłowy tylko w regionie poprowadzoną #pragma start_map_region/stop_map_region|
|Błąd kompilatora C2331|dostęp do "*identyfikator*"teraz zdefiniowany jako"*accessibility1*", poprzednio został zdefiniowany jako"*accessibility2*"|
|[Błąd kompilatora C2332](compiler-error-c2332.md)|"*typedef*": Brak nazwy tagu|
|[Błąd kompilatora C2333](compiler-error-c2333.md)|"*funkcja*": błąd w deklaracji funkcji; pomijanie treści funkcji|
|[Błąd kompilatora C2334](compiler-error-c2334.md)|Nieoczekiwany(e) token(y) poprzedniego "*tokenu*"; Pomijanie treści widocznych funkcji|
|Błąd kompilatora C2335|"*identyfikator*": typ nie może zostać wprowadzony w liście parametrów funkcji|
|Błąd kompilatora C2336|"*typu*": niedozwolony typ|
|[Błąd kompilatora C2337](compiler-error-c2337.md)|"*atrybut*": nie znaleziono atrybutu|
|[Błąd kompilatora C2338](compiler-error-c2338.md)|*(komunikat o błędzie z zewnętrznego dostawcy)*|
|Błąd kompilatora C2339|"*identyfikator*": niedozwolony typ w osadzonym IDL|
|Błąd kompilatora C2340|"*identyfikator*": "static" można używać tylko wewnątrz definicji klasy|
|[Błąd kompilatora C2341](compiler-error-c2341.md)|"*sekcji*': segment musi być zdefiniowany przy użyciu #pragma data_seg, code_seg lub wcześniejszej sekcji, aby użyć|
|Błąd kompilatora C2342|Błąd składniowy: konflikt typu kwalifikatorów|
|Błąd kompilatora C2343|"*sekcji*": konflikt atrybutów sekcji|
|[Błąd kompilatora C2344](compiler-error-c2344.md)|Wyrównaj (*numer*): wyrównanie musi być potęgą liczby dwa|
|[Błąd kompilatora C2345](compiler-error-c2345.md)|Wyrównaj (*numer*): Niedozwolona wartość wyrównania|
|[Błąd kompilatora C2346](compiler-error-c2346.md)|"*funkcja*" nie można skompilować jako natywny: "*wyjaśnienie*"|
|Błąd kompilatora C2347|Nieaktualne.|
|[Błąd kompilatora C2348](compiler-error-c2348.md)|"*typu*": nie jest agregacji stylu C, nie można wyeksportować w osadzonym IDL|
|[Błąd kompilatora C2349](compiler-error-c2349.md)|"*funkcja*" nie można skompilować jako zarządzany: "*wyjaśnienie*"; Użyj #pragma niezarządzanego|
|[Błąd kompilatora C2350](compiler-error-c2350.md)|"*identyfikator*" nie jest składową statyczną|
|[Błąd kompilatora C2351](compiler-error-c2351.md)|przestarzała Inicjalizacja składni konstruktora C++|
|[Błąd kompilatora C2352](compiler-error-c2352.md)|"*identyfikator*": niedozwolone wywołanie niestatycznej składowej — funkcja|
|[Błąd kompilatora C2353](compiler-error-c2353.md)|Specyfikacja wyjątku nie jest dozwolone.|
|Błąd kompilatora C2354|Nieaktualne.|
|[Błąd kompilatora C2355](compiler-error-c2355.md)|"this": można tworzyć odwołania wyłącznie wewnątrz niestatycznych elementów członkowskich lub danych niestatycznych inicjatorów składowych|
|[Compiler error C2356](compiler-error-c2356.md)|segment inicjalizacyjny nie może ulec zmianie podczas tłumaczenia jednostki|
|[Błąd kompilatora C2357](compiler-error-c2357.md)|"*identyfikator*": musi być funkcją typu "*typu*"|
|Błąd kompilatora C2358|"*identyfikator*": właściwość statyczna nie może być zdefiniowana poza definicją klasy|
|Błąd kompilatora C2359|Nieaktualne.|
|[Błąd kompilatora C2360](compiler-error-c2360.md)|Inicjalizacja "*identyfikator*" jest pomijana przy etykiecie "case"|
|[Błąd kompilatora C2361](compiler-error-c2361.md)|Inicjalizacja "*identyfikator*" jest pomijana przy etykiecie "default"|
|[Błąd kompilatora C2362](compiler-error-c2362.md)|Inicjalizacja "*identyfikator*" jest pomijana przy "goto *etykiety*"|
|Błąd kompilatora C2363|funkcja wewnętrzna numerycznego limitu kompilatora wymaga argumentu literału ciągu|
|[Błąd kompilatora C2364](compiler-error-c2364.md)|"*typu*": niedozwolony typ niestandardowegp atrybutu|
|[Błąd kompilatora C2365](compiler-error-c2365.md)|"*Członek1*": zmiana definicji; definicja poprzedniej została "*członek2*"|
|Błąd kompilatora C2366|"*identyfikator*": zmiana definicji; specyfikatory różnych implementation_key|
|Błąd kompilatora C2367|Nieaktualne.|
|[Błąd kompilatora C2368](compiler-error-c2368.md)|"*identyfikator*": zmiana definicji; specyfikatory różnych alokacji|
|[Compiler error C2369](compiler-error-c2369.md)|"*identyfikator*": zmiana definicji; różne indeksy|
|[Błąd kompilatora C2370](compiler-error-c2370.md)|"*identyfikator*": zmiana definicji; różne klasy magazynu|
|[Błąd kompilatora C2371](compiler-error-c2371.md)|"*identyfikator*": zmiana definicji; różne typy podstawowe|
|[Błąd kompilatora C2372](compiler-error-c2372.md)|"*identyfikator*": zmiana definicji; różne typy pośredniego wywołania|
|[Błąd kompilatora C2373](compiler-error-c2373.md)|"*identyfikator*": zmiana definicji; różne typy modyfikatorów|
|[Błąd kompilatora C2374](compiler-error-c2374.md)|"*identyfikator*": zmiana definicji; wielokrotna Inicjalizacja|
|[Błąd kompilatora C2375](compiler-error-c2375.md)|"*identyfikator*": zmiana definicji; różne powiązania|
|[Błąd kompilatora C2376](compiler-error-c2376.md)|"*identyfikator*": zmiana definicji; różne na podstawie alokacji|
|[Błąd kompilatora C2377](compiler-error-c2377.md)|"*identyfikator*": zmiana definicji; typedef nie może zostać przeciążony przez dowolny inny symbol|
|[Błąd kompilatora C2378](compiler-error-c2378.md)|"*identyfikator*": zmiana definicji; symbol nie może zostać przeciążony przez TypeDef|
|[Błąd kompilatora C2379](compiler-error-c2379.md)|Parametr formalny *numer* jest innego typu kiedy jest zwiększany|
|[Błąd kompilatora C2380](compiler-error-c2380.md)|Typ(-y) poprzedzający(-e) "*identyfikator*" (Konstruktor z typem zwracanym lub niedozwolona próba ponownego zdefiniowania bieżącej nazwy klasy?)|
|[Błąd kompilatora C2381](compiler-error-c2381.md)|"*identyfikator*": zmiana definicji; "__declspec(noreturn)" lub "[[noreturn]]" różni się|
|[Błąd kompilatora C2382](compiler-error-c2382.md)|"*identyfikator*": zmiana definicji; różne specyfikacje wyjątków|
|[Błąd kompilatora C2383](compiler-error-c2383.md)|"*identyfikator*": argumenty domyślne nie są dozwolone w tym symbolu|
|[Błąd kompilatora C2384](compiler-error-c2384.md)|"*elementu członkowskiego*": nie można zastosować elementu thread_local lub __declspec(thread) do składowej klasy zarządzane/WinRT|
|[Błąd kompilatora C2385](compiler-error-c2385.md)|niejednoznaczne dostęp do "*elementu członkowskiego*"|
|[Błąd kompilatora C2386](compiler-error-c2386.md)|"*identyfikator*": symbol o tej nazwie już istnieje w bieżącym zakresie|
|[Błąd kompilatora C2387](compiler-error-c2387.md)|"*identyfikator*": niejednoznaczna klasa bazowa|
|[Błąd kompilatora C2388](compiler-error-c2388.md)|"*identyfikator*": nie można zadeklarować symbolu z __declspec(appdomain) oraz __declspec (Process)|
|[Błąd kompilatora C2389](compiler-error-c2389.md)|"*operator*": niedozwolony operand "nullptr"|
|[Błąd kompilatora C2390](compiler-error-c2390.md)|"*identyfikator*": niepoprawna Klasa magazynu*specyfikator*"|
|[Błąd kompilatora C2391](compiler-error-c2391.md)|"*identyfikator*": "friend" nie może zostać użyty podczas definicji typu|
|[Błąd kompilatora C2392](compiler-error-c2392.md)|"*Członek1*": typy nie są obsługiwane w typach zarządzanych/WinRT, w przeciwnym razie zwraca kowariantne "*członek2*" może zostać przesłonięta|
|[Błąd kompilatora C2393](compiler-error-c2393.md)|"*symbol*": symbol per-appdomain nie może zostać alokowany w segmencie "*segmentu*"|
|[Błąd kompilatora C2394](compiler-error-c2394.md)|"*typu*:: operator *operator*": CLR/WinRT operator nie jest prawidłowy. Co najmniej jeden parametr musi być następujących typów:  T ^', t ^ % ", t ^ &", gdzie T = "*typu*"|
|[Błąd kompilatora C2395](compiler-error-c2395.md)|"*typu*:: operator *operator*": CLR/WinRT operator nie jest prawidłowy. Co najmniej jeden parametr musi być następujących typów: T ", t %", t & ", t ^', t ^ %", t ^ & ", gdzie T ="*typu*"|
|[Błąd kompilatora C2396](compiler-error-c2396.md)|"*type1*:: operator *type2*": CLR/WinRT konwersja zdefiniowana przez użytkownika funkcja nie jest prawidłowy. Należy konwertować z albo konwertować na: T ^', t ^ % ", t ^ &", gdzie T = "*type1*"|
|[Błąd kompilatora C2397](compiler-error-c2397.md)|Konwersja z "*type1*"to"*type2*" wymaga konwersji zawężającej|
|Błąd kompilatora C2398|Element "*numer*': konwersja z"*type1*"to"*type2*"wymaga konwersji zawężającej|
|Błąd kompilatora C2399|Nieaktualne.|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
