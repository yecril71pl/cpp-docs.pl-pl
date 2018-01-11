---
title: "C2032 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2032
dev_langs: C++
helpviewer_keywords: C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 87703c289dc522f62c29fd2110e969fd44abf645
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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