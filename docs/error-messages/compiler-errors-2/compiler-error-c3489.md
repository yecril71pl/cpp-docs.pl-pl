---
title: Compiler Error C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: d2ba8d919ab71b566950cc227588e071d24016bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381114"
---
# <a name="compiler-error-c3489"></a>Compiler Error C3489

"var" jest wymagana, gdy domyślny tryb przechwytywania to przez wartość

Po określeniu, że domyślny tryb przechwytywania wyrażenia lambda jest przez wartość, nie można przekazać zmiennej przez wartość do klauzuli przechwytywania, to wyrażenie.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie jawnie przekazać zmienną do klauzuli przechwytywania, lub

- Przez wartość nie zostanie podana jako domyślny tryb przechwytywania, lub

- Określ przez odwołanie jako domyślny tryb przechwytywania, lub

- W odniesieniu do klauzuli przechwytywania, należy przekazać zmienną. (Może to zmienić zachowanie Wyrażenie lambda).

## <a name="example"></a>Przykład

Poniższy przykład generuje zmiennej C3489 `n` pojawia się według wartości w klauzuli capture wyrażenia lambda, której domyślnym trybem jest przez wartość:

```
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

## <a name="example"></a>Przykład

Poniższy przykład przedstawia cztery możliwych rozwiązań do C3489:

```
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