---
title: Błąd kompilatora C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 1a61d4f2472ef6da8aedcf8a8ef90b70de47d8af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738274"
---
# <a name="compiler-error-c3495"></a>Błąd kompilatora C3495

"var": Przechwytywanie lambda musi mieć automatyczny czas trwania magazynu

Nie można przechwycić zmiennej, która nie ma automatycznego czasu trwania magazynu, na przykład zmiennej, która jest oznaczona `static` lub `extern`.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie przekazuj `static` lub zmiennej `extern` do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3495, ponieważ zmienna `static` `n` pojawia się na liście przechwytywania wyrażenia lambda:

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)

