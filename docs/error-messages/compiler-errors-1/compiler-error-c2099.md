---
title: Compiler Error C2099
ms.date: 11/04/2016
f1_keywords:
- C2099
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
ms.openlocfilehash: 9c83b4a50cb9cf5c5b1992f0f64e2eeb013b48e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376945"
---
# <a name="compiler-error-c2099"></a>Compiler Error C2099

Inicjator nie jest stałą

Ten błąd jest wystawiane tylko przez kompilator języka C i występuje tylko w przypadku zmiennych nie automatyczne.  Kompilator inicjalizuje-automatyczne zmienne na początku programu, a wartości, które są inicjowane musi być stałą.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2099.

```
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

## <a name="example"></a>Przykład

C2099 może również wystąpić, ponieważ kompilator nie będzie mógł wykonywać składania stałej w wyrażeniu w obszarze **/FP: strict** ponieważ zmiennoprzecinkowy ustawienia środowiska precyzji (zobacz [_controlfp_s —](../../c-runtime-library/reference/controlfp-s.md) dla więcej informacji) może się różnić od kompilacji do czasu wykonywania.

Gdy jest to stała składanie kończy się niepowodzeniem, kompilator wywołuje dynamiczna Inicjalizacja, która nie jest dozwolona w C.

Aby rozwiązać ten problem, skompiluj moduł jako plik .cpp lub Uprość wyrażenie.

Aby uzyskać więcej informacji, zobacz [/FP (określenie zachowania zmiennopozycyjna)](../../build/reference/fp-specify-floating-point-behavior.md).

Poniższy przykład spowoduje wygenerowanie C2099.

```
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```