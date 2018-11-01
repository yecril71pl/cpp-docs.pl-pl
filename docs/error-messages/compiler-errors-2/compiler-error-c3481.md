---
title: Błąd kompilatora C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: 32a04c2c49f8d9d974c3423756c4c9fc59a46495
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661984"
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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)