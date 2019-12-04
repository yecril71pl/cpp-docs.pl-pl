---
title: Błąd kompilatora C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 83c07da5383740ca14c9b9de6224f47cf844d5fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757647"
---
# <a name="compiler-error-c3194"></a>Błąd kompilatora C3194

"member": typ wartości nie może mieć operatora przypisania

Specjalne funkcje członkowskie, które wymagają automatycznego wywołania przez kompilator, takie jak Konstruktor kopiujący lub operator przypisania kopii, nie są obsługiwane w klasie wartości.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3194.

```cpp
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```
