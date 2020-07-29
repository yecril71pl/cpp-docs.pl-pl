---
title: Błąd kompilatora C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 50148f4fb5c3af33d8de8b005f75f491b0540271
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225504"
---
# <a name="compiler-error-c2388"></a>Błąd kompilatora C2388

"symbol": symbol nie może być zadeklarowany zarówno jako __declspec (AppDomain), jak i \_ _declspec (Process)

`appdomain` `process` **`__declspec`** Modyfikatory i nie mogą być używane dla tego samego symbolu. Magazyn dla zmiennej istnieje dla procesu lub dla domeny aplikacji.

Aby uzyskać więcej informacji, zobacz temat [AppDomain](../../cpp/appdomain.md) i [Process](../../cpp/process.md).

Poniższy przykład generuje C2388:

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
