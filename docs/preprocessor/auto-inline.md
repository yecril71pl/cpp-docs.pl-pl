---
title: auto_inline | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs: C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46a1ca697e12a5abe9745a558abf20b73fef8184
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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