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
ms.openlocfilehash: c59dcc8ec7749a91565d5af043b1bd9e9eaa16ea
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033167"
---
# <a name="autoinline"></a>auto_inline
Nie obejmuje wszystkie funkcje zdefiniowane w zakresie gdzie **poza** jest określony jako jako kandydatów do automatycznego rozwinięcia funkcji wbudowanej.

## <a name="syntax"></a>Składnia

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>Uwagi

Aby użyć **auto_inline** pragma, umieść go przed i natychmiast po (nie w) definicji funkcji. Pragmy staje się skuteczny w pierwszej definicji funkcji po pragmy jest widoczny.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)