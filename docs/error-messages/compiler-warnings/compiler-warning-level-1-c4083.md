---
title: Kompilatora (poziom 1) ostrzeżenie C4083 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4083
dev_langs:
- C++
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0d0d7baa0e521484841c638cef4332001a65e78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277683"
---
# <a name="compiler-warning-level-1-c4083"></a>Kompilator C4083 ostrzegawcze (poziom 1)
Oczekiwano 'token'; Znaleziono identyfikator 'Identyfikator'  
  
 Identyfikator występuje w niewłaściwym miejscu w **#pragma** instrukcji.  
  
## <a name="example"></a>Przykład  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 Sprawdź składnię [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) dyrektywy.