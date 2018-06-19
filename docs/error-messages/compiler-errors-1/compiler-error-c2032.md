---
title: C2032 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1db268222f3b9f7ca6f9ce297680866185e6661d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167219"
---
# <a name="compiler-error-c2032"></a>C2032 błąd kompilatora
"identyfikator": funkcja nie może być członkiem struktury/Unii "structorunion"  
  
 Struktura lub związek miała funkcji członkowskiej, co jest dozwolone w języku C++, ale nie w C. Aby rozwiązać problem, skompiluj jako program w języku C++ lub Usuń funkcję elementu członkowskiego.  
  
 Poniższy przykład generuje C2032:  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```