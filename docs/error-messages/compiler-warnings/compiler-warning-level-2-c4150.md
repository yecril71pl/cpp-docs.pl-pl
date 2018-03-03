---
title: "Kompilatora (poziom 2) ostrzeżenie C4150 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4150
dev_langs:
- C++
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09267a909ea6e4b0bedd43e6f31a31e778ffb904
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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