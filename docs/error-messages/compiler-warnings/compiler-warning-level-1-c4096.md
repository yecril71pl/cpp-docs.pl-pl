---
title: Kompilatora (poziom 1) ostrzeżenie C4096 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3787ef5482841e33658e02371fa0f6d1682612ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276282"
---
# <a name="compiler-warning-level-1-c4096"></a>Kompilator C4096 ostrzegawcze (poziom 1)
"": interfejs nie jest interfejsem COM; nie będzie emitowany do IDL  
  
 Definicja interfejsu mają może mieć jako interfejs COM nie został zdefiniowany jako interfejs COM i w związku z tym nie będzie emitowany do IDL pliku.  
  
 Zobacz [atrybuty interfejsu](../../windows/interface-attributes.md) dla atrybutów listy, które wskazują interfejs jest interfejsem COM.  
  
 Poniższy przykład generuje C4096:  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```