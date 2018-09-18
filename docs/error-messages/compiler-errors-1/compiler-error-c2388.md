---
title: Błąd kompilatora C2388 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6bcec4f5f218a52981a7770f5fa6e600494d9a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114153"
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