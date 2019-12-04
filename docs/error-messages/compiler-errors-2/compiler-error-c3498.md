---
title: Błąd kompilatora C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 771e8c72ab4386bb45a11983318f412e784f5bc9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738105"
---
# <a name="compiler-error-c3498"></a>Błąd kompilatora C3498

"var": nie można przechwycić zmiennej, która ma zarządzany lub WinRTtype

Nie można przechwycić zmiennej, która ma typ zarządzany lub środowisko wykonawcze systemu Windows typu w lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przekaż zmienną zarządzaną lub środowisko wykonawcze systemu Windows do listy parametrów wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3498, ponieważ zmienna, która ma typ zarządzany, pojawia się na liście przechwytywania wyrażenia lambda:

```cpp
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>Przykład

Poniższy przykład rozwiązuje C3498 przez przekazanie zmiennej zarządzanej `s` do listy parametrów wyrażenia lambda:

```cpp
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
