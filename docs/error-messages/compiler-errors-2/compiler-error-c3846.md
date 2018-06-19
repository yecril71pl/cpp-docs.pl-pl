---
title: C3846 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97d5650d1743ba379ce065d4051bfed807a1df71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268029"
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
