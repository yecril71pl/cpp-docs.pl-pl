---
title: Błąd kompilatora C3488
ms.date: 11/04/2016
f1_keywords:
- C3488
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
ms.openlocfilehash: 2b69ed4ac8b7e706096d107e9dfaa4447ca1bc79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738430"
---
# <a name="compiler-error-c3488"></a>Błąd kompilatora C3488

element "var" jest niedozwolony, gdy domyślny tryb przechwytywania to-Reference

Po określeniu, że domyślny tryb przechwytywania dla wyrażenia lambda jest przez odwołanie, nie można przekazać zmiennej przez odwołanie do klauzuli przechwytywania tego wyrażenia.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie przekazuj jawnie zmiennej do klauzuli Capture lub

- Nie określaj przez-Reference jako domyślnego trybu przechwytywania lub

- Określ wartość jako domyślny tryb przechwytywania lub

- Przekaż zmienną według wartości do klauzuli Capture. (Może to spowodować zmianę zachowania wyrażenia lambda).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3488, ponieważ odwołanie do zmiennej `n` pojawia się w klauzuli Capture wyrażenia lambda, którego domyślnym trybem jest odwołanie:

```cpp
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono cztery możliwe rozwiązania C3488:

```cpp
// C3488b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass &n to the capture clause.
   [&]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-reference as the default capture mode.
   [&n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-value as the default capture mode.
   [=, &n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by value to the capture clause.
   [n]() { return n; } ();
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)
