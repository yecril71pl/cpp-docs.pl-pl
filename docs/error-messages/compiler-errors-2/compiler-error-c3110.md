---
title: Błąd kompilatora C3110 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3110
dev_langs:
- C++
helpviewer_keywords:
- C3110
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81a5ebca8b1ad4fcc93b57ba49bce64a554131a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077090"
---
# <a name="compiler-error-c3110"></a>Błąd kompilatora C3110

"nazwa_funkcji": nie można przeciążyć metody interfejsu COM

Interfejs, który jest poprzedzony przez atrybut interfejsu, takich jak:

- [custom](../../windows/custom-cpp.md)

- [dispinterface](../../windows/dispinterface.md)

- [dual](../../windows/dual.md)

- [object](../../windows/object-cpp.md)

Nie można przeciążyć. Na przykład:

```
// C3110.cpp
#include <unknwn.h>
[ object, uuid= "4F98A180-EF37-11D1-978D-0000F805D73B" ]
__interface ITestInterface
{
   HRESULT mf1(void);
   HRESULT mf1(BSTR); // C3110
};

int main()
{
}
```