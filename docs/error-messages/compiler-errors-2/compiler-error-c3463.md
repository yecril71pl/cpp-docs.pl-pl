---
title: Błąd kompilatora C3463 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3463
dev_langs:
- C++
helpviewer_keywords:
- C3463
ms.assetid: 153efcc0-085c-4615-84ea-d22942618bdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2169897a3ad4a6d2d78f22b7ea323d70020e1b12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036621"
---
# <a name="compiler-error-c3463"></a>Błąd kompilatora C3463

"type": typ nie jest dozwolony w atrybucie "implements"

Nieprawidłowy typ został przekazany do [implementuje](../../windows/implements-cpp.md) atrybutu. Na przykład, można przekazać do interfejsu `implements`, ale nie można przekazać wskaźnik do interfejsu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3463.

```
// C3463.cpp
// compile with: /c
#include <windows.h>
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface X {};

typedef X* PX;

[ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=PX) ]   // C3463
// try the following line instead
// [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=X) ]
class CMyClass : public X {};
```