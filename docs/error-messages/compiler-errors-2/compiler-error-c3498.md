---
title: Błąd kompilatora C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: f1b978a585f3404cd3a881f25d6ef6a0f66b212d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686158"
---
# <a name="compiler-error-c3498"></a>Błąd kompilatora C3498

"var": nie można przechwycić zmiennej, która ma zarządzany lub WinRTtype

Nie można przechwycić zmiennej, która ma typ zarządzany lub środowisko wykonawcze systemu Windows typu w lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Przekaż zmienną zarządzaną lub środowisko wykonawcze systemu Windows do listy parametrów wyrażenia lambda.

## <a name="examples"></a>Przykłady

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
