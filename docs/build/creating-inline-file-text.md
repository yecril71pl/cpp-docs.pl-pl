---
title: Tworzenie tekstu pliku wbudowanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce0a345c6c2f48d3d5c2e6fb9d9cfc2a5c03e4ed
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720920"
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