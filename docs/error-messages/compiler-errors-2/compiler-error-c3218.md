---
title: Błąd kompilatora C3218
ms.date: 11/04/2016
f1_keywords:
- C3218
helpviewer_keywords:
- C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
ms.openlocfilehash: 386a0c180dd01161ebccdd2b04e899e0cc999614
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737988"
---
# <a name="compiler-error-c3218"></a>Błąd kompilatora C3218

"Type": typ nie jest dozwolony jako ograniczenie

Aby można było wprowadzić ograniczenie, musi to być typ wartości lub odwołanie do zarządzanej klasy lub interfejsu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3218.

```cpp
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
