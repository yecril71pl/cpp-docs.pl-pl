---
title: Kompilator ostrzeżenie (poziom 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 28b3e49717993a3bf20c8cfec5938d698266c0f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476079"
---
# <a name="compiler-warning-level-1-c4804"></a>Kompilator ostrzeżenie (poziom 1) C4804

'Operacja': niebezpieczne użycie typu "bool" w operacji

To ostrzeżenie dotyczy sytuacji, gdy używasz `bool` zmiennej lub wartość w nieoczekiwany sposób. Na przykład C4804 jest generowany, gdy używasz operatorów, takich jak operator jednoargumentowy ujemna (**-**) lub operatorem dopełnienia (`~`). Kompilator oblicza wyrażenie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```