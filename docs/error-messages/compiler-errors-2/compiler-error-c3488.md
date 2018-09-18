---
title: Błąd kompilatora C3488 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3488
dev_langs:
- C++
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15e1a21781eed96ee3a2a1430da8e43013393912
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061801"
---
# <a name="compiler-error-c3488"></a>Błąd kompilatora C3488

"var" nie jest dozwolone, gdy domyślny tryb przechwytywania to przez odwołanie

Po określeniu, czy domyślny tryb przechwytywania wyrażenia lambda jest przez odwołanie, nie można przekazać zmiennej w odniesieniu do klauzuli przechwytywania tego wyrażenia.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie jawnie przekazać zmienną do klauzuli przechwytywania, lub

- Nie określaj przez odwołanie jako domyślny tryb przechwytywania, lub

- Określ przez wartość jako domyślny tryb przechwytywania, lub

- Przekazać wartość zmiennej do klauzuli przechwytywania. (Może to zmienić zachowanie Wyrażenie lambda).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3488, ponieważ odwołanie do zmiennej `n` występuje w klauzuli przechwytywania wyrażenia lambda, w których domyślny tryb to przez odwołanie:

```
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

## <a name="example"></a>Przykład

Poniższy przykład przedstawia cztery możliwych rozwiązań do C3488:

```
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

## <a name="see-also"></a>Zobacz też

[Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)