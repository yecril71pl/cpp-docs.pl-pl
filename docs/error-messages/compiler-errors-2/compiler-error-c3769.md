---
title: C3769 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3769
dev_langs:
- C++
helpviewer_keywords:
- C3769
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5258c3dadd7ede384520b76e95c1b8e691882f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266975"
---
# <a name="compiler-error-c3769"></a>C3769 błąd kompilatora
"type": zagnieżdżona klasa nie może mieć taką samą nazwę jako natychmiastowo otaczającą klasę  
  
 Zagnieżdżona klasa nie może mieć taką samą nazwę jak natychmiastowo otaczającą klasę.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3769.  
  
```  
// C3769.cpp  
// compile with: /c  
class x {  
   class x {};   // C3769  
   class y {  
      class x{};   // OK  
   };  
};  
```