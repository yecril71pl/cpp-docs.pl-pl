---
title: auto_inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc2fb4cb870ff1dca2f0b55e9aad20741ffb8220
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083181"
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