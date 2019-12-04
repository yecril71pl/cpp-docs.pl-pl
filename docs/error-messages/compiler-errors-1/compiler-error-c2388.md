---
title: Błąd kompilatora C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 21658a659468a6e2a0d911af70eefdaed320446c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745060"
---
# <a name="compiler-error-c2388"></a>Błąd kompilatora C2388

"symbol": nie można zadeklarować symbolu z zarówno __declspec (AppDomain), jak i \__declspec (proces)

Modyfikatory `appdomain` i `process` `__declspec` nie mogą być używane dla tego samego symbolu. Magazyn dla zmiennej istnieje dla procesu lub dla domeny aplikacji.

Aby uzyskać więcej informacji, zobacz temat [AppDomain](../../cpp/appdomain.md) i [Process](../../cpp/process.md).

Poniższy przykład generuje C2388:

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
