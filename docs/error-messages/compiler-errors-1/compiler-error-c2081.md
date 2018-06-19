---
title: C2081 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 165217b3ea4d50dc965927419786a01a6cc92af3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166864"
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