---
title: "C2824 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2824
dev_langs: C++
helpviewer_keywords: C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d480198a93b7b2154eb66286db7d8e3d921de5ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2824"></a>C2824 błąd kompilatora
typem zwracanym dla "operator new" musi być "void *"  
  
 Z innych wskaźników overloads operatora `new` musi zwracać `void *`.  
  
 Poniższy przykład generuje C2824:  
  
```  
// C2824.cpp  
// compile with: /c  
class   A {  
   A* operator new(size_t i, char *m);   // C2824  
   // try the following line instead  
   // void* operator new(size_t i, char *m);  
};  
```