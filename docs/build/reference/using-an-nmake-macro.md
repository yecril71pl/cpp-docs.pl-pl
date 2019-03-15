---
title: Korzystanie z makro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823820"
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

[Podstawianie makr](macro-substitution.md)

## <a name="see-also"></a>Zobacz także

[Makra i NMAKE](macros-and-nmake.md)
