---
title: C3417 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3417
dev_langs:
- C++
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b83c3b6cf5697ca2e52f9f8ad6afdc2754edd4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3417"></a>C3417 błąd kompilatora
"członek": typy wartości nie może zawierać zdefiniowane przez użytkownika specjalne funkcje Członkowskie  
  
 Typy wartości nie może zawierać funkcji, takich jak konstruktora wystąpienia domyślnego, destruktor lub Konstruktor kopiujący.  
  
 Poniższy przykład generuje C3517:  
  
```  
// C3417.cpp  
// compile with: /clr /c  
value class VC {  
   VC(){}   // C3417  
  
   // OK  
   static VC(){}  
   VC(int i){}  
};  
```