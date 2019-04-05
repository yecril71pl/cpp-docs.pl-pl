---
title: Błąd kompilatora C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: acbe89b5183d0991fb8d4a571a9595d6f6bafc6c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026126"
---
# <a name="compiler-error-c3483"></a>Błąd kompilatora C3483

"var" jest już częścią listy przechwytów lambdy

Tę samą zmienną jest przekazywane do listy przechwytywania wyrażenia lambda więcej niż jeden raz.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Z listy przechwytywania, należy usunąć wszystkie dodatkowe wystąpienia w zmiennej.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3483, ponieważ zmienna `n` pojawia się więcej niż jeden raz na liście przechwytywania wyrażenia lambda:

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)