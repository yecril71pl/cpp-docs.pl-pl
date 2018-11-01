---
title: Błąd kompilatora C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: b58136cc03efda83071c531b25889743de3485f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456748"
---
# <a name="compiler-error-c3536"></a>Błąd kompilatora C3536

'symbol': nie można użyć, zanim zostanie zainicjowany

Nie można użyć symbol koła wskazane, zanim zostanie zainicjowany. W praktyce oznacza to, że zmienna nie może służyć do zainicjowania.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie Inicjuj zmienną z samym sobą.

## <a name="example"></a>Przykład

Poniższy przykład daje C3536, ponieważ każda zmienna jest inicjowana z samym sobą.

```
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../../cpp/auto-keyword.md)