---
title: Błąd kompilatora C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 67eaa9806dff96783f391c46c890b34e1ceef5a3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738417"
---
# <a name="compiler-error-c3489"></a>Błąd kompilatora C3489

element "var" jest wymagany, gdy domyślny tryb przechwytywania jest przez wartość

Po określeniu, że domyślny tryb przechwytywania dla wyrażenia lambda jest przez wartość, nie można przekazać zmiennej przez wartość do klauzuli przechwytywania tego wyrażenia.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie przekazuj jawnie zmiennej do klauzuli Capture lub

- Nie określaj według wartości jako domyślnego trybu przechwytywania ani

- Określ jako domyślny tryb przechwytywania, lub

- Przekaż zmienną przez odwołanie do klauzuli Capture. (Może to spowodować zmianę zachowania wyrażenia lambda).

## <a name="example"></a>Przykład

Poniższy przykład generuje zmienną C3489 `n` pojawia się według wartości w klauzuli Capture wyrażenia lambda, którego tryb domyślny ma wartość:

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono cztery możliwe rozwiązania C3489:

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
