---
title: Błąd kompilatora C3489 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b1631c9be33204edfa697cb349148d274fe30e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081224"
---
# <a name="compiler-error-c3489"></a>Błąd kompilatora C3489

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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)