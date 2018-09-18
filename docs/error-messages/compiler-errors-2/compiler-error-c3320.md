---
title: Błąd kompilatora C3320 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b67d419630d59902270638213ce7a79dd8b9e0c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078442"
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