---
title: Stałe znakowe języka C
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 684763b5ce3983b6efc44db9499c139c84f6e3aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507197"
---
# <a name="c-character-constants"></a>Stałe znakowe języka C

"Stałej znakowej" został utworzony, umieszczając pojedynczy znak z zestawu w pojedynczy cudzysłów znaków reprezentowanych (**""**). Stałe znaków są używane do reprezentowania znaków w [zestaw znaków wykonania](../c-language/execution-character-set.md).

## <a name="syntax"></a>Składnia

*stałej znakowej*: **"** *c char sekwencji* **"**

**L "** *c char sekwencji* **"**

*c char sekwencji*: *c-char*

*c char sekwencji c-char*

*c-char*: każdy członek znak źródłowy zestawu z wyjątkiem pojedynczego cudzysłowu (**"**), ukośnika odwrotnego (**\\**), lub znak nowego wiersza

*Sekwencja unikowa*

*Sekwencja unikowa*: *sekwencji unikowej prosty*

*ósemkowa sekwencja unikowa*

*szesnastkowe sekwencje*

*proste sekwencje*: jeden z **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*ósemkowa sekwencja unikowa*: **\\** *cyfrą ósemkową*

**\\**  *cyfrą ósemkową cyfrą ósemkową*

**\\**  *cyfrą ósemkową cyfrą ósemkową cyfrą systemu ósemkowego*

*szesnastkowe sekwencje*: **\x***cyfry szesnastkowe*

*szesnastkowe sekwencje szesnastkowe cyfrowy*

## <a name="see-also"></a>Zobacz też

[Stałe języka C](../c-language/c-constants.md)