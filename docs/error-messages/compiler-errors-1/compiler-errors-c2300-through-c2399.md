---
title: Błędy kompilatora od C2300 do C2399
ms.date: 11/17/2017
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
ms.openlocfilehash: 6f95ec90a08b842259a383d7bfc6af2cba119e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580638"
---
# <a name="compiler-errors-c2300-through-c2399"></a>Błędy kompilatora od C2300 do C2399

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2300](compiler-error-c2300.md)|"*klasy*": klasa nie ma wywołania destruktora "~*klasy*"|
|[Błąd kompilatora C2301](compiler-error-c2301.md)|po lewej "-> ~*identyfikator*" musi wskazywać na klasy/struct/union|
|[Błąd kompilatora C2302](compiler-error-c2302.md)|po lewej ". ~*identyfikator*" musi mieć typ klasy/struct/union|
|C2303 błąd kompilatora|Obsługa wyjątków strukturalnych nie można używać w procedurze wspólnej|
|C2304 błąd kompilatora|"*— słowo kluczowe*" nie można używać wewnątrz bloku catch|
|C2305 błąd kompilatora|"*pliku*" nie zawiera informacji o debugowaniu dla tego modułu|
|C2306 błąd kompilatora|"*pliku*" nie zawiera ostatnich informacji o debugowaniu dla tego modułu|
|[Błąd kompilatora C2307](compiler-error-c2307.md)|pragma *dyrektywy* należy przenieść poza funkcji, jeśli włączono kompilacji przyrostowej|
|[Błąd kompilatora C2308](compiler-error-c2308.md)|konkatenacja niedopasowanych ciągów znaków|
|[Błąd kompilatora C2309](compiler-error-c2309.md)|przy obsłudze catch Oczekiwano deklaracji wyjątku ujętego w nawiasy|
|[Błąd kompilatora C2310](compiler-error-c2310.md)|bloki catch muszą określać jeden typ|
|[Błąd kompilatora C2311](compiler-error-c2311.md)|"*typu*": zostanie przechwycony przez "..." w wierszu *numer*|
|[Błąd kompilatora C2312](compiler-error-c2312.md)|"*type1*": zostanie przechwycony przez "*type2*" w wierszu *numer*|
|[Błąd kompilatora C2313](compiler-error-c2313.md)|"*type1*": zostanie przechwycony przez odwołanie ("*type2*") w wierszu *numer*|
|C2314 błąd kompilatora|— słowo kluczowe "*keyword1*" jest przestarzałe: Użyj "*keyword2*" zamiast niego|
|[Błąd kompilatora C2315](compiler-error-c2315.md)|"*type1*": odwołanie zostało przechwycone przez "*type2*" w wierszu *numer*|
|[Błąd kompilatora C2316](compiler-error-c2316.md)|"*typu*": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub zostały usunięte|
|[Błąd kompilatora C2317](compiler-error-c2317.md)|począwszy od linii bloku "try" "*numer*" nie ma obsługi catch|
|[Błąd kompilatora C2318](compiler-error-c2318.md)|nie try blok skojarzonych z tym obsługi catch|
|[Błąd kompilatora C2319](compiler-error-c2319.md)|"try/catch" musi następować instrukcja złożona. Brak "{"|
|[Błąd kompilatora C2320](compiler-error-c2320.md)|Oczekiwano ":" Aby po specyfikatorze dostępu "*specyfikator*"|
|C2321 błąd kompilatora|"*identyfikator*" jest słowem kluczowym i nie można używać w tym kontekście|
|[Błąd kompilatora C2322](compiler-error-c2322.md)|"*identyfikator*": adres importu dllimport "*identyfikator*" nie jest statyczna|
|C2323 błąd kompilatora|"*identyfikator*": operator składowej nowego ani funkcje delete nie mogą być deklarowane statyczne lub w przestrzeni nazw, innym niż globalna przestrzeń nazw|
|[Błąd kompilatora C2324](compiler-error-c2324.md)|"*identyfikator*": nieoczekiwany po prawej stronie ":: ~"|
|[Błąd kompilatora C2325](compiler-error-c2325.md)|"*type1*": nieoczekiwany typ po prawej stronie "-> ~": oczekiwano "*type2*"|
|[Błąd kompilatora C2326](compiler-error-c2326.md)|"*deklaratora*": funkcja nie ma dostępu do "*identyfikator*"|
|[Błąd kompilatora C2327](compiler-error-c2327.md)|"*identyfikator*": Brak nazwy typu, statycznym lub modułu wyliczającego|
|C2328 błąd kompilatora|"*— słowo kluczowe*": słowo kluczowe nie jest jeszcze obsługiwana.|
|C2329 błąd kompilatora|"*identyfikator*": __ptr64 nie jest dostępny dla wskaźników do funkcji|
|C2330 błąd kompilatora|"implementation_key()" jest prawidłowy tylko w regionie poprowadzoną #pragma start_map_region/stop_map_region|
|C2331 błąd kompilatora|dostęp do "*identyfikator*"teraz zdefiniowany jako"*accessibility1*", poprzednio został zdefiniowany jako"*accessibility2*"|
|[Błąd kompilatora C2332](compiler-error-c2332.md)|"*typedef*": Brak nazwy tagu|
|[Błąd kompilatora C2333](compiler-error-c2333.md)|"*funkcja*": błąd w deklaracji funkcji; pomijanie treści funkcji|
|[Błąd kompilatora C2334](compiler-error-c2334.md)|Nieoczekiwany(e) token(y) poprzedniego "*tokenu*"; Pomijanie treści widocznych funkcji|
|C2335 błąd kompilatora|"*identyfikator*": typ nie może zostać wprowadzony w liście parametrów funkcji|
|C2336 błąd kompilatora|"*typu*": niedozwolony typ|
|[Błąd kompilatora C2337](compiler-error-c2337.md)|"*atrybut*": nie znaleziono atrybutu|
|[Błąd kompilatora C2338](compiler-error-c2338.md)|*(komunikat o błędzie z zewnętrznego dostawcy)*|
|C2339 błąd kompilatora|"*identyfikator*": niedozwolony typ w osadzonym IDL|
|C2340 błąd kompilatora|"*identyfikator*": "static" można używać tylko wewnątrz definicji klasy|
|[Błąd kompilatora C2341](compiler-error-c2341.md)|"*sekcji*': segment musi być zdefiniowany przy użyciu #pragma data_seg, code_seg lub wcześniejszej sekcji, aby użyć|
|C2342 błąd kompilatora|Błąd składniowy: konflikt typu kwalifikatorów|
|C2343 błąd kompilatora|"*sekcji*": konflikt atrybutów sekcji|
|[Błąd kompilatora C2344](compiler-error-c2344.md)|Wyrównaj (*numer*): wyrównanie musi być potęgą liczby dwa|
|[Błąd kompilatora C2345](compiler-error-c2345.md)|Wyrównaj (*numer*): Niedozwolona wartość wyrównania|
|[Błąd kompilatora C2346](compiler-error-c2346.md)|"*funkcja*" nie można skompilować jako natywny: "*wyjaśnienie*"|
|C2347 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2348](compiler-error-c2348.md)|"*typu*": nie jest agregacji stylu C, nie można wyeksportować w osadzonym IDL|
|[Błąd kompilatora C2349](compiler-error-c2349.md)|"*funkcja*" nie można skompilować jako zarządzany: "*wyjaśnienie*"; Użyj #pragma niezarządzanego|
|[Błąd kompilatora C2350](compiler-error-c2350.md)|"*identyfikator*" nie jest składową statyczną|
|[Błąd kompilatora C2351](compiler-error-c2351.md)|przestarzała Inicjalizacja składni konstruktora C++|
|[Błąd kompilatora C2352](compiler-error-c2352.md)|"*identyfikator*": niedozwolone wywołanie niestatycznej składowej — funkcja|
|[Błąd kompilatora C2353](compiler-error-c2353.md)|Specyfikacja wyjątku nie jest dozwolone.|
|C2354 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2355](compiler-error-c2355.md)|"this": można tworzyć odwołania wyłącznie wewnątrz niestatycznych elementów członkowskich lub danych niestatycznych inicjatorów składowych|
|[Błąd kompilatora C2356](compiler-error-c2356.md)|segment inicjalizacyjny nie może ulec zmianie podczas tłumaczenia jednostki|
|[Błąd kompilatora C2357](compiler-error-c2357.md)|"*identyfikator*": musi być funkcją typu "*typu*"|
|C2358 błąd kompilatora|"*identyfikator*": właściwość statyczna nie może być zdefiniowana poza definicją klasy|
|C2359 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2360](compiler-error-c2360.md)|Inicjalizacja "*identyfikator*" jest pomijana przy etykiecie "case"|
|[Błąd kompilatora C2361](compiler-error-c2361.md)|Inicjalizacja "*identyfikator*" jest pomijana przy etykiecie "default"|
|[Błąd kompilatora C2362](compiler-error-c2362.md)|Inicjalizacja "*identyfikator*" jest pomijana przy "goto *etykiety*"|
|C2363 błąd kompilatora|funkcja wewnętrzna numerycznego limitu kompilatora wymaga argumentu literału ciągu|
|[Błąd kompilatora C2364](compiler-error-c2364.md)|"*typu*": niedozwolony typ niestandardowegp atrybutu|
|[Błąd kompilatora C2365](compiler-error-c2365.md)|"*Członek1*": zmiana definicji; definicja poprzedniej została "*członek2*"|
|C2366 błąd kompilatora|"*identyfikator*": zmiana definicji; specyfikatory różnych implementation_key|
|C2367 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2368](compiler-error-c2368.md)|"*identyfikator*": zmiana definicji; specyfikatory różnych alokacji|
|[Błąd kompilatora C2369](compiler-error-c2369.md)|"*identyfikator*": zmiana definicji; różne indeksy|
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
|[Błąd kompilatora C2394](compiler-error-c2394.md)|"*typu*:: operator *operator*": nieprawidłowy operator CLR/WinRT. Co najmniej jeden parametr musi być następujących typów: t ^', t ^ % ", t ^ &", gdzie T = "*typu*"|
|[Błąd kompilatora C2395](compiler-error-c2395.md)|"*typu*:: operator *operator*": nieprawidłowy operator CLR/WinRT. Co najmniej jeden parametr musi być następujących typów: t ", t %", t & ", t ^', t ^ %", t ^ & ", gdzie T ="*typu*"|
|[Błąd kompilatora C2396](compiler-error-c2396.md)|"*type1*:: operator *type2*": funkcja konwersji zdefiniowanej przez użytkownika CLR/WinRT nie jest prawidłowy. Należy konwertować z albo konwertować na: t ^', t ^ % ", t ^ &", gdzie T = "*type1*"|
|[Błąd kompilatora C2397](compiler-error-c2397.md)|Konwersja z "*type1*"to"*type2*" wymaga konwersji zawężającej|
|C2398 błąd kompilatora|Element "*numer*': konwersja z"*type1*"to"*type2*"wymaga konwersji zawężającej|
|C2399 błąd kompilatora|Nieaktualne.|
