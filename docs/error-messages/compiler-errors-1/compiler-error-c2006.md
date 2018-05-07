---
title: C2006 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93880e7d767de3101cd7a292af5fa2874cae86bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2006"></a>C2006 błąd kompilatora
"dyrektywy" Oczekiwano nazwy pliku, znaleziono "token"  
  
 Dyrektywy, takich jak [#include](../../preprocessor/hash-include-directive-c-cpp.md) lub [#import](../../preprocessor/hash-import-directive-cpp.md) wymaga nazwy pliku. Aby rozwiązać problem, upewnij się, *tokenu* jest prawidłową nazwą pliku. Ponadto umieść nazwę pliku w podwójne cudzysłowy lub nawiasy.  
  
 Poniższy przykład generuje C2006:  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```