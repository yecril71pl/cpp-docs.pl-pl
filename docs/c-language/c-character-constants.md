---
title: Stałe znakowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9908bfd8be662a53727e9c833626f329dd45c04
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038584"
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