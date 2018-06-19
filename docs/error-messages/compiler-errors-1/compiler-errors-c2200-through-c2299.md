---
title: C2200 błędy kompilatora za pośrednictwem C2299 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
helpviewer_keywords:
- C2202
- C2209
- C2210
- C2211
- C2214
- C2215
- C2221
- C2225
- C2230
- C2235
- C2237
- C2239
- C2240
- C2257
- C2260
- C2263
- C2265
- C2269
- C2278
- C2281
- C2282
- C2288
- C2291
- C2294
dev_langs:
- C++
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 567cd6a9cbb042027b13056fe50330b31f326529
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236864"
---
# <a name="compiler-errors-c2200-through-c2299"></a>C2200 błędy kompilatora za pośrednictwem C2299

Artykuły w tej sekcji dokumentacji opisano podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2200](compiler-error-c2200.md)|"*funkcja*": funkcja została już zdefiniowana.|
|[Błąd kompilatora C2201](compiler-error-c2201.md)|"*identyfikator*": musi mieć zewnętrzne połączenie w celu eksportu/importu|
|C2202 błąd kompilatora|"*funkcja*": niewszystkie ścieżki kodu zwracają wartość|
|[Błąd kompilatora C2203](compiler-error-c2203.md)|Usuwanie operatora nie można określić zakresu tablicy|
|[Błąd kompilatora C2204](compiler-error-c2204.md)|"*typu*": definicja typu znaleziona w nawiasach|
|[Błąd kompilatora C2205](compiler-error-c2205.md)|"*identyfikator*": nie można zainicjalizować zmiennych extern w zakresie bloku|
|[Błąd kompilatora C2206](compiler-error-c2206.md)|"*funkcja*": element typedef nie może służyć do definicji funkcji|
|[Błąd kompilatora C2207](compiler-error-c2207.md)|"*elementu członkowskiego*": elementu członkowskiego szablonu klasy nie można pobrać typu funkcji|
|[Błąd kompilatora C2208](compiler-error-c2208.md)|"*typu*": Brak członków zdefiniowanych przy użyciu tego typu|
|C2209 błąd kompilatora|"*identyfikator*": aliasów nie można używać w deklaracjach konstruktorów|
|C2210 błąd kompilatora|"*identyfikator*": rozszerzenia pakietów nie może być używane jako argumenty niespakowane w szablonach aliasów|
|C2211 błąd kompilatora|Niewirtualny destruktor w klasie ref pochodzący z klasy ref z destruktorem publicznym również musi być publiczny|
|[Błąd kompilatora C2212](compiler-error-c2212.md)|"*identyfikator*": __based nie jest dostępny dla wskaźników do funkcji|
|[Błąd kompilatora C2213](compiler-error-c2213.md)|"*identyfikator*": niedozwolony argument dla __based|
|C2214 błąd kompilatora|wskaźniki oparte na "void" wymagają użycia: >|
|C2215 błąd kompilatora|"*— słowo kluczowe*" nie można używać z "/ arch: SSE"|
|[Błąd kompilatora C2216](compiler-error-c2216.md)|"*keyword1*"nie można używać z"*keyword2*"|
|[Błąd kompilatora C2217](compiler-error-c2217.md)|"*attribute1*"wymaga"*attribute2*"|
|[Błąd kompilatora C2218](compiler-error-c2218.md)|"*typ_wywołania*" nie można używać z "/ arch: IA32"|
|[Błąd kompilatora C2219](compiler-error-c2219.md)|Błąd składni: po musi występować kwalifikator typu "*"|
|[Błąd kompilatora C2220](compiler-error-c2220.md)|Ostrzeżenie potraktowano jako błąd — nie "*filetype*" plik wygenerowany|
|C2221 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2222](compiler-error-c2222.md)|Nieoczekiwany typ "*typu*": Oczekiwano klasy bazowej lub elementu członkowskiego|
|[Błąd kompilatora C2223](compiler-error-c2223.md)|po lewej "->*identyfikator*' musi wskazywać na struct/union|
|[Błąd kompilatora C2224](compiler-error-c2224.md)|po lewej ". *identyfikator*"musi mieć typ struct/union|
|C2225 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2226](compiler-error-c2226.md)|Błąd składniowy: nieoczekiwany typ "*typu*"|
|[Błąd kompilatora C2227](compiler-error-c2227.md)|po lewej "->*identyfikator*' musi wskazywać na typ klasy/struktury/Unii/generic|
|[Błąd kompilatora C2228](compiler-error-c2228.md)|po lewej ". *identyfikator*"musi mieć klasy/struktury/Unii|
|[Błąd kompilatora C2229](compiler-error-c2229.md)|klasy/struktury/Unii "*typu*" ma niedozwolony zerowy rozmiar tablicy|
|C2230 błąd kompilatora|Nie można odnaleźć modułu "*nazwa*"|
|[Błąd kompilatora C2231](compiler-error-c2231.md)|'. *identyfikator*": lewy argument operacji wskazuje"class/struct/union", użyj"->"|
|[Błąd kompilatora C2232](compiler-error-c2232.md)|"->*identyfikator*": lewy argument operacji ma "class/struct/union" typ, użyj"."|
|[Błąd kompilatora C2233](compiler-error-c2233.md)|"*identyfikator*": niedozwolone są tablice obiektów zawierające tablice o rozmiarze zerowym|
|[Błąd kompilatora C2234](compiler-error-c2234.md)|*Identyfikator*": tablice odwołań są niedozwolone|
|C2235 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2236](compiler-error-c2236.md)|Nieoczekiwany token "*tokenu*". Zapomnialeś ';'?|
|C2237 błąd kompilatora|wiele deklaracji modułu|
|[Błąd kompilatora C2238](compiler-error-c2238.md)|nieoczekiwane tokeny poprzedniego "*tokenu*"|
|C2239 błąd kompilatora|"*funkcja*": próba usunięcia funkcji __declspec(dllexport)|
|C2240 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2241](compiler-error-c2241.md)|"*identyfikator*": dostęp do elementu członkowskiego jest ograniczony|
|[Błąd kompilatora C2242](compiler-error-c2242.md)|Nazwa typu TypeDef nie może następować po klasy/struktury/Unii|
|[Błąd kompilatora C2243](compiler-error-c2243.md)|"*conversion_type*": konwersja z "*type1*"do"*type2*" istnieje, ale jest niedostępna|
|[Błąd kompilatora C2244](compiler-error-c2244.md)|"*identyfikator*": nie można dopasować definicji funkcji do istniejącej deklaracji|
|[Błąd kompilatora C2245](compiler-error-c2245.md)|nieistniejący element członkowski funkcji "*funkcja*" określony jako przyjaciel (sygnatura funkcji członkowskiej nie dopasowania do żadnego przeciążenia)|
|[Błąd kompilatora C2246](compiler-error-c2246.md)|"*identyfikator*": niedozwolony statyczny element członkowski danych zdefiniowany lokalnie w klasie|
|[Błąd kompilatora C2247](compiler-error-c2247.md)|"*identyfikator*" nie jest dostępna, ponieważ "*class1*"używa"*specyfikator*" Aby dziedziczyć z"*class2*"|
|[Błąd kompilatora C2248](compiler-error-c2248.md)|"*identyfikator*": nie można uzyskać dostępu *dostępności* *elementu członkowskiego* zadeklarowana w klasie*klasy*"|
|[Błąd kompilatora C2249](compiler-error-c2249.md)|"*identyfikator*": Brak dostępnej ścieżki do *dostępności* *elementu członkowskiego* zadeklarowanej w wirtualnej podstawowej "*klasy*"|
|[Błąd kompilatora C2250](compiler-error-c2250.md)|"*identyfikator*": niejednoznaczne dziedziczenie *klasy*::*elementu członkowskiego*"|
|[Błąd kompilatora C2251](compiler-error-c2251.md)|przestrzeń nazw "*przestrzeni nazw*"nie ma element członkowski"*identyfikator*"-Czy chodziło o "*elementu członkowskiego*"?|
|[Błąd kompilatora C2252](compiler-error-c2252.md)|Jawne tworzenie instancji szablonu może nastąpić tylko w zakresie przestrzeni nazw|
|[Błąd kompilatora C2253](compiler-error-c2253.md)|"*funkcja*": czysty specyfikator lub abstrakcyjny specyfikator override dozwolony tylko w funkcji wirtualnej|
|[Błąd kompilatora C2254](compiler-error-c2254.md)|"*funkcja*": czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla funkcji zaprzyjaźnionej|
|[Błąd kompilatora C2255](compiler-error-c2255.md)|"*elementu*": niedozwolone poza definicją klasy|
|[Błąd kompilatora C2256](compiler-error-c2256.md)|niedozwolone użycie zaprzyjaźnionego specyfikatora na "*funkcja*"|
|C2257 błąd kompilatora|"*specyfikator*": specyfikator jest niedozwolony w końcowym typie zwracanym|
|[Błąd kompilatora C2258](compiler-error-c2258.md)|Niedozwolona czysta składnia, musi być "= 0"|
|[Błąd kompilatora C2259](compiler-error-c2259.md)|"*klasy*": nie można utworzyć wystąpienia klasy abstrakcyjnej|
|C2260 błąd kompilatora|"*specyfikator*": Nieprawidłowy specyfikator InternalsVisibleToAttribute zaprzyjaźnionego zestawu|
|[Błąd kompilatora C2261](compiler-error-c2261.md)|"*ciąg*": odwołanie do zestawu jest nieprawidłowa i nie można go rozpoznać|
|[Błąd kompilatora C2262](compiler-error-c2262.md)|"*specyfikator*": Deklaracje InternalsVisibleTo nie mogą mieć wersji, kultury ani architektury procesora określona|
|C2263 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2264](compiler-error-c2264.md)|"*funkcja*": błąd w definicji funkcji lub deklaracji; nie wywołano funkcji|
|C2265 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2266](compiler-error-c2266.md)|"*identyfikator*": odwołanie do tablicy o nieustalonym zakresie z systemem innym niż stała jest niedozwolony|
|[Błąd kompilatora C2267](compiler-error-c2267.md)|"*funkcja*": funkcje statyczne w zakresie bloku są niedozwolone|
|[Błąd kompilatora C2268](compiler-error-c2268.md)|"*funkcja*" jest pomocnika biblioteki kompilatora wstępnie zdefiniowane. Biblioteka pomocników nie jest obsługiwana z opcją /GL; Skompiluj plik obiektu "*filename*" bez/GL.|
|C2269 błąd kompilatora|Nie można utworzyć wskaźnika ani odwołania do kwalifikowanego typu funkcji (wymaga wskaźnika do elementu członkowskiego)|
|[Błąd kompilatora C2270](compiler-error-c2270.md)|"*funkcja*": Modyfikatory niedozwolone dla funkcji niebędących funkcjami Członkowskimi|
|[Błąd kompilatora C2271](compiler-error-c2271.md)|"*funkcja*": nowy/delete nie może mieć formalnej listy modyfikatorów|
|[Błąd kompilatora C2272](compiler-error-c2272.md)|"*funkcja*": Modyfikatory niedozwolone dla statycznych funkcji Członkowskich|
|[Błąd kompilatora C2273](compiler-error-c2273.md)|"*typu*": niedozwolony po prawej stronie operatora "->"|
|[Błąd kompilatora C2274](compiler-error-c2274.md)|"*typu*": niedozwolony po prawej stronie '.' — operator|
|[Błąd kompilatora C2275](compiler-error-c2275.md)|"*typu*": niedozwolone użycie tego typu jako wyrażenia|
|[Błąd kompilatora C2276](compiler-error-c2276.md)|"*operator*": Niedozwolona operacja na wyrażeniu związanym funkcji członkowskiej|
|[Błąd kompilatora C2277](compiler-error-c2277.md)|"*funkcja*": nie można pobrać adresu funkcji członkowskiej|
|C2278 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2279](compiler-error-c2279.md)|Specyfikacja wyjątku nie może występować w deklaracji typedef|
|[Błąd kompilatora C2280](compiler-error-c2280.md)|"*klasy*::*funkcja*": próba odwołania usunięta funkcja|
|C2281 błąd kompilatora|"*klasy*::*funkcja*": funkcję można usunąć tylko na pierwszej deklaracji|
|C2282 błąd kompilatora|"*function1*nie może zastąpić*function2*"|
|[Błąd kompilatora C2283](compiler-error-c2283.md)|"*identyfikatorem*": czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla nienazwanego klasie/strukturze|
|C2284 błąd kompilatora|"*funkcja*": niedozwolony argument wewnętrznej funkcji, parametr *numer*|
|[Błąd kompilatora C2285](compiler-error-c2285.md)|wskaźniki do członków reprezentacji zostały już ustalone - pragma ignorowane|
|[Błąd kompilatora C2286](compiler-error-c2286.md)|wskaźniki do elementów członkowskich "*identyfikator*" reprezentacja ma już ustawioną *dziedziczenia* -deklaracja ignorowana|
|[Błąd kompilatora C2287](compiler-error-c2287.md)|"*identyfikator*": reprezentacja dziedziczenia: "*inheritiance*"jest mniej ogólny niż wymagany"*dziedziczenia*"|
|C2288 błąd kompilatora|Nieaktualne.|
|[Błąd kompilatora C2289](compiler-error-c2289.md)|Kwalifikator użyty więcej niż raz tego samego typu|
|[Błąd kompilatora C2290](compiler-error-c2290.md)|Składnia "asm" C++ ignorowane. Użyj __asm.|
|C2291 błąd kompilatora|Nie można eksportować anonimowej przestrzeni nazw.|
|[Błąd kompilatora C2292](compiler-error-c2292.md)|"*identyfikator*": Najlepsza reprezentacja dziedziczenia w przypadku: *inheritance1*"zadeklarowana ale"*inheritance2*"wymagane|
|[Błąd kompilatora C2293](compiler-error-c2293.md)|"*identyfikator*": niedozwolony zmiennej członkowskiej jako specyfikator __based|
|C2294 błąd kompilatora|Nie można wyeksportować symbolu "*identyfikator*", ponieważ ma połączenie zewnętrzne|
|[Błąd kompilatora C2295](compiler-error-c2295.md)|znaki ucieczki "*znak*": jest niedozwolony w definicji makra|
|[Błąd kompilatora C2296](compiler-error-c2296.md)|"*operator*": niedozwolone, lewy operand jest typu "*typu*"|
|[Błąd kompilatora C2297](compiler-error-c2297.md)|"*operator*": niedozwolone, prawy operand jest typu "*typu*"|
|[Błąd kompilatora C2298](compiler-error-c2298.md)|brakujące wywołanie do wskaźnika granicy dla funkcji członkowskiej|
|[Błąd kompilatora C2299](compiler-error-c2299.md)|"*funkcja*": Zmiana zachowania: jawną specjalizacją nie może być Konstruktor kopiujący lub kopia operatora przypisania|
