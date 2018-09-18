---
title: Błąd kompilatora C2862 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2862
dev_langs:
- C++
helpviewer_keywords:
- C2862
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cfd5ee07ecd7ca1613c4e7b5584294e58aace3e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049790"
---
# <a name="compiler-error-c2862"></a>Błąd kompilatora C2862

"interface": interfejs może mieć tylko publiczne elementy członkowskie

Chronione i prywatnych składowych można uzyskać dostęp tylko z innych funkcji Członkowskich. Takich elementów członkowskich są użycia w interfejsie, ponieważ nie może dostarczać implementacje dla każdego z jej członków.

Poniższy przykład spowoduje wygenerowanie C2862:

```
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