---
title: Tworzenie tekstu pliku wbudowanego
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: 4989d0757e893a7bc4b0a0e8937afee18719aa4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523116"
---
# <a name="creating-inline-file-text"></a>Tworzenie tekstu pliku wbudowanego

Pliki wbudowane są tymczasowy lub stały.

## <a name="syntax"></a>Składnia

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Uwagi

Określ *inlinetext* w pierwszym wierszu po poleceniu. Oznacz kończyć podwójne nawiasy (<<) na początku w osobnym wierszu. Ten plik zawiera wszystkie *inlinetext* przed ograniczająca nawiasy kwadratowe. *Inlinetext* może mieć rozszerzenia — makro i podstawienia, ale nie dyrektywy lub komentarze pliku reguł programu make. Miejsca do magazynowania, karty i znaki nowego wiersza są traktowane dosłownie.

Plik tymczasowy istnieje w czasie trwania sesji i mogą być ponownie używane przez inne polecenia. Określ **zachować** po kątem zamykających nawiasów kwadratowych do przechowywania pliku po sesji NMAKE; bez nazwy pliku jest zachowywany na dysku wraz ze wygenerowanej nazwy pliku. Określ **NOKEEP** lub Brak pliku tymczasowego. **Zachowaj** i **NOKEEP** nie jest uwzględniana wielkość liter.

## <a name="see-also"></a>Zobacz też

[Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)