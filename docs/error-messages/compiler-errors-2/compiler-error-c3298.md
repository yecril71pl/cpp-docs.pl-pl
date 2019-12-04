---
title: Błąd kompilatora C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: d5e9586b026e0092491c80c23f55080354c9e465
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760078"
---
# <a name="compiler-error-c3298"></a>Błąd kompilatora C3298

"constraint_1": nie można użyć "constraint_2" jako ograniczenia, ponieważ element "constraint_2" ma ograniczenie ref, a element "constraint_1" ma ograniczenie wartości

Nie można określić wzajemnie wykluczających się właściwości ograniczenia. Na przykład parametr typu generycznego nie może być ograniczony do typu wartości i typu referencyjnego.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnegoC++(/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3298.

```cpp
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```
