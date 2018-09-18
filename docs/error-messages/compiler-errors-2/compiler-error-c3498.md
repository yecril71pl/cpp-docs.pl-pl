---
title: Błąd kompilatora C3498 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb87abc113e586aa4f3097444df4c5a46a6a92c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106782"
---
# <a name="compiler-error-c3498"></a>Błąd kompilatora C3498

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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)