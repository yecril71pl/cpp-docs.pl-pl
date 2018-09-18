---
title: Kompilator ostrzeżenie (poziom 1) C4925 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4925
dev_langs:
- C++
helpviewer_keywords:
- C4925
ms.assetid: a4b206c0-016a-4f28-873a-bb8bb41bad50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62c661b4fffee6c6da17d72724d61b7df39a3268
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109447"
---
# <a name="compiler-warning-level-1-c4925"></a>Kompilator ostrzeżenie (poziom 1) C4925

"method": metoda interfejsu dispinterface nie może być wywoływana ze skryptu

Języki skryptów nie można utworzyć VT_BYREF parametru "in", można tylko utworzyć VT_BYREF parametrów "out".

Innym sposobem rozwiązania tego ostrzeżenia jest nie parametrze (w definicję i implementację) typ wskaźnika.

Poniższy przykład spowoduje wygenerowanie C4925:

```
// C4925.cpp
// compile with: /LD /W1
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[ module(name="Test")];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IDisp {
   [id(9)] void f([in] int*);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002")  ]
struct CDisp : IDisp {   // C4925
   void f(int*) {}
};
```