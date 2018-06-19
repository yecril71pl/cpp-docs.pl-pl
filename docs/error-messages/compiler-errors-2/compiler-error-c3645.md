---
title: C3645 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3645
dev_langs:
- C++
helpviewer_keywords:
- C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a711f37e3ab54de5e3cfad77b82fbd603edfaf6e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263830"
---
# <a name="compiler-error-c3645"></a>C3645 błąd kompilatora
"Funkcja": __clrcall nie można używać w funkcjach skompilowanych do natywnego kodu  
  
 Obecność niektórych słów kluczowych w funkcji spowoduje, że funkcja zestawiane na natywny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3645.  
  
```  
// C3645.cpp  
// compile with: /clr /c  
#pragma unmanaged   
int __clrcall dog() {}   // C3645  
```