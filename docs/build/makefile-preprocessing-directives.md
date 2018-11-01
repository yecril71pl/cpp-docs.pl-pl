---
title: Dyrektywy przetwarzania wstępnego pliku reguł programu Make
ms.date: 06/14/2018
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
ms.openlocfilehash: adc81e5c4ea3d0d4a80e7efad4eaab15a5048cd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593573"
---
# <a name="makefile-preprocessing-directives"></a>Dyrektywy przetwarzania wstępnego pliku reguł programu Make

Dyrektywy przetwarzania wstępnego nie jest uwzględniana wielkość liter. Pierwszy punkt wykrzyknika (!) musi znajdować się na początku wiersza. Zero lub więcej znaków tabulacji lub spacji, może następować po elemencie wykrzyknika dla wcięcia.

- **! CMDSWITCHES** {**+** &#124; **-**}*opcji* ...

   Włącza każdego *opcji* wymienione lub wyłączyć. Spacje lub tabulatory musi występować przed + lub - operatora; Brak mogą występować między operatora i [opcji litery](../build/nmake-options.md). Liter nie jest uwzględniana wielkość liter i są określone bez ukośnika (/). Aby wyłączyć niektórych opcjami na i innych wyłączone, należy użyć oddzielnych specyfikacji **! CMDSWITCHES**.

   Tylko /D / po, /N i /S mogą być używane w pliku reguł programu make. W Tools.ini, wszystkie opcje są dozwolone z wyjątkiem /F, / Help, / nologo, / X, a /?. Zmiany określony w bloku opis wprowadzone do czasu kolejnego bloku opisu. Ta dyrektywa aktualizuje **MAKEFLAGS**; zmiany są dziedziczone podczas rekursji, jeśli **MAKEFLAGS** jest określony.

- **! Błąd***tekstu* 

   Wyświetla *tekstu* w błąd U1050, a następnie zostanie zatrzymana NMAKE, nawet wtedy, gdy /K, / I **. Ignoruj**, **! CMDSWITCHES**, lub jest używany modyfikator polecenia kreski (-). Spacje lub tabulatory przed *tekstu* są ignorowane.

- **! KOMUNIKAT***tekstu* 

   Wyświetla *tekst* do wyjścia standardowego. Spacje lub tabulatory przed *tekstu* są ignorowane.

- **! OBEJMUJĄ** [ **\<** ] *filename* [ **>** ]

   Odczytuje *filename* jako pliku reguł programu make, następnie będzie kontynuowane przy użyciu bieżącego pliku reguł programu make. Wyszukuje NMAKE *filename* najpierw w określonej lub bieżącego katalogu następnie rekursywnie między katalogami wszelkich nadrzędnych pliki reguł programu make, następnie Jeśli *filename* jest ujęta w nawiasy (\<>), w katalogach określonych przez **INCLUDE** makra, która jest początkowo ustawiona zmienna środowiskowa INCLUDE. Przydatne do przekazania **. SUFIKSY** ustawień **. CENNEGO**i reguły wnioskowania cykliczne pliki reguł programu make.

- **! Jeśli** *constant_expression*

   Przetwarza instrukcje między **! Jeśli** , a następnie **! ELSE** lub **! ENDIF** Jeśli *constant_expression* ma wartość różną od zera.

- **! IFDEF***makra* 

   Przetwarza instrukcje między **! IFDEF** , a następnie **! ELSE** lub **! ENDIF** Jeśli *makra* jest zdefiniowana. Null — makro jest uważany za można zdefiniować.

- **! IFNDEF***makra* 

   Przetwarza instrukcje między **! IFNDEF** , a następnie **! ELSE** lub **! ENDIF** Jeśli *makra* nie został zdefiniowany.

- **! ELSE** [**IF** *constant_expression* &#124; **IFDEF** *makra* &#124; **IFNDEF**  *makra*]

   Przetwarza instrukcje między **! ELSE** , a następnie **! ENDIF** Jeśli wcześniej **! Jeśli**, **! IFDEF**, lub **! IFNDEF** instrukcji obliczone na wartość zero. Opcjonalne słowa kluczowe podać kontrolę nad przetwarzania wstępnego.

- **! ELSEIF**

   Synonim dla **! Jeśli nie**.

- **! ELSEIFDEF**

   Synonim dla **! ELSE IFDEF**.

- **! ELSEIFNDEF**

   Synonim dla **! ELSE IFNDEF**.

- **! ENDIF**

   Oznacza koniec **! Jeśli**, **! IFDEF**, lub **! IFNDEF** bloku. Dowolny tekst po **! ENDIF** jest ignorowane w tym samym wierszu.

- **! UNDEF***makra* 

   Jedno anulowanie definicji *makra*.

## <a name="see-also"></a>Zobacz także

- [Przetwarzanie wstępne pliku reguł programu Make](../build/makefile-preprocessing.md)