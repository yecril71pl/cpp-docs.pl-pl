---
title: Błąd kompilatora C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: a67d4d859e3a9dd2241f14a476492df0fd3e6b8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223424"
---
# <a name="compiler-error-c3495"></a>Błąd kompilatora C3495

"var": Przechwytywanie lambda musi mieć automatyczny czas trwania magazynu

Nie można przechwycić zmiennej, która nie ma automatycznego czasu trwania magazynu, na przykład zmiennej oznaczonej jako **`static`** lub **`extern`** .

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie przekazuj **`static`** ani **`extern`** zmiennej do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3495, ponieważ **`static`** zmienna `n` pojawia się na liście przechwytywania wyrażenia lambda:

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
