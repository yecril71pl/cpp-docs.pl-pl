---
title: Błąd kompilatora C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: 937b4e993919f5b6e28e3c389476854be36fa1cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668289"
---
# <a name="compiler-error-c3499"></a>Błąd kompilatora C3499

lambda, która została określona ma zwracać typ void nie może zwracać wartości

Kompilator generuje ten błąd, gdy wyrażenie lambda, które określa `void` jako typ zwracany zwraca wartość lub wyrażenie lambda zawiera więcej niż jedną instrukcję i zwraca wartość, ale nie określa jego typem zwracanym.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Zwraca wartość z wyrażenia lambda lub

- Podaj typ zwracany wyrażenia lambda lub

- Połącz instrukcji, które tworzą treść wyrażenia lambda w pojedynczej instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3499, ponieważ treść wyrażenia lambda zawiera wiele instrukcji i zwraca wartość, ale wyrażenia lambda nie określa typ zwracany:

```
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa możliwe rozwiązania do C3499. Pierwsze rozwiązanie zapewnia zwracany typ wyrażenia lambda. Drugie rozwiązanie łączy instrukcji, które tworzą treść wyrażenia lambda w pojedynczej instrukcji.

```
// C3499b.cpp

int main()
{
   // Possible resolution 1:
   // Provide the return type of the lambda expression.
   [](int x) -> int { int n = x * 2; return n; } (5);

   // Possible resolution 2:
   // Combine the statements that make up the body of
   // the lambda expression into a single statement.
   [](int x) { return x * 2; } (5);
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)