---
title: C3886 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3886
dev_langs:
- C++
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e17e56ac999680728f14d0ea3a98cc7c05b66e31
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268380"
---
# <a name="compiler-error-c3886"></a>C3886 błąd kompilatora
"var": literał elementu członkowskiego danych musi zostać zainicjowany  
  
 A [literału](../../windows/literal-cpp-component-extensions.md) po declaraed można zainicjować zmiennej.  
  
 Poniższy przykład generuje C3886:  
  
```  
// C3886.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal int staticConst;   // C3886  
   literal int staticConst2 = 0;   // OK  
};  
```