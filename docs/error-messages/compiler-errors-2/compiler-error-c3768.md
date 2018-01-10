---
title: "C3768 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3768
dev_langs: C++
helpviewer_keywords: C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba2f52622cde34a8301529d569790c67a72bbb74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3768"></a>C3768 błąd kompilatora
Nie można przyjąć adresu wirtualnej funkcji vararg w czystym kodzie zarządzanym  
  
 **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015.  
  
 Podczas kompilowania za pomocą `/clr:pure`, nie można przyjąć adresu wirtualnej `vararg` funkcji.  
  
## <a name="example"></a>Przykład  

 Poniższy przykład generuje C3768:  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```