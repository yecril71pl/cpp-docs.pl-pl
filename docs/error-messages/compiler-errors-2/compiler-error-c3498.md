---
title: Compiler Error C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 463e210e5a1ac5eb6d197062ed8921f9bbae4ad2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381010"
---
# <a name="compiler-error-c3498"></a>Compiler Error C3498

"var": nie można dokonać przechwytu zmiennej, która ma zarządzanej lub WinRTtype

Nie można dokonać przechwytu zmiennej, która ma typ zarządzany lub typu środowiska wykonawczego Windows w wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przekaż zarządzany lub zmiennej środowiska wykonawczego Windows, do listy parametrów wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3498, ponieważ zmienna, która ma typ zarządzany, który pojawia się na liście przechwytywania wyrażenia lambda:

```
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

Poniższy przykład usuwa C3498 przez przekazanie zmiennej zarządzanych `s` do listy parametrów wyrażenia lambda:

```
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