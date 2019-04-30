---
title: Compiler Error C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 3e387fe77c521a4f25ba67205f1fbd552397e272
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381042"
---
# <a name="compiler-error-c3495"></a>Compiler Error C3495

"var": przechwytywania lambda musi mieć automatycznym okresem magazynu

Nie można dokonać przechwytu zmiennej, która nie ma czas trwania automatycznego przechowywania, takie jak zmienna, która jest oznaczona `static` lub `extern`.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie przekazuj `static` lub `extern` zmiennej do listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3495, ponieważ `static` zmiennej `n` pojawia się na liście przechwytywania wyrażenia lambda:

```
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)

