---
title: "C3923 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3923
dev_langs: C++
helpviewer_keywords: C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 863273ec0e9922a6a0b4e7355fe47178a7dd5bbe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3923"></a>C3923 błąd kompilatora
"członek": lokalnej klasy, struktury lub Unii definicje są niedozwolone w funkcji członkowskiej klasy zarządzanej lub WinRT  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3923.  
  
```  
// C3923.cpp  
// compile with: /clr /c  
ref struct x {  
   void Test() {  
      struct a {};   // C3923  
      class b {};   // C3923  
      union c {};   // C3923  
   }  
};  
```