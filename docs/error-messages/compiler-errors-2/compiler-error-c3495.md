---
title: Błąd kompilatora C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 6fe4286142c90f341925d7e76ca8de6d3b7daa9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075008"
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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
