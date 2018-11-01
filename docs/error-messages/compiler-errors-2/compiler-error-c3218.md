---
title: Błąd kompilatora C3218
ms.date: 11/04/2016
f1_keywords:
- C3218
helpviewer_keywords:
- C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
ms.openlocfilehash: 87084f9751b1593ec93a3062f23714bba403da9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578207"
---
# <a name="compiler-error-c3218"></a>Błąd kompilatora C3218

"type": typ nie jest dozwolony jako ograniczenia

Dla typu jako ograniczenie musi być typem wartości lub odwołania do zarządzanej klasy lub interfejsu.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3218.

```
// C3218.cpp
// compile with: /clr /c
class A {};
ref class B {};

// Delete the following 3 lines to resolve.
generic <class T>
where T : A   // C3218
ref class C {};

// OK
generic <class T>
where  T : B
ref class D {};
```