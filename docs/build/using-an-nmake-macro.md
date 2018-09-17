---
title: Korzystanie z makro NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b68a5f3128b5d3780895f8080411819ed9b538
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712598"
---
# <a name="using-an-nmake-macro"></a>Korzystanie z makro NMAKE

Aby użyć makra, należy ująć jego nazwę w nawiasach poprzedzone znakiem dolara ($) w następujący sposób.

## <a name="syntax"></a>Składnia

```
$(macroname)
```

## <a name="remarks"></a>Uwagi

Żadne spacje są dozwolone. Nawiasy są opcjonalne Jeśli *makra* jest pojedynczy znak. Ciąg definicji zastępuje $(*makra*); niezdefiniowane makro zastępuje pusty ciąg.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Podstawianie makr](../build/macro-substitution.md)

## <a name="see-also"></a>Zobacz też

[Makra i NMAKE](../build/macros-and-nmake.md)