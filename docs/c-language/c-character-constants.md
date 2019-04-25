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

"Stałej znakowej" został utworzony, umieszczając pojedynczy znak z zestawu w pojedynczy cudzysłów znaków reprezentowanych (**""**). Stałe znaków są używane do reprezentowania znaków w [zestaw znaków wykonania](../c-language/execution-character-set.md).

## <a name="syntax"></a>Składnia

*stałej znakowej*: **"** *c char sekwencji* **"**

**L "** *c char sekwencji* **"**

*c char sekwencji*: *c-char*

*c char sekwencji c-char*

*c-char*: Każdy członek znak źródłowy zestawu z wyjątkiem pojedynczego cudzysłowu (**"**), ukośnika odwrotnego (**\\**), lub znak nowego wiersza

*escape-sequence*

*Sekwencja unikowa*: *sekwencji unikowej prosty*

*octal-escape-sequence*

*hexadecimal-escape-sequence*

*proste sekwencje*: jeden z **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*ósemkowa sekwencja unikowa*: **\\** *cyfrą ósemkową*

**\\**  *cyfrą ósemkową cyfrą ósemkową*

**\\**  *cyfrą ósemkową cyfrą ósemkową cyfrą systemu ósemkowego*

*szesnastkowe sekwencje*: **\x** *cyfry szesnastkowe*

*hexadecimal-escape-sequence hexadecimal-digit*

## <a name="see-also"></a>Zobacz także

[Stałe języka C](../c-language/c-constants.md)
