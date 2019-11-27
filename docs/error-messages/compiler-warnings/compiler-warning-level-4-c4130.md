---
title: Ostrzeżenie kompilatora (poziom 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: b55594608eccc5d1e5e764bffb73ecb3787af1e4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541593"
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

Instrukcja **if** porównuje wartość przechowywaną w wskaźniku `pc` na adres ciągu "Hello", który jest przypisywany oddzielnie za każdym razem, gdy ciąg występuje w kodzie. Instrukcja **if** nie porównuje ciągu wskazywanego przez `pc` z ciągiem "Hello".

Aby porównać ciągi, użyj funkcji `strcmp`.