---
title: "C2081 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2081
dev_langs: C++
helpviewer_keywords: C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10a3e8f4444fcdb0fe9e286abf5331c1d8bae523
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2081"></a>C2081 błąd kompilatora
'Identyfikator': Nazwa w liście parametrów formalnych jest niedozwolony  
  
 Identyfikator spowodował błąd składni.  
  
 Ten błąd może być spowodowany przy użyciu stary styl formalnej listy parametrów. Należy podać typ parametrów formalnych na liście parametrów formalnych.  
  
 Poniższy przykład generuje C2081:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```