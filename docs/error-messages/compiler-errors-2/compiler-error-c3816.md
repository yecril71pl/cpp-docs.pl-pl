---
title: Błąd kompilatora C3816
ms.date: 11/04/2016
f1_keywords:
- C3816
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
ms.openlocfilehash: d362480b3380fe4576ef56b8ca76dfa10eaa1408
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557303"
---
# <a name="compiler-error-c3816"></a>Błąd kompilatora C3816

poprzednio zadeklarowany lub zdefiniowany przy użyciu różnych zarządzanych lub WinRTmodifier "deklaracją"

Deklaracją do przodu i rzeczywista deklaracja wymagającą występować nie konflikty lub niespójności w deklaracji atrybutów.

Poniższy przykład generuje C3816 i pokazuje, jak go naprawić:

```
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```