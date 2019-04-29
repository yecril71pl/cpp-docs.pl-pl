---
title: Błędy kompilatora — od C2200 do C2299
ms.date: 04/21/2019
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
ms.assetid: 9b36d11b-9510-4390-96f1-0c9235124d14
ms.openlocfilehash: 5af97ab46a97d3019abcc937cc0a74c5f865a9ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360518"
---
# <a name="compiler-errors-c2200-through-c2299"></a>Błędy kompilatora — od C2200 do C2299

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2200](compiler-error-c2200.md)|"*funkcja*": funkcja została już zdefiniowana|
|[Compiler error C2201](compiler-error-c2201.md)|"*identyfikator*": musi mieć zewnętrzne połączenie w celu eksportu/importu|
|Błąd kompilatora C2202|"*funkcja*": niewszystkie ścieżki kodu zwracają wartość|
|[Błąd kompilatora C2203](compiler-error-c2203.md)|Usuń operator nie może określić zakresu tablicy|
|[Compiler error C2204](compiler-error-c2204.md)|"*typu*": definicja typu znaleziona w nawiasach|
|[Compiler error C2205](compiler-error-c2205.md)|"*identyfikator*": nie można zainicjalizować zmiennych extern w zakresie bloku|
|[Compiler error C2206](compiler-error-c2206.md)|"*funkcja*": typedef nie można używać do definicji funkcji|
|[Błąd kompilatora C2207](compiler-error-c2207.md)|"*elementu członkowskiego*": składowej szablonu klasy nie może uzyskać typu funkcji|
|[Compiler error C2208](compiler-error-c2208.md)|"*typu*": Brak składowych zdefiniowanych przy użyciu tego typu|
|Compiler error C2209|"*identyfikator*": aliasów nie można używać w deklaracjach konstruktorów|
|Błąd kompilatora C2210|"*identyfikator*": rozszerzenia pakietów nie można użyć jako argumenty niespakowanych parametrów w szablonach aliasów|
|Błąd kompilatora C2211|Niewirtualny destruktor w klasie ref pochodzący od klasy ref z destruktorem publicznym również musi być publiczny|
|[Błąd kompilatora C2212](compiler-error-c2212.md)|"*identyfikator*": __based nie jest dostępny dla wskaźników do funkcji|
|[Błąd kompilatora C2213](compiler-error-c2213.md)|"*identyfikator*": niedozwolony argument dla __based|
|Błąd kompilatora C2214|wskaźniki oparte na "void" wymagają użycia: >|
|Błąd kompilatora C2215|"*— słowo kluczowe*" nie można używać z "/ arch: SSE"|
|[Błąd kompilatora C2216](compiler-error-c2216.md)|"*keyword1*"nie można używać z"*keyword2*"|
|[Błąd kompilatora C2217](compiler-error-c2217.md)|"*attribute1*"wymaga"*attribute2*"|
|[Błąd kompilatora C2218](compiler-error-c2218.md)|"*calltype*" nie można używać z "/ arch: IA32"|
|[Compiler error C2219](compiler-error-c2219.md)|Błąd składniowy: po musi występować kwalifikator typu "*"|
|[Błąd kompilatora C2220](compiler-error-c2220.md)|Ostrzeżenie potraktowano jako błąd - nie "*typ_pliku*" pliku wygenerowanego|
|Błąd kompilatora C2221|Nieaktualne.|
|[Błąd kompilatora C2222](compiler-error-c2222.md)|Nieoczekiwany typ "*typu*": Oczekiwano klasy bazowej lub składowej|
|[Błąd kompilatora C2223](compiler-error-c2223.md)|po lewej "->*identyfikator*" musi wskazywać na struct/union|
|[Błąd kompilatora C2224](compiler-error-c2224.md)|po lewej ". *identyfikator*"musi być typ struct/union|
|Błąd kompilatora C2225|Nieaktualne.|
|[Błąd kompilatora C2226](compiler-error-c2226.md)|Błąd składniowy: nieoczekiwany typ "*typu*"|
|[Błąd kompilatora C2227](compiler-error-c2227.md)|po lewej "->*identyfikator*" musi wskazywać typ klasy/struct/union/generic|
|[Błąd kompilatora C2228](compiler-error-c2228.md)|po lewej ". *identyfikator*"musi mieć klasy/struct/union|
|[Błąd kompilatora C2229](compiler-error-c2229.md)|Klasa/struct/union "*typu*" ma niedozwolony zerowy rozmiar tablicy|
|Błąd kompilatora C2230|Nie można odnaleźć modułu "*nazwa*"|
|[Błąd kompilatora C2231](compiler-error-c2231.md)|'. *identyfikator*": lewy argument operacji wskazuje"class/struct/union", użyj opcji"->"|
|[Błąd kompilatora C2232](compiler-error-c2232.md)|"->*identyfikator*": lewy operand "class/struct/union ' type, użyj"."|
|[Błąd kompilatora C2233](compiler-error-c2233.md)|"*identyfikator*": niedozwolone są tablice obiektów zawierające tablice o rozmiarze zerowym|
|[Błąd kompilatora C2234](compiler-error-c2234.md)|*Identyfikator*": tablice odwołań są niedozwolone|
|Błąd kompilatora C2235|Nieaktualne.|
|[Błąd kompilatora C2236](compiler-error-c2236.md)|Nieoczekiwany token "*tokenu*". Zapomnialeś ';'?|
|Błąd kompilatora C2237|Deklaracja wielu modułów|
|[Błąd kompilatora C2238](compiler-error-c2238.md)|Nieoczekiwany(e) token(y) poprzedniego "*tokenu*"|
|Błąd kompilatora C2239|"*funkcja*": próba usunięcia funkcji __declspec(dllexport)|
|Błąd kompilatora C2240|Nieaktualne.|
|[Błąd kompilatora C2241](compiler-error-c2241.md)|"*identyfikator*": dostęp do składowej jest ograniczony|
|[Błąd kompilatora C2242](compiler-error-c2242.md)|Nazwa TypeDef nie mogą następować po klasie/struct/union|
|[Błąd kompilatora C2243](compiler-error-c2243.md)|"*conversion_type*': konwersja z"*type1*"to"*type2*"istnieje, ale jest niedostępna|
|[Błąd kompilatora C2244](compiler-error-c2244.md)|"*identyfikator*": nie można dopasować definicji funkcji do istniejącej deklaracji|
|[Błąd kompilatora C2245](compiler-error-c2245.md)|Funkcja elementu członkowskiego nieistniejącej "*funkcja*" określona jako friend (sygnatura funkcji składowej nie pasuje do żadnego przeciążenia)|
|[Błąd kompilatora C2246](compiler-error-c2246.md)|"*identyfikator*": niedozwolona statyczna składowa danych zdefiniowana lokalnie w klasie|
|[Błąd kompilatora C2247](compiler-error-c2247.md)|"*identyfikator*" nie jest dostępny ponieważ "*klasa1*"używa"*specyfikator*" Aby odziedziczyć po"*klasa2*"|
|[Compiler error C2248](compiler-error-c2248.md)|"*identyfikator*": nie można uzyskać dostępu *ułatwień dostępu* *elementu członkowskiego* zadeklarowana w klasie*klasy*"|
|[Compiler error C2249](compiler-error-c2249.md)|"*identyfikator*": Brak dostępnej ścieżki do *ułatwień dostępu* *elementu członkowskiego* zadeklarowanej w wirtualnej podstawowej "*klasy*"|
|[Błąd kompilatora C2250](compiler-error-c2250.md)|"*identyfikator*": niejednoznaczne dziedziczenie *klasy*::*elementu członkowskiego*"|
|[Compiler error C2251](compiler-error-c2251.md)|przestrzeń nazw "*przestrzeni nazw*"nie ma składowej"*identyfikator*" — Czy chodziło Ci o "*elementu członkowskiego*"?|
|[Compiler error C2252](compiler-error-c2252.md)|Jawne tworzenie instancji szablonu może nastąpić tylko w zakresie przestrzeni nazw|
|[Błąd kompilatora C2253](compiler-error-c2253.md)|"*funkcja*": czysty specyfikator lub abstrakcyjny specyfikator override dozwolony tylko dla wirtualnej funkcji|
|[Błąd kompilatora C2254](compiler-error-c2254.md)|"*funkcja*": czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla funkcji zaprzyjaźnionej|
|[Błąd kompilatora C2255](compiler-error-c2255.md)|"*elementu*": niedozwolone poza definicją klasy|
|[Compiler error C2256](compiler-error-c2256.md)|niedozwolone użycie zaprzyjaźnionego specyfikatora na "*funkcja*"|
|Błąd kompilatora C2257|"*specyfikator*": specyfikator jest niedozwolony w końcowym typie zwracanym|
|[Compiler error C2258](compiler-error-c2258.md)|Niedozwolona czysta składnia, musi być "= 0"|
|[Compiler error C2259](compiler-error-c2259.md)|"*klasy*": nie można utworzyć wystąpienia klasy abstrakcyjnej|
|Błąd kompilatora C2260|"*specyfikator*": Nieprawidłowy specyfikator InternalsVisibleToAttribute zaprzyjaźnionego zestawu|
|[Błąd kompilatora C2261](compiler-error-c2261.md)|"*ciąg*": odwołanie do zestawu jest nieprawidłowa i nie można go rozpoznać|
|[Błąd kompilatora C2262](compiler-error-c2262.md)|"*specyfikator*": Deklaracje InternalsVisibleTo nie mogą mieć wersji, kultury ani architektury procesora|
|Błąd kompilatora C2263|Nieaktualne.|
|[Błąd kompilatora C2264](compiler-error-c2264.md)|"*funkcja*": błąd w deklaracji lub definicji funkcji; nie wywołano funkcji|
|Błąd kompilatora C2265|Nieaktualne.|
|[Błąd kompilatora C2266](compiler-error-c2266.md)|"*identyfikator*": odwołanie do tablicy o nieustalonym zakresie innego niż stała jest niedozwolony|
|[Błąd kompilatora C2267](compiler-error-c2267.md)|"*funkcja*": funkcje statyczne w zakresie bloku są niedozwolone|
|[Compiler error C2268](compiler-error-c2268.md)|"*funkcja*" jest pomocnika biblioteki kompilatora wstępnie zdefiniowane. Biblioteka pomocników nie jest obsługiwana z opcją /GL; kompilowanie pliku obiektu "*filename*" bez/GL.|
|Błąd kompilatora C2269|Nie można utworzyć wskaźnik lub odwołanie do typu funkcji kwalifikowanej (wymaga wskaźników do elementów członkowskich)|
|[Błąd kompilatora C2270](compiler-error-c2270.md)|"*funkcja*": Modyfikatory niedozwolone dla funkcji niebędących funkcjami Członkowskimi|
|[Błąd kompilatora C2271](compiler-error-c2271.md)|"*funkcja*": nowy/delete nie może mieć formalnej listy modyfikatorów|
|[Błąd kompilatora C2272](compiler-error-c2272.md)|"*funkcja*": Modyfikatory niedozwolone dla statycznych funkcji składowych|
|[Błąd kompilatora C2273](compiler-error-c2273.md)|"*typu*": niedozwolony po prawej stronie operatora "->"|
|[Błąd kompilatora C2274](compiler-error-c2274.md)|"*typu*": niedozwolony po prawej stronie "." — operator|
|[Błąd kompilatora C2275](compiler-error-c2275.md)|"*typu*": niedozwolone użycie tego typu jako wyrażenia|
|[Błąd kompilatora C2276](compiler-error-c2276.md)|"*operator*": Niedozwolona operacja na wyrażeniu związanym funkcji składowej|
|[Błąd kompilatora C2277](compiler-error-c2277.md)|"*funkcja*": nie można przyjąć adresu funkcji składowej|
|Błąd kompilatora C2278|Nieaktualne.|
|[Compiler error C2279](compiler-error-c2279.md)|Specyfikacja wyjątku nie może występować w deklaracji typedef|
|[Błąd kompilatora C2280](compiler-error-c2280.md)|"*klasy*::*funkcja*": próba odwania do usuniętej funkcji do|
|Błąd kompilatora C2281|"*klasy*::*funkcja*": funkcja może zostać usunięta tylko na pierwszej deklaracji|
|Błąd kompilatora C2282|"*function1*nie może przesłonić*function2*"|
|[Błąd kompilatora C2283](compiler-error-c2283.md)|"*identyfikator*": czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony w klasie/strukturze bez nazwy|
|Błąd kompilatora C2284|"*funkcja*": niedozwolony argument wewnętrznej funkcji, parametr *numer*|
|[Błąd kompilatora C2285](compiler-error-c2285.md)|wskaźniki do składowych reprezentacji ma zostały już ustalone — pragma ignorowane|
|[Compiler error C2286](compiler-error-c2286.md)|wskaźniki do elementów członkowskich "*identyfikator*" reprezentacji ustawiono już *dziedziczenia* — deklaracja ignorowana|
|[Błąd kompilatora C2287](compiler-error-c2287.md)|"*identyfikator*": reprezentacja dziedziczenia: "*inheritiance*"jest mniej ogólny niż wymagany"*dziedziczenia*"|
|Błąd kompilatora C2288|Nieaktualne.|
|[Compiler error C2289](compiler-error-c2289.md)|tym samym kwalifikator typu użyty więcej niż raz|
|[Compiler error C2290](compiler-error-c2290.md)|Składnia "asm" C++ ignorowane. Użyj __asm.|
|Błąd kompilatora C2291|Nie można eksportować anonimowej przestrzeni nazw.|
|[Błąd kompilatora C2292](compiler-error-c2292.md)|"*identyfikator*": reprezentacja dziedziczenia w przypadku najlepiej: *inheritance1*"zadeklarowana ale"*inheritance2*"wymagane|
|[Błąd kompilatora C2293](compiler-error-c2293.md)|"*identyfikator*": niedozwolony zmiennej składowej jako specyfikatora __based|
|Błąd kompilatora C2294|Nie można wyeksportować symbolu "*identyfikator*", ponieważ ma połączenie zewnętrzne|
|[Błąd kompilatora C2295](compiler-error-c2295.md)|poprzedzone znakiem zmiany znaczenia "*znak*": jest niedozwolony w definicji makra|
|[Compiler error C2296](compiler-error-c2296.md)|"*operator*": niedozwolone, Lewy argument operacji ma typ "*typu*"|
|[Błąd kompilatora C2297](compiler-error-c2297.md)|"*operator*": niedozwolone, prawy operand jest typu "*typu*"|
|[Compiler error C2298](compiler-error-c2298.md)|brakujące wywołanie do wskaźnika granicy dla funkcji członkowskiej|
|[Compiler error C2299](compiler-error-c2299.md)|"*funkcja*": Zmiana zachowania: jawną specjalizacją nie może być Konstruktor kopiujący lub kopia operatora przypisania|

## <a name="see-also"></a>Zobacz także

[C /C++ kompilatora i tworzenia błędy i ostrzeżenia narzędzi](../compiler-errors-1/c-cpp-build-errors.md) \
[Błędy kompilatora — od C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
