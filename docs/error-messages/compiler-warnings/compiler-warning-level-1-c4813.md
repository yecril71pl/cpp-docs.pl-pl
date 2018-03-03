---
title: "Kompilatora (poziom 1) ostrzeżenie C4813 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4813
dev_langs:
- C++
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f4e888d924c79d18f1b12b1d92cfd0d40f5cc47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4813"></a>Kompilator C4813 ostrzegawcze (poziom 1)
"Funkcja": funkcja zaprzyjaźniona klasy lokalnej zostało wcześniej zadeklarowane  
  
 Funkcja zaprzyjaźniona klasy wewnętrzny nie został zadeklarowany w klasie zewnętrzne.  
  
 Poniższy przykład generuje C4813:  
  
```  
// C4813.cpp  
// compile with: /W1 /LD  
void MyClass()  
{  
   // void func();  
   class InnerClass  
   {  
      friend void func();   // C4813 uncomment declaration above  
   };  
}  
```