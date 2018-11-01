---
title: Błąd kompilatora C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: b856f607d764ac0a42781a80787663d965748317
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626905"
---
# <a name="compiler-error-c3480"></a>Błąd kompilatora C3480

"var": zmienna przechwytująca lambdę musi być z otaczającego zakresu funkcji

Zmienna przechwytująca lambdę nie pochodzi z otaczającego zakresu funkcji.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Usuń zmienną z listy przechwytywania wyrażenia lambda.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3480, ponieważ zmienna `global` nie pochodzi z otaczającego zakresu funkcji:

```
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>Przykład

Poniższy przykład usuwa C3480, usuwając zmiennej `global` z listy przechwytywania wyrażenia lambda:

```
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)