---
title: Błąd kompilatora C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 62afcb1fafc19d3d61a86f2fbc10cb99e095afc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393665"
---
# <a name="compiler-error-c2388"></a>Błąd kompilatora C2388

'symbol': nie można zadeklarować symbolu z __declspec(appdomain) zarówno i \__declspec(process)

`appdomain` i `process` `__declspec` modyfikatorów nie można używać w tym samym symbolu. Magazyn dla zmiennej istnieje dla procesu lub dla domeny aplikacji.

Aby uzyskać więcej informacji, zobacz [appdomain](../../cpp/appdomain.md) i [procesu](../../cpp/process.md).

Poniższy przykład spowoduje wygenerowanie C2388:

```
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```