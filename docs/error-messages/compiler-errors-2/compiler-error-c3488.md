---
title: Błąd kompilatora C3488
ms.date: 11/04/2016
f1_keywords:
- C3488
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
ms.openlocfilehash: a39c625e63936700661790023a983fa39eeda369
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685795"
---
# <a name="compiler-error-c3488"></a>Błąd kompilatora C3488

element "var" jest niedozwolony, gdy domyślny tryb przechwytywania to-Reference

Po określeniu, że domyślny tryb przechwytywania dla wyrażenia lambda jest przez odwołanie, nie można przekazać zmiennej przez odwołanie do klauzuli przechwytywania tego wyrażenia.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie przekazuj jawnie zmiennej do klauzuli Capture lub

- Nie określaj przez-Reference jako domyślnego trybu przechwytywania lub

- Określ wartość jako domyślny tryb przechwytywania lub

- Przekaż zmienną według wartości do klauzuli Capture. (Może to spowodować zmianę zachowania wyrażenia lambda).

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C3488, ponieważ odwołanie do zmiennej `n` pojawia się w klauzuli Capture wyrażenia lambda, którego domyślnym trybem jest odwołanie:

```cpp
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

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
