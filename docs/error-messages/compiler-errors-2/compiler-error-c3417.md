---
title: Błąd kompilatora C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: 574af940f17c1a79472d6d20d63c9ff74d4c411e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367671"
---
# <a name="compiler-error-c3417"></a>Błąd kompilatora C3417

"członek": typy wartości nie może zawierać funkcji specjalnych elementów członkowskich zdefiniowanych przez użytkownika

Typy wartości nie może zawierać funkcji, takich jak konstruktora wystąpienia domyślnego, destruktor lub konstruktorem kopiującym.

Poniższy przykład spowoduje wygenerowanie C3517:

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```