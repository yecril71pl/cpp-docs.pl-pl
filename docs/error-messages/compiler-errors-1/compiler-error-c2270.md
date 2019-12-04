---
title: Błąd kompilatora C2270
ms.date: 11/04/2016
f1_keywords:
- C2270
helpviewer_keywords:
- C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
ms.openlocfilehash: 67dc970ffb5dac218072ff98046f88c31a9c2db9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758726"
---
# <a name="compiler-error-c2270"></a>Błąd kompilatora C2270

"Function": Modyfikatory niedozwolone dla funkcji niebędących członkami

Funkcja nieczłonkowska jest zadeklarowana przy użyciu elementu [const](../../cpp/const-cpp.md), [volatile](../../cpp/volatile-cpp.md)lub innego modyfikatora pamięci.

Poniższy przykład generuje C2270:

```cpp
// C2270.cpp
// compile with: /c
void func1(void) const;   // C2270, nonmember function

void func2(void);

class CMyClass {
public:
   void func2(void) const;
};
```
