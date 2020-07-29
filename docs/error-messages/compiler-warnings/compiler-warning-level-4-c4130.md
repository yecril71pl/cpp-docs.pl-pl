---
title: Ostrzeżenie kompilatora (poziom 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 7b2fbccfd3b124220d6e310c01adace1d3e112c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219966"
---
# <a name="compiler-warning-level-4-c4130"></a>Ostrzeżenie kompilatora (poziom 4) C4130

"operator": operacja logiczna na adresie ciągu stałej

Użycie operatora z adresem literału ciągu powoduje nieoczekiwany kod.

Poniższy przykład generuje C4130:

```cpp
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

**`if`** Instrukcja porównuje wartość przechowywaną w wskaźniku `pc` na adres ciągu "Hello", który jest przypisywany oddzielnie za każdym razem, gdy ciąg występuje w kodzie. **`if`** Instrukcja nie porównuje ciągu wskazywanego przez `pc` ciąg "Hello".

Aby porównać ciągi, użyj `strcmp` funkcji.
