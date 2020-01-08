---
title: Błąd kompilatora C2099
ms.date: 11/04/2016
f1_keywords:
- C2099
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
ms.openlocfilehash: e9fb7739111d13a585579455ed97cecaca3266e4
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301941"
---
# <a name="compiler-error-c2099"></a>Błąd kompilatora C2099

Inicjator nie jest stałą

Ten błąd jest wystawiany tylko przez kompilator C i występuje tylko w przypadku zmiennych nieautomatycznych.  Kompilator inicjuje zmienne nieautomatyczne na początku programu i wartości, które są inicjowane, muszą być stałe.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2099.

```c
// C2099.c
int j;
int *p;
j = *p;   // C2099 *p is not a constant
```

## <a name="example"></a>Przykład

C2099 może również wystąpić, ponieważ kompilator nie jest w stanie wykonać ciągłej łamania na wyrażeniu w obszarze **/FP: Strict** , ponieważ ustawienia środowiska liczby zmiennoprzecinkowej (zobacz [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) więcej informacji) mogą różnić się od kompilacji w czasie wykonywania.

Gdy stałe łamanie nie powiedzie się, kompilator wywołuje dynamiczną inicjalizację, która nie jest dozwolona w C.

Aby rozwiązać ten problem, skompiluj moduł jako plik. cpp lub Uprość wyrażenie.

Aby uzyskać więcej informacji, zobacz [/FP (Określ zachowanie zmiennoprzecinkowe)](../../build/reference/fp-specify-floating-point-behavior.md).

Poniższy przykład generuje C2099.

```c
// C2099_2.c
// compile with: /fp:strict /c
float X = 2.0 - 1.0;   // C2099
float X2 = 1.0;   // OK
```
