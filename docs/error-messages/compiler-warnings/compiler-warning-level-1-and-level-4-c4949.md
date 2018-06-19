---
title: Kompilator C4949 ostrzegawcze (poziom 1 i 4) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dbf80f85db7334d4bcb46402851cac601d258f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279649"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Kompilator C4949 ostrzegawcze (poziom 1 i 4)
dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"  
  
 Kompilator ignoruje [zarządzane](../../preprocessor/managed-unmanaged.md) i niezarządzanych pragm, jeśli kod źródłowy nie jest skompilowana przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). To ostrzeżenie ma charakter informacyjny.  
  
 Poniższy przykład generuje C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 Gdy **#pragma niezarządzanych** jest używana bez **/CLR**, C4949 to ostrzeżenie poziom 4.  
  
 Poniższy przykład generuje C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```