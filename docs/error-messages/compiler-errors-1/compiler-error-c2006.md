---
title: "C2006 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2006
dev_langs: C++
helpviewer_keywords: C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8d182e7a98d01dee4047defa5adb5ccc2dc7cde5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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