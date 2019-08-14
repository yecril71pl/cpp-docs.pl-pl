---
title: Dyrektywy przetwarzania wstępnego pliku reguł programu Make
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980512"
---
# <a name="makefile-preprocessing-directives"></a>Dyrektywy przetwarzania wstępnego pliku reguł programu Make

Dyrektywy przetwarzania wstępnego nie uwzględnia wielkości liter. Początkowy wykrzyknik (!) musi pojawić się na początku wiersza. Zero lub więcej spacji lub tabulatorów może pojawić się po znaku wykrzyknika, w przypadku wcięcia.

- `!CMDSWITCHES`{`+` &#124; opcja... `-`

   Włącza lub wyłącza każdą *opcję* . Spacje lub tabulatory muszą znajdować `-` się przed `+` operatorem or; Brak może pojawić się między operatorem a literami [opcji](running-nmake.md#nmake-options). W literach nie jest rozróżniana wielkość liter i są one`/`określone bez ukośnika (). Aby włączyć niektóre opcje i wyłączyć inne, użyj oddzielnych specyfikacji `!CMDSWITCHES`.

   W pliku reguł programu make można używać tylko opcji/D,/I,/N i/S. W pliku Tools. ini wszystkie opcje są dozwolone z wyjątkiem/F,/HELP,/NOLOGO,/X i/?. Zmiany określone w bloku opisu nie zaczną obowiązywać do następnego bloku opisu. Ta dyrektywa aktualizuje **MAKEFLAGS**; zmiany są dziedziczone podczas rekursji, jeśli określono **MAKEFLAGS** .

- `!ERROR`*tekst*

   Wyświetla *tekst* w U1050 błędu, a następnie zatrzymuje NMAKE, nawet w przypadku, gdy jest `.IGNORE`używany `!CMDSWITCHES`modyfikator poleceń/k,/i`-`,, lub pauzy (). Spacje lub tabulatory przed *tekstem* zostanie zignorowane.

- `!MESSAGE`*tekst*

   Wyświetla *tekst* na standardowym wyjściu. Spacje lub tabulatory przed *tekstem* zostanie zignorowane.

- `!INCLUDE`[ `<` ] *filename* [ `>` ]

   Odczytuje *nazwę pliku* jako plik reguł programu make, a następnie kontynuuje pracę z bieżącym programem Make. NMAKE wyszukuje *nazwy pliku* najpierw w określonym lub bieżącym katalogu, a następnie rekursywnie za pomocą katalogów wszelkich nadrzędnych plików reguł programu make, a następnie, jeśli filename`< >`jest ujęty w nawiasy kątowe (), w katalogach określonych przez  **Dołącz** makro, które początkowo jest ustawione na zmienną środowiskową INCLUDE. Przydatne do przekazywania `.SUFFIXES` ustawień, `.PRECIOUS`i reguł wnioskowania do cyklicznych plików reguł programu make.

- `!IF`*constant_expression*

   Przetwarza instrukcje między `!IF` i Next `!ELSE` lub `!ENDIF` if *constant_expression* oblicza wartość różną od zera.

- `!IFDEF`Nr *makra*

   Przetwarza instrukcje między `!IFDEF` i następnym `!ELSE` lub `!ENDIF` Jeśli *makroname* jest zdefiniowane. Makro o wartości null jest uznawane za zdefiniowane.

- `!IFNDEF`Nr *makra*

   Przetwarza instrukcje między `!IFNDEF` i dalej `!ELSE` lub `!ENDIF` Jeśli *makroname* nie jest zdefiniowane.

- `!ELSE`[`IF` &#124; &#124; constant_expression Macroname`IFDEF` ] `IFNDEF`

   Przetwarza instrukcje między `!ELSE` i dalej `!ENDIF` , jeśli instrukcja poprzedzająca `!IFDEF` `!IF`,, `!IFNDEF` lub została oceniona jako zero. Opcjonalne słowa kluczowe zapewniają następną kontrolę nad przetwarzaniem wstępnie.

- `!ELSEIF`

   Synonimu dla `!ELSE IF`.

- `!ELSEIFDEF`

   Synonimu dla `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonimu dla `!ELSE IFNDEF`.

- `!ENDIF`

   Oznacza koniec elementu `!IF`, `!IFDEF`, lub `!IFNDEF` . Dowolny tekst po `!ENDIF` tym samym wierszu jest ignorowany.

- `!UNDEF`Nr *makra*

   Dedefiniowanie *makraname*.

## <a name="see-also"></a>Zobacz także

- [Przetwarzanie wstępne pliku reguł programu Make](makefile-preprocessing.md)