---
title: "C3156 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3156
dev_langs: C++
helpviewer_keywords: C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 793b143fa42e790610a086782c4bf99369965e1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3156"></a>C3156 błąd kompilatora
"class": nie masz lokalnej definicji typu zarządzanego lub typu WinRT  
  
 Funkcja nie może zawierać definicji lub deklaracja zarządzanego lub WinRT klasy, struktury lub interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3156.  
  
```  
// C3156.cpp  
// compile with: /clr /c  
void f() {  
   ref class X {};   // C3156  
   ref class Y;   // C3156  
}  
```  
