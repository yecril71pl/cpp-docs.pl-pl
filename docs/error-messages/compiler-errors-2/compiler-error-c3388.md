---
title: Błąd kompilatora C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: bb2a847c24b2a0b7829008793f311459e76587f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758349"
---
# <a name="compiler-error-c3388"></a>Błąd kompilatora C3388

"Type": niedozwolone jako ograniczenie, przy założeniu, że element "ref class" będzie kontynuował analizowanie

Określono ograniczenie dla typu ogólnego, ale ograniczenie nie zostało prawidłowo określone. Aby uzyskać więcej informacji, zobacz [ograniczeniaC++dotyczące parametrów typu ogólnego (/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C3388.

```cpp
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```
