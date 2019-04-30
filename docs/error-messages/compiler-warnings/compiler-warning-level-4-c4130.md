---
title: Kompilator ostrzeżenie (poziom 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 1b1fb72d68309a4bef56ccd844ad30d967bbadbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401321"
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