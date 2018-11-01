---
title: Błąd kompilatora C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: 8a2d8f6ab72a5e72a646cb1fca64635bc72dd2ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492848"
---
# <a name="compiler-error-c3298"></a>Błąd kompilatora C3298

"constraint_1": nie można użyć "constraint_2" jako ograniczenie, ponieważ "constraint_2" ma ograniczenie ref oraz 'constraint_1' posiada wartość ograniczenia

Nie można określić wzajemnie wykluczających się właściwości ograniczenia. Na przykład parametru typu generycznego nie może być ograniczony do typu wartości i typ odwołania.

Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3298.

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```