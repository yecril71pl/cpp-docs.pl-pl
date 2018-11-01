---
title: Korzystanie z makro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: 9d8ff76e1e730b65db363749797ef9ae2062adab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645084"
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