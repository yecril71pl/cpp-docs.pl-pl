---
title: Błąd kompilatora C2099 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fcbefa4d8fb9d5503f28cf3bf39cafc6b05a225
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116831"
---
# <a name="compiler-error-c2099"></a>Błąd kompilatora C2099

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