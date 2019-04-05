---
title: Compiler Error C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: 381e665745f79f6156350f66e412f0580a06f6fb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027314"
---
# <a name="compiler-error-c3499"></a>Compiler Error C3499

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)