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
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170491"
---
# <a name="makefile-preprocessing-directives"></a>Dyrektywy przetwarzania wstępnego pliku reguł programu Make

Dyrektywy przetwarzania wstępnego nie uwzględnia wielkości liter. Początkowy wykrzyknik (!) musi pojawić się na początku wiersza. Zero lub więcej spacji lub tabulatorów może pojawić się po znaku wykrzyknika, w przypadku wcięcia.

- `!CMDSWITCHES` {`+` &#124; `-`} —*opcja* ...

   Włącza lub wyłącza każdą *opcję* . Spacje lub tabulatory muszą znajdować się przed operatorem `+` lub `-`; między operatorem a [literami opcji](running-nmake.md#nmake-options)nie mogą występować żadne znaki. W literach nie jest rozróżniana wielkość liter i są one określone bez ukośnika (`/`). Aby włączyć niektóre opcje i wyłączyć inne, użyj oddzielnych specyfikacji `!CMDSWITCHES`.

   W pliku reguł programu make można używać tylko opcji/D,/I,/N i/S. W pliku Tools. ini wszystkie opcje są dozwolone z wyjątkiem/F,/HELP,/NOLOGO,/X i/?. Zmiany określone w bloku opisu nie zaczną obowiązywać do następnego bloku opisu. Ta dyrektywa aktualizuje **MAKEFLAGS**; zmiany są dziedziczone podczas rekursji, jeśli określono **MAKEFLAGS** .

- `!ERROR` *tekst*

   Wyświetla *tekst* w U1050 błędu, a następnie zatrzymuje NMAKE, nawet jeśli jest używany modyfikator poleceń/K,/i, `.IGNORE`, `!CMDSWITCHES`lub kreski (`-`). Spacje lub tabulatory przed *tekstem* zostanie zignorowane.

- `!MESSAGE` *tekst*

   Wyświetla *tekst* na standardowym wyjściu. Spacje lub tabulatory przed *tekstem* zostanie zignorowane.

- `!INCLUDE` [`<`] *filename* [`>`]

   Odczytuje *nazwę pliku* jako plik reguł programu make, a następnie kontynuuje pracę z bieżącym programem Make. NMAKE wyszukuje *nazwy pliku* najpierw w określonym lub bieżącym katalogu, a następnie rekursywnie za pomocą katalogów wszelkich nadrzędnych plików reguł programu make, a następnie, jeśli *filename* jest ujęty w nawiasy kątowe (`< >`), w katalogach określonych przez makro **include** , które początkowo jest ustawiona na zmienna środowiskowa include. Przydatne do przekazywania `.SUFFIXES` ustawień, `.PRECIOUS`i reguł wnioskowania do cyklicznych plików reguł programu make.

- `!IF` *constant_expression*

   Przetwarza instrukcje między `!IF` a następnym `!ELSE` lub `!ENDIF`, jeśli *constant_expression* ma wartość różną od zera.

- `!IFDEF` *Macroname*

   Przetwarza instrukcje między `!IFDEF` a następnym `!ELSE` lub `!ENDIF`, jeśli określono wartość *Macroname* . Makro o wartości null jest uznawane za zdefiniowane.

- `!IFNDEF` *Macroname*

   Przetwarza instrukcje między `!IFNDEF` a następnym `!ELSE` lub `!ENDIF`, jeśli *makroname* nie jest zdefiniowane.

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *Macroname* &#124; `IFNDEF` *Macroname*]

   Przetwarza instrukcje między `!ELSE` a następnym `!ENDIF`, jeśli wcześniejsza instrukcja `!IF`, `!IFDEF`lub `!IFNDEF` została oceniona jako zero. Opcjonalne słowa kluczowe zapewniają następną kontrolę nad przetwarzaniem wstępnie.

- `!ELSEIF`

   Synonimu dla `!ELSE IF`.

- `!ELSEIFDEF`

   Synonimu dla `!ELSE IFDEF`.

- `!ELSEIFNDEF`

   Synonimu dla `!ELSE IFNDEF`.

- `!ENDIF`

   Oznacza koniec bloku `!IF`, `!IFDEF`lub `!IFNDEF`. Dowolny tekst po `!ENDIF` w tym samym wierszu jest ignorowany.

- `!UNDEF` *Macroname*

   Dedefiniowanie *makraname*.

## <a name="see-also"></a>Zobacz też

- [Przetwarzanie wstępne pliku reguł programu Make](makefile-preprocessing.md)
