---
title: Kompilator ostrzeżenie (poziom 4) C4130 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21d73595e41c4c83eda61fa749c9f2dc72bb14bc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038103"
---
# <a name="compiler-warning-level-4-c4130"></a>Kompilator ostrzeżenie (poziom 4) C4130

'operator': operacja logiczna na adresie ciągu stałych

Adres literału ciągu przy użyciu operatora daje nieoczekiwany kod.

Poniższy przykład spowoduje wygenerowanie C4130:

```
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

**Jeśli** instrukcji porównuje wartość przechowywana we wskaźniku `pc` adres ciąg "Hello", który jest przydzielany oddzielnie każdorazowo ciąg występuje w kodzie. **Jeśli** instrukcji nie porównuje ciąg wskazywany przez `pc` z ciągiem "Hello".

Aby porównać ciągi, należy użyć `strcmp` funkcji.