---
title: C3136 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f892c7f3d1ca7bf2aebf3ecfe7574182b544fd01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3136"></a>C3136 błąd kompilatora
"interface": interfejs COM może tylko dziedziczyć z innego interfejsu COM, "interface" nie jest interfejsem COM  
  
 Interfejs, do którego należy zastosować [atrybutu interfejsu](../../windows/interface-attributes.md) dziedziczy interfejs, który nie jest interfejsem COM. Interfejs COM, ale ostatecznie dziedziczy `IUnknown`. Każdy interfejs poprzedzony przez atrybut interfejs jest interfejsem COM.  
  
 Poniższy przykład generuje C3136:  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```