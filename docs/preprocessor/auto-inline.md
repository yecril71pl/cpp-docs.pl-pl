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
ms.openlocfilehash: de012a31fe68c68d4e64df2d3fa10b44d9112735
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="autoinline"></a>auto_inline
Nie obejmuje wszystkie funkcje zdefiniowane w zakresie gdzie **poza** jest określony jako jako kandydatów do automatycznego rozwinięcia funkcji wbudowanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma auto_inline( [{on | off}] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć **auto_inline** pragma, umieść go przed i natychmiast po (nie w) definicji funkcji. Pragma działa na pierwszym definicji funkcji po pragma jest widoczna.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)