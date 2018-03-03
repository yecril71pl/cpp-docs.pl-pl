---
title: "C3846 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ede4decb1a6dde5a85008c6e15f5f764224627e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3846"></a>C3846 błąd kompilatora
"symbol": nie można zaimportować symbolu z "assembly2": ponieważ "symbol" został już zaimportowany z innego zestawu "zestaw1"  
  
 Nie można zaimportować symbolu z przywoływanego zestawu, ponieważ nie zostały wcześniej zaimportowane z przywoływanego zestawu.  
  
## <a name="example"></a>Przykład
Poniższy przykład generuje C3846:  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 A następnie skompilować to:  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  
