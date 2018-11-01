---
title: Błąd kompilatora C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581470"
---
# <a name="compiler-error-c3320"></a>Błąd kompilatora C3320

"type": typ nie może mieć taką samą nazwę jak właściwość modułu "name"

Wyeksportowanego typu zdefiniowanego przez użytkownika (UDT), co może być struktury, klasy, enum lub Unii, nie może mieć takiej samej nazwie, jako parametr przekazywany do [modułu](../../windows/module-cpp.md) właściwości name atrybutu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3320:

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```