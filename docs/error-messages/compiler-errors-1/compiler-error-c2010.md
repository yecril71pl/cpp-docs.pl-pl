---
title: Błąd kompilatora C2010
ms.date: 11/04/2016
f1_keywords:
- C2010
helpviewer_keywords:
- C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
ms.openlocfilehash: 71cb0012f5e7bda3a0f1409fe71649a5bd0944b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434228"
---
# <a name="compiler-error-c2010"></a>Błąd kompilatora C2010

"character": nieoczekiwany w formalnej liście parametrów makra

Znak jest niepoprawnie używany na liście parametrów formalnych w definicji makra. Usuń znak, aby naprawić błąd.

Poniższy przykład spowoduje wygenerowanie C2010:

```
// C2010.cpp
// compile with: /c
#define mymacro(a|) (2*a)   // C2010
#define mymacro(a) (2*a)   // OK
```