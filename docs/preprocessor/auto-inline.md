---
title: auto_inline
ms.date: 11/04/2016
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: a3e49941271ec294ddb69861d12e3451332770fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633350"
---
# <a name="autoinline"></a>auto_inline
Nie obejmuje wszystkie funkcje zdefiniowane w zakresie gdzie **poza** jest określony jako jako kandydatów do automatycznego rozwinięcia funkcji wbudowanej.

## <a name="syntax"></a>Składnia

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>Uwagi

Aby użyć **auto_inline** pragma, umieść go przed i natychmiast po (nie w) definicji funkcji. Pragmy staje się skuteczny w pierwszej definicji funkcji po pragmy jest widoczny.

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)