---
title: Błąd kompilatora C2732 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 040fd73bcb69ef032d5c6150bb157337f34a2088
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079664"
---
# <a name="compiler-error-c2732"></a>Błąd kompilatora C2732

Specyfikacja powiązania jest sprzeczna wcześniejszą specyfikacją dla "function"

Funkcja jest już zadeklarowana ze specyfikatorem różne powiązania.

Ten błąd może być spowodowany przez obejmują plików przy użyciu specyfikatorów różne powiązania.

Aby naprawić ten błąd, zmień `extern` instrukcji, aby zaakceptować powiązań. W szczególności, nie jest zawijany `#include` dyrektywy w `extern "C"` bloków.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2732:

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```