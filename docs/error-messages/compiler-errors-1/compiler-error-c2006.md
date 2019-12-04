---
title: Błąd kompilatora C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756555"
---
# <a name="compiler-error-c2006"></a>Błąd kompilatora C2006

"dyrektywa" oczekuje nazwy pliku, znaleziono "token"

Dyrektywy takie jak [#include](../../preprocessor/hash-include-directive-c-cpp.md) lub [#import](../../preprocessor/hash-import-directive-cpp.md) wymagają pliku filename. Aby rozwiązać ten problem, upewnij się, że *token* jest prawidłową nazwą pliku. Należy również umieścić nazwę pliku w podwójnych cudzysłowach lub nawiasach kątowych.

Poniższy przykład generuje C2006:

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

Możliwe rozwiązanie:

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```
