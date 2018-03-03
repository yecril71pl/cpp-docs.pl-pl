---
title: "C3865 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cec5eabe6f4fa62648e9d3787d8ef2d2133f7736
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3865"></a>C3865 błąd kompilatora
"calling_convention": można używać tylko w natywnych funkcjach Członkowskich  
  
 Konwencja wywoływania została użyta w funkcję, która została globalnej funkcji lub funkcja zarządzanego elementu członkowskiego. Konwencja wywoływania może służyć tylko w funkcji natywnej (nie zarządzanego) elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [konwencji wywoływania](../../cpp/calling-conventions.md).  
  
 Poniższy przykład generuje C3865:  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```