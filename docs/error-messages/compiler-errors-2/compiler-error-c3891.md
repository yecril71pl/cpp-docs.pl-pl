---
title: "C3891 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3891
dev_langs: C++
helpviewer_keywords: C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: daf8c50dfb041194e376b1b62943da021a423ed4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3891"></a>C3891 błąd kompilatora
"var": literał elementu członkowskiego danych nie można użyć jako l wartością  
  
 A [literału](../../windows/literal-cpp-component-extensions.md) zmienna jest stała i jej wartości nie można zmienić po jego inicjowania w deklaracji.  
  
 Poniższy przykład generuje C3891:  
  
```  
// C3891.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   Y1::staticConst = 0;   // C3891  
}  
```