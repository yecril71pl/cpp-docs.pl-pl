---
title: Błąd kompilatora C2646 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2646
dev_langs:
- C++
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c94895dfd429723819190ad622e3a7d93fd38a99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104273"
---
# <a name="compiler-error-c2646"></a>Błąd kompilatora C2646

anonimowej struktury lub Unii, globalnie lub zakresie przestrzeni nazw musi być zadeklarowane jako statyczne

Anonimowej struktury lub Unii ma globalne lub zakresie przestrzeni nazw ale nie jest zadeklarowana `static`.

Poniższy przykład generuje C2646 i pokazuje, jak go naprawić:

```
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```