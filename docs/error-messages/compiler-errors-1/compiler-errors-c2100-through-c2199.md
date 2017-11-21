---
title: "Błędy kompilatora — od C2100 c2199 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
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
dev_langs: C++
ms.assetid: 1ccab076-0954-4386-b959-d3112a6793ae
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f03dc203c34e5389eb153288ccdc92e77473686
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-errors-c2100-through-c2199"></a>Błędy kompilatora — od C2100 do C2199
Artykuły w tej części dokumentacji zawierają informacje o podsekcji błędów kompilatora Visual C++. Można uzyskać dostępu do informacji w tym miejscu lub w **dane wyjściowe** okna w programie Visual Studio, możesz wybrać numer błędu, a następnie wybierz pozycję klawisz F1.  
  
> [!NOTE]
>  Nie każdy [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] błędu jest opisane w witrynie MSDN. W wielu przypadkach diagnostycznych komunikat zawiera wszystkie informacje, które są dostępne. Jeśli uważasz, że komunikat o błędzie musi dodatkowe informacje, można Daj nam znać. Można Użyj formularza opinii na tej stronie, lub przejdź do paska menu w programie Visual Studio i wybierz **pomocy**, **zgłosić usterkę**, lub można przesłać raportu sugestię lub usterki na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Błędy i ostrzeżenia na forach MSDN publicznego może się okazać dodatkowej pomocy. [Języka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) forum jest pytania i dyskusji o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] składni języka i kompilatora. [Visual C++ ogólne](http://go.microsoft.com/fwlink/?LinkId=158194) forum jest odpowiedzi na pytania dotyczące [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] nie opisano w innych forach. Można również znaleźć pomoc na temat błędów i ostrzeżeń w [przepełnienie stosu](http://stackoverflow.com/).  
  
|Błąd|Komunikat|  
|-----------|-------------|  
|[Błąd kompilatora — od C2100](compiler-error-c2100.md)|Niedozwolony element pośredni|  
|[C2101 błąd kompilatora](compiler-error-c2101.md)|"&" dla stałej|  
|[C2102 błąd kompilatora](compiler-error-c2102.md)|"&" wymaga wartości l|  
|[C2103 błąd kompilatora](compiler-error-c2103.md)|"&" zarejestrować zmiennej|  
|[C2104 błąd kompilatora](compiler-error-c2104.md)|"&" na pole bitowe ignorowane|  
|[C2105 błąd kompilatora](compiler-error-c2105.md)|"*operator*" wymaga wartości l|  
|[C2106 błąd kompilatora](compiler-error-c2106.md)|"*operator*": lewy operand musi być l-value|  
|[C2107 błąd kompilatora](compiler-error-c2107.md)|Nieprawidłowy indeks, pośrednik niedozwolony|  
|[C2108 błąd kompilatora](compiler-error-c2108.md)|Indeks dolny nie jest typu całkowitego|  
|[C2109 błąd kompilatora](compiler-error-c2109.md)|Indeks dolny wymaga tablicy lub wskaźnika typu|  
|[C2110 błąd kompilatora](compiler-error-c2110.md)|"+": nie można dodać dwóch wskaźników|  
|[C2111 błąd kompilatora](compiler-error-c2111.md)|"+": Dodawanie wskaźników wymaga całkowitego operandu|  
|[C2112 błąd kompilatora](compiler-error-c2112.md)|"-": wskaźnik odejmowania wymaga wartości całkowitej lub wskaźnika operandu|  
|[C2113 błąd kompilatora](compiler-error-c2113.md)|"-": wskaźnik może zostać odjęty tylko od innego wskaźnika|  
|[C2114 błąd kompilatora](compiler-error-c2114.md)|"*operator*": wskaźnik po lewej stronie; wymaga całkowitej wartości po prawej stronie|  
|[C2115 błąd kompilatora](compiler-error-c2115.md)|"*operator*": niezgodne typy|  
|[C2116 błąd kompilatora](compiler-error-c2116.md)|listy parametrów funkcji różnią się|  
|[C2117 błąd kompilatora](compiler-error-c2117.md)|"*identyfikator*": przepełnienie granic tablicy|  
|[C2118 błąd kompilatora](compiler-error-c2118.md)|Indeks dolny ujemna|  
|C2119 błąd kompilatora|"*identyfikator*": typ dla "*typu*" nie można wywnioskować na podstawie pustego inicjalizatora|  
|[C2120 błąd kompilatora](compiler-error-c2120.md)|"void" niedozwolone ze wszystkimi typami|  
|[C2121 błąd kompilatora](compiler-error-c2121.md)|"#": nieprawidłowy znak: prawdopodobnie wynik rozwinięcia makra|  
|[C2122 błąd kompilatora](compiler-error-c2122.md)|"*identyfikator*": parametr prototypu w liście nazw jest niedozwolony|  
|C2123 błąd kompilatora|"*identyfikator*": szablony alias nie może być jawnie lub częściowo specjalizowany|  
|[C2124 błąd kompilatora](compiler-error-c2124.md)|Dzielenie lub dzielenie modulo przez zero|  
|C2125 błąd kompilatora|"constexpr" jest niezgodny z "*tokenu*"|  
|C2126 błąd kompilatora|"*identyfikator*" nie można zadeklarować ze specyfikatorem "constexpr"|  
|C2127 błąd kompilatora|"*identyfikator*": niedozwolone inicjowanie elementu "constexpr" jednostki o niestałe wyrażenie|  
|[C2128 błąd kompilatora](compiler-error-c2128.md)|"*funkcja*": alloc_text/same_seg dotyczy tylko funkcji z powiązaniem C|  
|[C2129 błąd kompilatora](compiler-error-c2129.md)|Funkcja statyczna "*identyfikator*" zadeklarowana ale niezdefiniowana|  
|[C2130 błąd kompilatora](compiler-error-c2130.md)|#line oczekiwany ciąg zawierający nazwę pliku, znaleziono "*tokenu*"|  
|C2131 błąd kompilatora|Wyrażenie nie zostało obliczone do stałej|  
|[C2132 błąd kompilatora](compiler-error-c2132.md)|Błąd składniowy: nieoczekiwany identyfikator|  
|[C2133 błąd kompilatora](compiler-error-c2133.md)|"*identyfikator*': nieznany rozmiar|  
|[C2134 błąd kompilatora](compiler-error-c2134.md)|"*funkcja*": nie powoduje wywołanie w wyrażeniu stałym|  
|[C2135 błąd kompilatora](compiler-error-c2135.md)|"*operator*": operacja na polu bitowym niedozwolony|  
|C2136 błąd kompilatora|niedozwolone kontrakt interfejsu API tworzenia|  
|[C2137 błąd kompilatora](compiler-error-c2137.md)|Stała znakowa pusty|  
|[C2138 błąd kompilatora](compiler-error-c2138.md)|niedozwolone jest zdefiniowanie wyliczenia bez elementów członkowskich|  
|[C2139 błąd kompilatora](compiler-error-c2139.md)|"*klasy*": Niezdefiniowana klasa nie jest dozwolona jako argument typu wewnętrznej cechy kompilatora "*cechy*"|  
|[C2140 błąd kompilatora](compiler-error-c2140.md)|"*typu*": typ, który jest zależny od parametru typu ogólnego nie jest dozwolona jako argument typu wewnętrznej cechy kompilatora "*cechy*"|  
|[C2141 błąd kompilatora](compiler-error-c2141.md)|przepełnienie rozmiar tablicy|  
|[C2142 błąd kompilatora](compiler-error-c2142.md)|deklaracje funkcji różnią się, parametry zmiennej określone tylko w jednej z nich|  
|[C2143 błąd kompilatora](compiler-error-c2143.md)|Błąd składniowy: brakuje "*token1*"before"*token2*"|  
|[C2144 błąd kompilatora](compiler-error-c2144.md)|Błąd składniowy: "*typu*"powinien być poprzedzony przez"*token2*"|  
|[C2145 błąd kompilatora](compiler-error-c2145.md)|Błąd składniowy: brakuje "*tokenu*" przed identyfikatorem|  
|[C2146 błąd kompilatora](compiler-error-c2146.md)|Błąd składniowy: brakuje "*tokenu*"przed identyfikatorem"*identyfikator*"|  
|[C2147 błąd kompilatora](compiler-error-c2147.md)|Błąd składniowy: "*tokenu*" jest nowym słowem kluczowym|  
|[C2148 błąd kompilatora](compiler-error-c2148.md)|Całkowity rozmiar tablicy nie może przekraczać 0 x*wartość* bajtów|  
|[C2149 błąd kompilatora](compiler-error-c2149.md)|"*identyfikator*": nazwane pole bitowe nie może mieć zerowej szerokości|  
|[C2150 błąd kompilatora](compiler-error-c2150.md)|"*identyfikator*": pole bitowe musi być typu "int", "signed int" lub "unsigned int"|  
|[C2151 błąd kompilatora](compiler-error-c2151.md)|więcej niż jeden atrybut językowy|  
|[C2152 błąd kompilatora](compiler-error-c2152.md)|"*identyfikator*": wskaźniki do funkcji z różnymi atrybutami|  
|[C2153 błąd kompilatora](compiler-error-c2153.md)|literały całkowite muszą mieć co najmniej jedną cyfrę|  
|[C2154 błąd kompilatora](compiler-error-c2154.md)|"*typu*": tylko typ wyliczeniowy jest dozwolony jako argument typu wewnętrznej cechy kompilatora "*cechy*"|  
|[C2155 błąd kompilatora](compiler-error-c2155.md)|"?": lewy operand nieprawidłowy, oczekiwano arytmetycznego lub typu wskaźnika|  
|[C2156 błąd kompilatora](compiler-error-c2156.md)|pragma musi znajdować się poza funkcją|  
|[C2157 błąd kompilatora](compiler-error-c2157.md)|"*identyfikator*": musi być zadeklarowana przed użyciem w liście pragma|  
|[C2158 błąd kompilatora](compiler-error-c2158.md)|"*typu*': dyrektywa #pragma make_public jest obecnie obsługiwany tylko w przypadku natywnych nieszablonowych typów|  
|[C2159 błąd kompilatora](compiler-error-c2159.md)|Określono więcej niż jednej klasy magazynu|  
|[C2160 błąd kompilatora](compiler-error-c2160.md)|"##" nie może występować na początku definicji makra|  
|[C2161 błąd kompilatora](compiler-error-c2161.md)|"##" nie może występować na końcu definicji makra|  
|[C2162 błąd kompilatora](compiler-error-c2162.md)|Oczekiwany parametr formalny makra|  
|[C2163 błąd kompilatora](compiler-error-c2163.md)|"*funkcja*": nie jest dostępna jako funkcja wewnętrzna|  
|[C2164 błąd kompilatora](compiler-error-c2164.md)|"*funkcja*": wewnętrzna funkcja nie jest zadeklarowana|  
|[C2165 błąd kompilatora](compiler-error-c2165.md)|"*modyfikator*": nie można modyfikować wskaźników do danych|  
|[C2166 błąd kompilatora](compiler-error-c2166.md)|wartość l Określa obiekt const|  
|[C2167 błąd kompilatora](compiler-error-c2167.md)|"*funkcja*": zbyt wiele parametrów rzeczywistych dla wewnętrznej funkcji|  
|[C2168 błąd kompilatora](compiler-error-c2168.md)|"*funkcja*": zbyt mało rzeczywistych parametrów w wewnętrznej funkcji|  
|[C2169 błąd kompilatora](compiler-error-c2169.md)|"*funkcja*": wewnętrzna funkcja nie może być zdefiniowana|  
|[C2170 błąd kompilatora](compiler-error-c2170.md)|"*identyfikator*": nie zadeklarowano jako funkcja, nie może być wewnętrzne|  
|[C2171 błąd kompilatora](compiler-error-c2171.md)|"*operator*": niedozwolone na operandach typu "*typu*"|  
|[C2172 błąd kompilatora](compiler-error-c2172.md)|"*funkcja*": rzeczywisty parametr nie jest wskaźnikiem: parametr *numer*|  
|[C2173 błąd kompilatora](compiler-error-c2173.md)|"*funkcja*": rzeczywisty parametr nie jest wskaźnikiem: parametr *numer*, lista parametrów *numer*|  
|[C2174 błąd kompilatora](compiler-error-c2174.md)|"*funkcja*": rzeczywisty parametr jest typu "void": parametr *numer*, lista parametrów *numer*|  
|[C2175 błąd kompilatora](compiler-error-c2175.md)|"*ustawień regionalnych*": nieprawidłowe ustawienia regionalne|  
|C2176 błąd kompilatora|instrukcja return nie może występować w procedurze obsługi funkcji bloku "try" skojarzonym z konstruktorem|  
|[C2177 błąd kompilatora](compiler-error-c2177.md)|stała jest za duży|  
|[C2178 błąd kompilatora](compiler-error-c2178.md)|"*identyfikator*"nie mogą być zadeklarowane z"*specyfikator*" Specyfikator|  
|[C2179 błąd kompilatora](compiler-error-c2179.md)|"*typu*": argument atrybutu nie może używać parametrów typu|  
|[C2180 błąd kompilatora](compiler-error-c2180.md)|wyrażenie kontrolne jest typu "*typu*"|  
|[C2181 błąd kompilatora](compiler-error-c2181.md)|Niedozwolona instrukcja else bez zgodnej instrukcji if|  
|[C2182 błąd kompilatora](compiler-error-c2182.md)|"*identyfikator*": niedozwolone użycie typu "void"|  
|[C2183 błąd kompilatora](compiler-error-c2183.md)|Błąd składniowy: jednostka tłumaczenia jest pusta|  
|[C2184 błąd kompilatora](compiler-error-c2184.md)|"*typu*": niedozwolony typ w wyrażeniu __except|  
|[C2185 błąd kompilatora](compiler-error-c2185.md)|"*identyfikator*": niedozwolona Alokacja|  
|[C2186 błąd kompilatora](compiler-error-c2186.md)|"*operator*": niedozwolony operand typu "void"|  
|C2187 błąd kompilatora|Błąd składniowy: "*tokenu*' była Nieoczekiwana w tym miejscu|  
|[C2188 błąd kompilatora](compiler-error-c2188.md)|"*numer*": zbyt duży dla znaku dwubajtowego|  
|C2189 błąd kompilatora|Nie można zastosować atrybutu "alignas" do pola bitowego, parametru funkcji, deklaracji wyjątku lub zmiennej zadeklarowanej przy użyciu klasy magazynu "register"|  
|[C2190 błąd kompilatora](compiler-error-c2190.md)|Pierwsza lista parametrów dłuższa niż druga|  
|[C2191 błąd kompilatora](compiler-error-c2191.md)|druga lista parametrów dłuższa niż pierwsza|  
|[C2192 błąd kompilatora](compiler-error-c2192.md)|Parametr "*numer*" innej deklaracji|  
|[C2193 błąd kompilatora](compiler-error-c2193.md)|"*identyfikator*": już w segmencie|  
|[C2194 błąd kompilatora](compiler-error-c2194.md)|"*identyfikator*": jest segmentem tekstu|  
|[C2195 błąd kompilatora](compiler-error-c2195.md)|"*identyfikator*": jest segmentem danych|  
|[C2196 błąd kompilatora](compiler-error-c2196.md)|przypadek wartość "*wartość*" już używana|  
|[C2197 błąd kompilatora](compiler-error-c2197.md)|"*funkcja*": za dużo argumentów dla wywołania|  
|[C2198 błąd kompilatora](compiler-error-c2198.md)|"*funkcja*": zbyt mało argumentów dla wywołania|  
|[Do C2199 błąd kompilatora](compiler-error-c2199.md)|Błąd składniowy: znaleziono "*identyfikator* (" w zakresie globalnym (czy deklaracja jest zamierzona?)|  