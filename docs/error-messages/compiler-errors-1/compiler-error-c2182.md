---
title: "C2182 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2182
dev_langs: C++
helpviewer_keywords: C2182
ms.assetid: dfd8d47d-9606-496e-bd96-4bf41ba1f857
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d5dc323cd1efd5ad96ee77a741414f8bfbcc12de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2182"></a>C2182 błąd kompilatora
"identyfikator": niedozwolone użycie typu "void"  
  
 Zmienna jest zadeklarowany jako typ `void`.  
  
 Poniższy przykład generuje C2182:  
  
```  
// C2182.cpp  
// compile with: /c  
int main() {  
   int i = 10;  
   void &ir = i;   // C2182 cannot have a reference to type void  
   int &ir = i;   // OK  
}  
```