---
title: "Dyrektywy przetwarzania wstępnego pliku makefile | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1bc73a86b0772b13731aaf7ac4e2ef0760caa8a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="makefile-preprocessing-directives"></a>Dyrektywy przetwarzania wstępnego pliku reguł programu Make
Dyrektywy przetwarzania wstępnego nie jest uwzględniana wielkość liter. Początkowa wykrzyknika (!) musi znajdować się na początku wiersza. Zero lub więcej spacji ani karty mogą być wyświetlane po wykrzyknika dla wcięcia.  
  
 **! CMDSWITCHES**  
 {**+**&#124;  **-** }*opcji*... Włącza każdego *opcji* wymienione lub wyłączyć. Spacji ani karty musi występować przed + lub - operator; Brak może wystąpić między operatora i [opcję litery](../build/nmake-options.md). Liter nie jest uwzględniana wielkość liter i zostały określone bez ukośnika (/). Aby włączyć niektóre opcje na i inne off, użyj oddzielnych specyfikacji **! CMDSWITCHES**.  
  
 Tylko /D / I, /N i /S może być używana w pliku reguł programu make. W Tools.ini, wszystkie opcje są dozwolone z wyjątkiem /F, / Help, / nologo, / X, a /?. Określony w bloku opis zmian uwzględnione po następnym bloku opis. Ta dyrektywa aktualizuje **MAKEFLAGS**; zmiany są dziedziczone podczas rekursji, jeśli **MAKEFLAGS** jest określona.  
  
 **! Błąd***tekstu*   
 Wyświetla *tekst* w błąd U1050, a następnie zatrzymanie NMAKE, nawet jeśli /K, / I **. Ignoruj**, **! CMDSWITCHES**, lub służy polecenie modyfikator kreski (-). Spacji ani tabulatorów przed *tekst* są ignorowane.  
  
 **! KOMUNIKAT***tekstu*   
 Wyświetla *tekst* do wyjścia standardowego. Spacji ani tabulatorów przed *tekst* są ignorowane.  
  
 **! OBEJMUJĄ**[  **\<** ] *filename*[  **>** ]  
 Odczytuje *filename* jako pliku reguł programu make, następnie jest kontynuowana z bieżącego pliku reguł programu make. Wyszukuje NMAKE *filename* najpierw w określonym katalogu lub bieżącego, następnie rekursywnie za pośrednictwem katalogów dowolnego nadrzędnego pliki reguł programu make, następnie, jeśli *filename* jest ujęta w nawiasy (\<>), w katalogach określonych przez **INCLUDE** makra, która jest początkowo ustawiona zmiennej środowiskowej INCLUDE. Przydatne do przekazania **. SUFIKSY** ustawienia **. CENNY**oraz reguły wnioskowania cyklicznego pliki reguł programu make.  
  
 **! JEŚLI**  `constantexpression`  
 Przetwarza instrukcje między **! Jeśli** Następna **! ELSE** lub `!ENDIF` Jeśli `constantexpression` ma wartość różną od zera.  
  
 **! IFDEF***makra*   
 Przetwarza instrukcje między `!IFDEF` Następna **! ELSE** lub `!ENDIF` Jeśli *makra* jest zdefiniowany. Null — makro jest uznawany za ma zostać zdefiniowana.  
  
 **! IFNDEF***makra*   
 Przetwarza instrukcje między **! IFNDEF** Następna **! ELSE** lub `!ENDIF` Jeśli *makra* nie jest zdefiniowany.  
  
 **! ELSE**[**IF** *constantexpression* &#124; **IFDEF** *makra*&#124; **IFNDEF** *makra*]  
 Przetwarza instrukcje między **! ELSE** Następna `!ENDIF` Jeśli wcześniej **! Jeśli**, `!IFDEF`, lub **! IFNDEF** instrukcji obliczoną wartością zero. Opcjonalne słowa kluczowe podać kontroli przetwarzania wstępnego.  
  
 **! ELSEIF**  
 Synonim **! ELSE IF**.  
  
 **! ELSEIFDEF —**  
 Synonim **! ELSE IFDEF**.  
  
 **! ELSEIFNDEF —**  
 Synonim **! ELSE IFNDEF**.  
  
 `!ENDIF`  
 Oznacza koniec **! Jeśli**, `!IFDEF`, lub **! IFNDEF** bloku. Tekst po `!ENDIF` jest ignorowane w tym samym wierszu.  
  
 **! UNDEF***makra*   
 Anulowanie definicji *makra*.  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzanie wstępne pliku reguł programu Make](../build/makefile-preprocessing.md)