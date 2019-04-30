---
title: Kompilator ostrzeżenie (poziom 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: b6fc5708d4e2f9982ceaab57260f13e134e4d247
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406408"
---
# <a name="compiler-warning-level-1-c4806"></a>Kompilator ostrzeżenie (poziom 1) C4806

'Operacja': niebezpieczna operacja: żadna wartość typu "type" promowane do typu "type" może być równe podanej stałej

Ten komunikat ostrzega względem kodu, takich jak `b == 3`, gdzie `b` ma typ `bool`. Wspieranie reguł Przyczyna `bool` do zajęcia miejsca `int`. To jest dozwolony, ale nigdy nie może być **true**. Poniższy przykład spowoduje wygenerowanie C4806:

```
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```