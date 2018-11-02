---
title: Błędy kompilatora — od C2100 do C2199
ms.date: 11/17/2017
f1_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
helpviewer_keywords:
- C2119
- C2123
- C2125
- C2126
- C2127
- C2131
- C2136
- C2176
- C2187
- C2189
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
ms.openlocfilehash: 98e804b7c53eddf239e752f120854439cc3a0b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546567"
---
# <a name="compiler-errors-c2100-through-c2199"></a>Błędy kompilatora — od C2100 do C2199

Artykuły w tej sekcji dokumentacji wyjaśniają podzbiór komunikaty o błędach, które są generowane przez kompilator.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Komunikaty o błędach

|Błąd|Komunikat|
|-----------|-------------|
|[Błąd kompilatora C2100](compiler-error-c2100.md)|Niedozwolony operator pośredni|
|[Błąd kompilatora C2101](compiler-error-c2101.md)|"&" na — stała|
|[Błąd kompilatora C2102](compiler-error-c2102.md)|"&" wymaga wartości l|
|[Błąd kompilatora C2103](compiler-error-c2103.md)|"&" w rejestrze zmiennej|
|[Błąd kompilatora C2104](compiler-error-c2104.md)|"&" na pole bitowe ignorowane|
|[Błąd kompilatora C2105](compiler-error-c2105.md)|"*operator*" wymaga wartości l|
|[Błąd kompilatora C2106](compiler-error-c2106.md)|"*operator*": lewy operand musi być l wartości|
|[Błąd kompilatora C2107](compiler-error-c2107.md)|Nieprawidłowy indeks, pośrednik niedozwolony|
|[Błąd kompilatora C2108](compiler-error-c2108.md)|Indeks dolny nie jest typem całkowitym|
|[Błąd kompilatora C2109](compiler-error-c2109.md)|Indeks dolny wymaga tablicy lub wskaźnika typu|
|[Błąd kompilatora C2110](compiler-error-c2110.md)|"+": nie można dodać dwóch wskaźników|
|[Błąd kompilatora C2111](compiler-error-c2111.md)|"+": Dodawanie wskaźników wymaga całkowitego operandu|
|[Błąd kompilatora C2112](compiler-error-c2112.md)|"-": wskaźnik odejmowania wymaga wartości całkowitej lub wskaźnika operandu|
|[Błąd kompilatora C2113](compiler-error-c2113.md)|"-": wskaźnik może zostać odjęty tylko od innego wskaźnika|
|[Błąd kompilatora C2114](compiler-error-c2114.md)|"*operator*": wskaźnik po lewej stronie; wymaga całkowitej wartości po prawej stronie|
|[Błąd kompilatora C2115](compiler-error-c2115.md)|"*operator*": niezgodne typy|
|[Błąd kompilatora C2116](compiler-error-c2116.md)|listy parametrów funkcji różnił się|
|[Błąd kompilatora C2117](compiler-error-c2117.md)|"*identyfikator*": przepełnienie granic tablicy|
|[Błąd kompilatora C2118](compiler-error-c2118.md)|ujemny indeks dolny|
|C2119 błąd kompilatora|"*identyfikator*": typ dla "*typu*" nie można wywnioskować na podstawie pustego inicjalizatora|
|[Błąd kompilatora C2120](compiler-error-c2120.md)|"void" niedozwolone ze wszystkimi typami|
|[Błąd kompilatora C2121](compiler-error-c2121.md)|"#": nieprawidłowy znak: prawdopodobnie wynik rozwinięcia makra|
|[Błąd kompilatora C2122](compiler-error-c2122.md)|"*identyfikator*": parametr prototypu w liście nazw jest niedozwolony|
|C2123 błąd kompilatora|"*identyfikator*": szablony aliasów nie może być jawnie lub częściowo specjalizowany|
|[Błąd kompilatora C2124](compiler-error-c2124.md)|Dzielenie lub dzielenie modulo przez zero|
|C2125 błąd kompilatora|"constexpr" jest niezgodna z "*tokenu*"|
|C2126 błąd kompilatora|"*identyfikator*" nie można zadeklarować ze specyfikatorem "constexpr"|
|C2127 błąd kompilatora|"*identyfikator*": niedozwolone inicjowanie elementu "constexpr" jednostki o niestałe wyrażenie|
|[Błąd kompilatora C2128](compiler-error-c2128.md)|"*funkcja*": alloc_text/same_seg dotyczy tylko funkcji z powiązaniem C|
|[Błąd kompilatora C2129](compiler-error-c2129.md)|Funkcja statyczna "*identyfikator*" zadeklarowana ale niezdefiniowana|
|[Błąd kompilatora C2130](compiler-error-c2130.md)|#line oczekiwany ciąg zawierający nazwę pliku, znaleziono "*tokenu*"|
|C2131 błąd kompilatora|Wyrażenie nie zostało obliczone do stałej|
|[Błąd kompilatora C2132](compiler-error-c2132.md)|Błąd składniowy: nieoczekiwany identyfikator|
|[Błąd kompilatora C2133](compiler-error-c2133.md)|"*identyfikator*": nieznany rozmiar|
|[Błąd kompilatora C2134](compiler-error-c2134.md)|"*funkcja*": nie powoduje wywołanie w wyrażeniu stałym|
|[Błąd kompilatora C2135](compiler-error-c2135.md)|"*operator*": operacja na polu bitowym niedozwolone|
|C2136 błąd kompilatora|Tworzenie kontrakt interfejsu API, które nie są dozwolone|
|[Błąd kompilatora C2137](compiler-error-c2137.md)|pusty znak stałej|
|[Błąd kompilatora C2138](compiler-error-c2138.md)|niedozwolone jest zdefiniowanie wyliczenia bez składowych|
|[Błąd kompilatora C2139](compiler-error-c2139.md)|"*klasy*": Niezdefiniowana klasa nie jest dozwolona jako argument typu wewnętrznej cechy kompilatora "*cech*"|
|[Błąd kompilatora C2140](compiler-error-c2140.md)|"*typu*": typ, który jest zależny od parametru typu generycznego nie jest dozwolona jako argument typu wewnętrznej cechy kompilatora "*cech*"|
|[Błąd kompilatora C2141](compiler-error-c2141.md)|Przekroczono rozmiar tablicy|
|[Błąd kompilatora C2142](compiler-error-c2142.md)|deklaracje funkcji różnią się, parametry zmiennej określone tylko w jednej z nich|
|[Błąd kompilatora C2143](compiler-error-c2143.md)|Błąd składniowy: brakuje "*token1*"before"*token2*"|
|[Błąd kompilatora C2144](compiler-error-c2144.md)|Błąd składniowy: "*typu*"powinien być poprzedzony"*token2*"|
|[Błąd kompilatora C2145](compiler-error-c2145.md)|Błąd składniowy: brakuje "*tokenu*" przed identyfikatorem|
|[Błąd kompilatora C2146](compiler-error-c2146.md)|Błąd składniowy: brakuje "*tokenu*"przed identyfikatorem"*identyfikator*"|
|[Błąd kompilatora C2147](compiler-error-c2147.md)|Błąd składniowy: "*tokenu*" jest nowe słowo kluczowe|
|[Błąd kompilatora C2148](compiler-error-c2148.md)|Całkowity rozmiar tablicy nie może przekroczyć 0 x*wartość* bajtów|
|[Błąd kompilatora C2149](compiler-error-c2149.md)|"*identyfikator*": nazwane pole bitowe nie może mieć zerowej szerokości|
|[Błąd kompilatora C2150](compiler-error-c2150.md)|"*identyfikator*": pole bitowe musi być typu "int", "signed int" lub "unsigned int"|
|[Błąd kompilatora C2151](compiler-error-c2151.md)|więcej niż jeden atrybut językowy|
|[Błąd kompilatora C2152](compiler-error-c2152.md)|"*identyfikator*": wskaźniki do funkcji z różnymi atrybutami|
|[Błąd kompilatora C2153](compiler-error-c2153.md)|literały całkowite muszą mieć co najmniej jedną cyfrę|
|[Błąd kompilatora C2154](compiler-error-c2154.md)|"*typu*": tylko typ wyliczeniowy jest dozwolony jako argument typu wewnętrznej cechy kompilatora "*cech*"|
|[Błąd kompilatora C2155](compiler-error-c2155.md)|"?": lewy operand nieprawidłowy, oczekiwano arytmetycznego lub typu wskaźnika|
|[Błąd kompilatora C2156](compiler-error-c2156.md)|pragma musi znajdować się poza funkcją|
|[Błąd kompilatora C2157](compiler-error-c2157.md)|"*identyfikator*": musi być zadeklarowana przed użyciem w liście pragma|
|[Błąd kompilatora C2158](compiler-error-c2158.md)|"*typu*": #pragma make_public dyrektywa jest obecnie obsługiwana dla natywnych typów nieszablonowe|
|[Błąd kompilatora C2159](compiler-error-c2159.md)|więcej niż jedną klasę magazynu określony|
|[Błąd kompilatora C2160](compiler-error-c2160.md)|' ##' nie może występować na początku definicji makra|
|[Błąd kompilatora C2161](compiler-error-c2161.md)|' ##' nie może wystąpić na końcu definicji makra|
|[Błąd kompilatora C2162](compiler-error-c2162.md)|Oczekiwany parametr formalny makra|
|[Błąd kompilatora C2163](compiler-error-c2163.md)|"*funkcja*": nie jest dostępna jako funkcja wewnętrzna|
|[Błąd kompilatora C2164](compiler-error-c2164.md)|"*funkcja*": wewnętrzna funkcja nie jest zadeklarowana|
|[Błąd kompilatora C2165](compiler-error-c2165.md)|"*modyfikator*": nie można modyfikować wskaźników do danych|
|[Błąd kompilatora C2166](compiler-error-c2166.md)|wartość l Określa obiekt const|
|[Błąd kompilatora C2167](compiler-error-c2167.md)|"*funkcja*": zbyt wiele parametrów rzeczywistych dla wewnętrznej funkcji|
|[Błąd kompilatora C2168](compiler-error-c2168.md)|"*funkcja*": zbyt mało rzeczywistych parametrów w wewnętrznej funkcji|
|[Błąd kompilatora C2169](compiler-error-c2169.md)|"*funkcja*": wewnętrzna funkcja nie może być zdefiniowana|
|[Błąd kompilatora C2170](compiler-error-c2170.md)|"*identyfikator*": nie zadeklarowano jako funkcja, nie może być wewnętrzne|
|[Błąd kompilatora C2171](compiler-error-c2171.md)|"*operator*": niedozwolone na operandach typu "*typu*"|
|[Błąd kompilatora C2172](compiler-error-c2172.md)|"*funkcja*": rzeczywisty parametr nie jest wskaźnikiem: parametr *numer*|
|[Błąd kompilatora C2173](compiler-error-c2173.md)|"*funkcja*": rzeczywisty parametr nie jest wskaźnikiem: parametr *numer*, lista parametrów *numer*|
|[Błąd kompilatora C2174](compiler-error-c2174.md)|"*funkcja*": rzeczywisty parametr jest typu "void": parametr *numer*, lista parametrów *numer*|
|[Błąd kompilatora C2175](compiler-error-c2175.md)|"*ustawień regionalnych*": nieprawidłowe ustawienia regionalne|
|C2176 błąd kompilatora|instrukcja return nie może występować w procedurze obsługi funkcji bloku "try" skojarzonym z konstruktorem|
|[Błąd kompilatora C2177](compiler-error-c2177.md)|za duża stała|
|[Błąd kompilatora C2178](compiler-error-c2178.md)|"*identyfikator*"nie może być zadeklarowana z"*specyfikator*" Specyfikator|
|[Błąd kompilatora C2179](compiler-error-c2179.md)|"*typu*": argument atrybutu nie może używać parametrów typu|
|[Błąd kompilatora C2180](compiler-error-c2180.md)|wyrażenie kontrolne jest typu "*typu*"|
|[Błąd kompilatora C2181](compiler-error-c2181.md)|Niedozwolona instrukcja else bez pasującego if|
|[Błąd kompilatora C2182](compiler-error-c2182.md)|"*identyfikator*": niedozwolone użycie typu "void"|
|[Błąd kompilatora C2183](compiler-error-c2183.md)|Błąd składniowy: jednostka tłumaczeniowa jest pusta|
|[Błąd kompilatora C2184](compiler-error-c2184.md)|"*typu*": niedozwolony typ w wyrażeniu __except|
|[Błąd kompilatora C2185](compiler-error-c2185.md)|"*identyfikator*": niedozwolona Alokacja|
|[Błąd kompilatora C2186](compiler-error-c2186.md)|"*operator*": niedozwolony operand typu "void"|
|C2187 błąd kompilatora|Błąd składniowy: "*tokenu*' była Nieoczekiwana w tym miejscu|
|[Błąd kompilatora C2188](compiler-error-c2188.md)|"*numer*": zbyt duży dla znaku dwubajtowego|
|C2189 błąd kompilatora|Nie można zastosować atrybutu "alignas" do pola bitowego, parametru funkcji, deklaracji wyjątku lub zmiennej zadeklarowanej przy użyciu klasy magazynu "register"|
|[Błąd kompilatora C2190](compiler-error-c2190.md)|Pierwsza lista parametrów dłuższa niż druga|
|[Błąd kompilatora C2191](compiler-error-c2191.md)|druga lista parametrów dłuższa niż pierwsza|
|[Błąd kompilatora C2192](compiler-error-c2192.md)|Parametr "*numer*" deklaracji różni się|
|[Błąd kompilatora C2193](compiler-error-c2193.md)|"*identyfikator*": już w segmencie|
|[Błąd kompilatora C2194](compiler-error-c2194.md)|"*identyfikator*": jest segmentem tekstu|
|[Błąd kompilatora C2195](compiler-error-c2195.md)|"*identyfikator*": jest segmentem danych|
|[Błąd kompilatora C2196](compiler-error-c2196.md)|wartość Case "*wartość*" już użyta|
|[Błąd kompilatora C2197](compiler-error-c2197.md)|"*funkcja*": zbyt wiele argumentów dla wywołania|
|[Błąd kompilatora C2198](compiler-error-c2198.md)|"*funkcja*": zbyt mało argumentów dla wywołania|
|[Błąd kompilatora C2199](compiler-error-c2199.md)|Błąd składniowy: znaleziono "*identyfikator* (" w zakresie globalnym (była deklaracja jest zamierzona?)|