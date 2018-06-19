---
title: C2774 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2774
dev_langs:
- C++
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a6fc100bf7cd4a57c5c23630b28c41d92cf43d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234957"
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