---
title: Błąd kompilatora C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: eff7c7a4f39524aa1d894b7b4590aa809714aae6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041205"
---
# <a name="compiler-error-c3481"></a>Błąd kompilatora C3481

"var": zmienna przechwytująca lambdę nie znaleziono

Kompilator nie można odnaleźć definicji zmiennej, które przekazałeś do listy przechwytywania wyrażenia lambda.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń zmienną z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3481, ponieważ zmienna `n` nie jest zdefiniowany:

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)