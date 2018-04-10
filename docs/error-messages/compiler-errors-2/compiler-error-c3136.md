---
title: C3136 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2b4daa5076a04825cea6a96709f40716f3eaeff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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