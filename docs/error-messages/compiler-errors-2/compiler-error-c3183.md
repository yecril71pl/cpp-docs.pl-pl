---
title: C3183 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3183
dev_langs:
- C++
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4520922550dfcb5050c5e8a122910acf4b124934
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3183"></a>C3183 błąd kompilatora
Nie można zdefiniować nienazwanej klasy, struktury lub związku wewnątrz zarządzane lub WinRT "typu"  
  
Typ, który jest osadzony w zarządzanych lub WinRT musi mieć nazwę typu.  
  
Poniższy przykład generuje C3183:  
  
```  
// C3183a.cpp  
// compile with: /clr /c  
ref class Test  
{  
   ref class  
   {  // C3183, delete class or name it  
      int a;  
      int b;  
   };  
};  
```  
