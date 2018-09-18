---
title: Kompilator ostrzeżenie (poziom 4) C4682 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4682
dev_langs:
- C++
helpviewer_keywords:
- C4682
ms.assetid: 858ea157-1244-4a61-85df-97b3de43d418
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa804b96c2177fc4d263b76feeaa770fea07b5de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092638"
---
# <a name="compiler-warning-level-4-c4682"></a>Kompilator ostrzeżenie (poziom 4) C4682

"parametru": nie określono atrybutu kierunkowego parametru, domyślnie na [in]

Metoda dla parametru w interfejsie opartego na atrybutach nie ma jednego atrybuty kierunkowe: [w](../../windows/in-cpp.md) lub [się](../../windows/out-cpp.md). Parametr w.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4682:

```
// C4682.cpp
// compile with: /W4
#pragma warning(default : 4682)
#include <windows.h>
[module(name="MyModule")];

[ library_block, object, uuid("c54ad59d-d516-41dd-9acd-afda17565c2b") ]
__interface IMyIface : IUnknown
{
   HRESULT f1(int i, int *pi); // C4682
   // try the following line
   // HRESULT f1([in] int i, [in] int *pi);
};

int main()
{
}
```