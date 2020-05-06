---
title: Stałe znakowe języka C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326303"
---
# <a name="c-character-constants"></a>Stałe znakowe języka C

"Stała znakowa" jest tworzona przez zawrzeć pojedynczy znak z zestawu znaków do zaprezentowania w pojedynczym cudzysłowie (**""**). Stałe znakowe służą do reprezentowania znaków w [zestawie znaków wykonania](../c-language/execution-character-set.md).

## <a name="syntax"></a>Składnia

*znak — stała*: **"** *c-char-Sequence* **"**

**L "** *c-char-Sequence* **"**

*c-char-Sequence*: *c-char*

*c-char-Sequence c-char*

*c-char*: każdy element członkowski zestawu znaków źródłowych z wyjątkiem pojedynczego cudzysłowu (**'**), ukośnika odwrotnego**\\**() lub znaku nowego wiersza

*Sekwencja ucieczki*

*Escape — sekwencja*: *Simple-Escape-Sequence*

*ósemkowe — sekwencja ucieczki*

*szesnastkowe — sekwencja ucieczki*

*prosta — sekwencja ucieczki*: jedno z **\a \b/\n/lt \t \v**

**\\' \\" \\\ \\?**

*ósemkowe — sekwencja ucieczki*: **\\** *ósemkowa cyfra*  

**\\**  *ósemkowa cyfra ósemkowa*

**\\**  *ósemkowa cyfra ósemkowa cyfra ósemkowa*

*szesnastkowe-Escape-Sequence*: **\x**  *szesnastkowe-cyfra*

*szesnastkowe — Ucieczka — sekwencja szesnastkowa*

## <a name="see-also"></a>Zobacz też

[Stałe języka C](../c-language/c-constants.md)
