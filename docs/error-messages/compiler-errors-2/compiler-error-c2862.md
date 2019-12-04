---
title: Błąd kompilatora C2862
ms.date: 11/04/2016
f1_keywords:
- C2862
helpviewer_keywords:
- C2862
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
ms.openlocfilehash: cd14f310a00202dce73f091dee46a4605858b698
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755086"
---
# <a name="compiler-error-c2862"></a>Błąd kompilatora C2862

"Interface": interfejs może mieć tylko publiczne składowe

Dostęp do chronionych i prywatnych członków można uzyskać tylko z innych funkcji Członkowskich. Takie składowe nie są używane w interfejsie, ponieważ nie mogą zapewnić implementacji dla żadnego z jej elementów członkowskich.

Poniższy przykład generuje C2862:

```cpp
// C2862.cpp
// compile with: /c
#include <unknwn.h>

[object, uuid="60719E20-EF37-11D1-978D-0000F805D73B"]
__interface IMyInterface {
   HRESULT mf1(void);   // OK
protected:
   HRESULT mf2(int *b);   // C2862
private:
   HRESULT mf3(int *c);   // C2862
};
```
