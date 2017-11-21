---
title: "Kompilatora (poziom 2) ostrzeżenie C4150 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4150
dev_langs: C++
helpviewer_keywords: C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: abf4b51e79cd282ab3a76e89f6c746f4e5cf5298
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4150"></a>Kompilator C4150 ostrzegawcze (poziom 2)
Usunięcie wskaźnika do niekompletnego typu 'type'; Brak wywołania destruktora  
  
 **Usunąć** operator jest wywoływana, aby usunąć typu, który został zadeklarowany, ale nie jest zdefiniowany, dlatego kompilator nie może odnaleźć destruktora.  
  
 Poniższy przykład generuje C4150:  
  
```  
// C4150.cpp  
// compile with: /W2  
class  IncClass;  
  
void NoDestruct( IncClass* pIncClass )  
{  
   delete pIncClass;  
} // C4150, define class to resolve  
  
int main()  
{  
}  
```