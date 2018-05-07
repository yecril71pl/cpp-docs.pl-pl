---
title: C3161 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d7aff3eb41c03f5be774704922340ac54126fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3161"></a>C3161 błąd kompilatora
"interface": zagnieżdżanie klasy, struktury, Unii lub interfejsu w interfejsie jest niedozwolone; Zagnieżdżanie interfejsu w klasy, struktury lub Unii jest niedozwolony  
  
 [__Interface](../../cpp/interface.md) może występować tylko w zakresie globalnym lub w przestrzeni nazw. Klasy, struktury lub związku nie są wyświetlane w interfejsie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3161.  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```