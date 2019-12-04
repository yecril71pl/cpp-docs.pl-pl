---
title: Błąd kompilatora C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d20b5e816930969278536fe3771df4ad38c3c86b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737520"
---
# <a name="compiler-error-c3399"></a>Błąd kompilatora C3399

"Type": nie można podać argumentów podczas tworzenia wystąpienia parametru generycznego

Podczas określania ograniczenia `gcnew()` należy określić, że typ ograniczenia będzie miał Konstruktor bez parametrów. W związku z tym, wystąpił błąd podczas próby utworzenia wystąpienia tego typu i przekazania parametru.

Aby uzyskać więcej informacji, zobacz [ograniczeniaC++dotyczące parametrów typu ogólnego (/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C3399.

```cpp
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```
