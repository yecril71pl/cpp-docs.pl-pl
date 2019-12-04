---
title: Błąd kompilatora C3499
ms.date: 11/04/2016
f1_keywords:
- C3499
helpviewer_keywords:
- C3499
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
ms.openlocfilehash: e50aaeac4a9f02cf3e67c25a08afdc2df0f1c62f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738014"
---
# <a name="compiler-error-c3499"></a>Błąd kompilatora C3499

lambda, która została określona jako zwracająca typ void nie może zwracać wartości

Kompilator generuje ten błąd, gdy wyrażenie lambda, które określa `void` jako zwracany typ zwraca wartość; lub gdy wyrażenie lambda zawiera więcej niż jedną instrukcję i zwraca wartość, ale nie określa jej typu zwracanego.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie zwracaj wartości z wyrażenia lambda lub

- Podaj zwracany typ wyrażenia lambda lub

- Połącz instrukcje tworzące treść wyrażenia lambda w pojedynczej instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3499, ponieważ treść wyrażenia lambda zawiera wiele instrukcji i zwraca wartość, ale wyrażenie lambda nie określa zwracanego typu:

```cpp
// C3499a.cpp

int main()
{
   [](int x) { int n = x * 2; return n; } (5); // C3499
}
```

## <a name="example"></a>Przykład

Poniższy przykład przedstawia dwa możliwe rozwiązania do C3499. Pierwsze rozwiązanie zapewnia zwracany typ wyrażenia lambda. Druga rozdzielczość łączy instrukcje, które tworzą treść wyrażenia lambda w pojedynczej instrukcji.

```cpp
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
