---
title: "C2774 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2774
dev_langs: C++
helpviewer_keywords: C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b5b8b898dead7d08795e25d87f66a2c24214fc3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2774"></a>C2774 błąd kompilatora
'Identyfikator': nie metody "put" jest skojarzony z tą właściwością  
  
 Element członkowski danych zadeklarowana z [właściwości](../../cpp/property-cpp.md) nie ma `put` funkcji, ale wyrażenie usiłuje ustawić jej wartości.  
  
 Poniższy przykład generuje C2774:  
  
```  
// C2774.cpp  
struct A {  
   __declspec(property(get=GetProp)) int prop;  
   int GetProp(void);  
  
   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;  
   int GetProp2(void);  
   void PutProp2(int);  
};  
  
int main() {  
   A* pa = new A;  
   int val = 0;  
   pa->prop = val;   // C2774  
   pa->prop++;   // C2774  
}  
```