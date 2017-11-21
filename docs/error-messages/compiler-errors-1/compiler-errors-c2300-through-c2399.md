---
title: "Błędy kompilatora od C2300 C2399 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
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
dev_langs: C++
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f8e1dcf350c974f5be96b971d3d70e69b95ebc9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2300-through-c2399"></a>Błędy kompilatora od C2300 do C2399
Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.  
  
> [!NOTE]
>  Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).  
  
|Błąd|Komunikat|  
|-----------|-------------|  
|[Kompilatora od C2300 do błędu](compiler-error-c2300.md)|"*klasy*": klasa nie ma destruktora o nazwie "~*klasy*"|  
|[C2301 błąd kompilatora](compiler-error-c2301.md)|po lewej "-> ~*identyfikator*' musi wskazywać klasy/struktury/Unii|  
|[C2302 błąd kompilatora](compiler-error-c2302.md)|po lewej ". ~*identyfikator*" musi mieć typ klasy/struktury/Unii|  
|C2303 błąd kompilatora|Obsługa wyjątków strukturalnych nie można używać w procedurze wspólnej|  
|C2304 błąd kompilatora|"*— słowo kluczowe*" nie można używać wewnątrz bloku catch|  
|C2305 błąd kompilatora|"*pliku*" nie zawiera informacji o debugowaniu dla tego modułu|  
|C2306 błąd kompilatora|"*pliku*" nie zawiera ostatnich informacji o debugowaniu dla tego modułu|  
|[C2307 błąd kompilatora](compiler-error-c2307.md)|pragma *dyrektywy* musi zostać przeniesiona poza funkcję Jeśli włączono kompilację przyrostową|  
|[C2308 błąd kompilatora](compiler-error-c2308.md)|łączenie ciągów niezgodne|  
|[C2309 błąd kompilatora](compiler-error-c2309.md)|przy obsłudze catch Oczekiwano deklaracji wyjątku ujętego w nawiasy|  
|[C2310 błąd kompilatora](compiler-error-c2310.md)|bloki catch muszą określać jeden typ|  
|[C2311 błąd kompilatora](compiler-error-c2311.md)|"*typu*": zostanie przechwycony przez "..." w wierszu *numer*|  
|[C2312 błąd kompilatora](compiler-error-c2312.md)|"*type1*": zostanie przechwycony przez "*type2*" w wierszu *numer*|  
|[C2313 błąd kompilatora](compiler-error-c2313.md)|"*type1*": zostanie przechwycony przez odwołanie ("*type2*") w wierszu *numer*|  
|C2314 błąd kompilatora|— słowo kluczowe "*keyword1*" jest przestarzała: Użyj "*keyword2*" zamiast niego|  
|[C2315 błąd kompilatora](compiler-error-c2315.md)|"*type1*": odwołanie zostało przechwycone przez "*type2*" w wierszu *numer*|  
|[C2316 błąd kompilatora](compiler-error-c2316.md)|"*typu*": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub zostały usunięte|  
|[C2317 błąd kompilatora](compiler-error-c2317.md)|począwszy od linii bloku "try" "*numer*" nie ma obsługi catch|  
|[C2318 błąd kompilatora](compiler-error-c2318.md)|nie try blok skojarzonych z tym obsługi catch|  
|[C2319 błąd kompilatora](compiler-error-c2319.md)|"try/catch" musi następować złożonej instrukcji. Brakuje "{"|  
|[C2320 błąd kompilatora](compiler-error-c2320.md)|Oczekiwano ":" aby występował po specyfikatorze dostępu "*specyfikator*"|  
|C2321 błąd kompilatora|"*identyfikator*" jest słowem kluczowym i nie można użyć w tym kontekście|  
|[C2322 błąd kompilatora](compiler-error-c2322.md)|"*identyfikator*': adres dllimport"*identyfikator*"nie jest statyczna|  
|C2323 błąd kompilatora|"*identyfikator*": nowy operator niebędący elementem członkowskim ani funkcje delete mogą nie być deklarowane jako statyczne lub w przestrzeni nazw innej niż globalna przestrzeń nazw|  
|[C2324 błąd kompilatora](compiler-error-c2324.md)|"*identyfikator*": nieoczekiwany po prawej stronie ":: ~"|  
|[C2325 błąd kompilatora](compiler-error-c2325.md)|"*type1*": nieoczekiwany typ po prawej stronie ' -> ~ ": oczekiwano"*type2*"|  
|[C2326 błąd kompilatora](compiler-error-c2326.md)|"*deklarator*": funkcja nie może uzyskać dostępu "*identyfikator*"|  
|[C2327 błąd kompilatora](compiler-error-c2327.md)|"*identyfikator*": nie jest nazwa typu, statycznym lub modułu wyliczającego|  
|C2328 błąd kompilatora|"*— słowo kluczowe*": słowo kluczowe nie jest jeszcze obsługiwany.|  
|C2329 błąd kompilatora|"*identyfikator*": __ptr64 nie jest dostępny dla wskaźników do funkcji|  
|C2330 błąd kompilatora|"implementation_key ()" jest prawidłowy tylko w regionie ograniczonego #pragma start_map_region/stop_map_region|  
|C2331 błąd kompilatora|dostęp do "*identyfikator*"teraz zdefiniowany jako"*accessibility1*", poprzednio został zdefiniowany jako"*accessibility2*"|  
|[C2332 błąd kompilatora](compiler-error-c2332.md)|"*typedef*": Brak nazwy tagu|  
|[C2333 błąd kompilatora](compiler-error-c2333.md)|"*funkcja*": błąd w deklaracji funkcji; pomijanie treści funkcji|  
|[C2334 błąd kompilatora](compiler-error-c2334.md)|nieoczekiwane tokeny poprzedniego "*tokenu*"; Pomijanie treści widocznych funkcji|  
|C2335 błąd kompilatora|"*identyfikator*": typ nie może zostać wprowadzony na liście parametrów funkcji|  
|C2336 błąd kompilatora|"*typu*": niedozwolony typ|  
|[C2337 błąd kompilatora](compiler-error-c2337.md)|"*atrybutu*": nie znaleziono atrybutu|  
|[C2338 błąd kompilatora](compiler-error-c2338.md)|*(komunikat o błędzie z zewnętrznego dostawcy)*|  
|C2339 błąd kompilatora|"*identyfikator*": niedozwolony typ w osadzonym IDL|  
|C2340 błąd kompilatora|"*identyfikator*": "static" może być użyte tylko w definicji klasy|  
|[C2341 błąd kompilatora](compiler-error-c2341.md)|"*sekcji*': segment musi być zdefiniowany przy użyciu #pragma data_seg, code_seg lub wcześniejszej sekcji do użycia|  
|C2342 błąd kompilatora|Błąd składniowy: konflikt typu kwalifikatorów|  
|C2343 błąd kompilatora|"*sekcji*": konflikt atrybutów sekcji|  
|[C2344 błąd kompilatora](compiler-error-c2344.md)|Dopasuj (*numer*): wyrównanie musi być potęgą liczby dwa|  
|[C2345 błąd kompilatora](compiler-error-c2345.md)|Dopasuj (*numer*): Niedozwolona wartość wyrównania|  
|[C2346 błąd kompilatora](compiler-error-c2346.md)|"*funkcja*" nie można skompilować jako natywny: "*wyjaśnienie*"|  
|C2347 błąd kompilatora|Nieaktualne.|  
|[C2348 błąd kompilatora](compiler-error-c2348.md)|"*typu*": nie jest agregacji stylu języka C, nie może być eksportowany w osadzonych IDL|  
|[C2349 błąd kompilatora](compiler-error-c2349.md)|"*funkcja*" nie można skompilować jako zarządzany: "*wyjaśnienie*"; Użyj #pragma niezarządzanego|  
|[C2350 błąd kompilatora](compiler-error-c2350.md)|"*identyfikator*" nie jest statycznym elementem członkowskim|  
|[C2351 błąd kompilatora](compiler-error-c2351.md)|przestarzała Inicjalizacja składni konstruktora C++|  
|[C2352 błąd kompilatora](compiler-error-c2352.md)|"*identyfikator*": niedozwolone wywołanie funkcji niestatycznego elementu członkowskiego|  
|[C2353 błąd kompilatora](compiler-error-c2353.md)|Specyfikacja wyjątku nie jest dozwolone.|  
|C2354 błąd kompilatora|Nieaktualne.|  
|[C2355 błąd kompilatora](compiler-error-c2355.md)|"this": może być przywoływany tylko wewnątrz instrukcji lub funkcji niestatycznego elementu członkowskiego danych niestatycznych inicjatorów elementów członkowskich|  
|[C2356 błąd kompilatora](compiler-error-c2356.md)|segment inicjalizacyjny nie może ulec zmianie podczas tłumaczenia jednostki|  
|[C2357 błąd kompilatora](compiler-error-c2357.md)|"*identyfikator*": musi być funkcją typu "*typu*"|  
|C2358 błąd kompilatora|"*identyfikator*": właściwość statyczna nie może być zdefiniowana poza definicją klasy|  
|C2359 błąd kompilatora|Nieaktualne.|  
|[C2360 błąd kompilatora](compiler-error-c2360.md)|Inicjowanie "*identyfikator*" jest pomijana przy etykiecie "case"|  
|[C2361 błąd kompilatora](compiler-error-c2361.md)|Inicjowanie "*identyfikator*" jest pomijana przy etykiecie "default"|  
|[C2362 błąd kompilatora](compiler-error-c2362.md)|Inicjowanie "*identyfikator*" jest pomijana przy "goto *etykiety*"|  
|C2363 błąd kompilatora|funkcja wewnętrzna numerycznego limitu kompilatora wymaga argumentu literału ciągu|  
|[C2364 błąd kompilatora](compiler-error-c2364.md)|"*typu*": niedozwolony typ niestandardowegp atrybutu|  
|[C2365 błąd kompilatora](compiler-error-c2365.md)|"*Członek1*": zmiana definicji; definicja poprzedniej został "*member2*"|  
|C2366 błąd kompilatora|"*identyfikator*": zmiana definicji; specyfikatory różnych implementation_key|  
|C2367 błąd kompilatora|Nieaktualne.|  
|[C2368 błąd kompilatora](compiler-error-c2368.md)|"*identyfikator*": zmiana definicji; specyfikatory różnych alokacji|  
|[C2369 błąd kompilatora](compiler-error-c2369.md)|"*identyfikator*": zmiana definicji; różne indeksy dolne|  
|[C2370 błąd kompilatora](compiler-error-c2370.md)|"*identyfikator*": zmiana definicji; różne klasy magazynu|  
|[C2371 błąd kompilatora](compiler-error-c2371.md)|"*identyfikator*": zmiana definicji; różne typy podstawowe|  
|[C2372 błąd kompilatora](compiler-error-c2372.md)|"*identyfikator*": zmiana definicji; różne typy pośredniego wywołania|  
|[C2373 błąd kompilatora](compiler-error-c2373.md)|"*identyfikator*": zmiana definicji; różne typy modyfikatorów|  
|[C2374 błąd kompilatora](compiler-error-c2374.md)|"*identyfikator*": zmiana definicji; inicjowanie wielu|  
|[C2375 błąd kompilatora](compiler-error-c2375.md)|"*identyfikator*": zmiana definicji; różne połączenie|  
|[C2376 błąd kompilatora](compiler-error-c2376.md)|"*identyfikator*": zmiana definicji; różne na podstawie alokacji|  
|[C2377 błąd kompilatora](compiler-error-c2377.md)|"*identyfikator*": zmiana definicji; typedef nie może zostać przeciążony przez dowolny inny symbol|  
|[C2378 błąd kompilatora](compiler-error-c2378.md)|"*identyfikator*": zmiana definicji; symbol nie może zostać przeciążony przez TypeDef|  
|[C2379 błąd kompilatora](compiler-error-c2379.md)|formalny parametr *numer* jest innego typu kiedy jest zwiększany|  
|[C2380 błąd kompilatora](compiler-error-c2380.md)|Typ(-y) poprzedzający(-e) "*identyfikator*" (Konstruktor z typem zwracanym lub niedozwolona próba ponownego zdefiniowania bieżącej nazwy klasy?)|  
|[C2381 błąd kompilatora](compiler-error-c2381.md)|"*identyfikator*": zmiana definicji; "__declspec(noreturn)" lub "[[noreturn]]" różni się|  
|[C2382 błąd kompilatora](compiler-error-c2382.md)|"*identyfikator*": zmiana definicji; różne specyfikacje wyjątków|  
|[C2383 błąd kompilatora](compiler-error-c2383.md)|"*identyfikator*": argumenty domyślne są niedozwolone w tym symbolu|  
|[C2384 błąd kompilatora](compiler-error-c2384.md)|"*elementu członkowskiego*": nie można zastosować elementu thread_local lub __declspec(thread) do elementu członkowskiego klasy managed WinRT|  
|[C2385 błąd kompilatora](compiler-error-c2385.md)|niejednoznaczne dostęp "*elementu członkowskiego*"|  
|[C2386 błąd kompilatora](compiler-error-c2386.md)|"*identyfikator*": symbol o tej nazwie już istnieje w bieżącym zakresie|  
|[C2387 błąd kompilatora](compiler-error-c2387.md)|"*identyfikator*": niejednoznaczna klasa podstawowa|  
|[C2388 błąd kompilatora](compiler-error-c2388.md)|"*identyfikator*": nie można zadeklarować symbolu z __declspec(process) i __declspec(appdomain)|  
|[C2389 błąd kompilatora](compiler-error-c2389.md)|"*operator*": niedozwolony operand "nullptr"|  
|[C2390 błąd kompilatora](compiler-error-c2390.md)|"*identyfikator*": klasa niewłaściwej*specyfikator*"|  
|[C2391 błąd kompilatora](compiler-error-c2391.md)|"*identyfikator*": "friend" nie może zostać użyty podczas definicji typu|  
|[C2392 błąd kompilatora](compiler-error-c2392.md)|"*Członek1*": typy nie są obsługiwane w typach zarządzanych WinRT, w przeciwnym razie zwraca kowariantnego "*member2*" zostanie przesłonięte|  
|[C2393 błąd kompilatora](compiler-error-c2393.md)|"*symbol*": symbol per-appdomain nie może zostać alokowany w segmencie "*segmentu*"|  
|[C2394 błąd kompilatora](compiler-error-c2394.md)|"*typu*:: operator *operator*": operator CLR i WinRT nie jest prawidłowy. Co najmniej jeden parametr musi być następujących typów: 'T ^ ", t ^ %", t ^ & ", gdzie T ="*typu*"|  
|[C2395 błąd kompilatora](compiler-error-c2395.md)|"*typu*:: operator *operator*": operator CLR i WinRT nie jest prawidłowy. Co najmniej jeden parametr musi być następujących typów: 'T ", 'T %", t & ", można ^", 'T ^ % ", 'T ^ &", gdzie T = "*typu*"|  
|[C2396 błąd kompilatora](compiler-error-c2396.md)|"*type1*:: operator *type2*": funkcja zdefiniowana przez użytkownika konwersja CLR i WinRT nie jest prawidłowy. Należy konwertować z albo konwertować na: 'T ^ ", t ^ %", t ^ & ", gdzie T ="*type1*"|  
|[C2397 błąd kompilatora](compiler-error-c2397.md)|Konwersja z "*type1*"do"*type2*" wymaga konwersji zawężającej|  
|C2398 błąd kompilatora|Element "*numer*": konwersja z "*type1*"do"*type2*" wymaga konwersji zawężającej|  
|C2399 błąd kompilatora|Nieaktualne.|  
