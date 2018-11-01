---
title: Kompilator ostrzeżenie (poziom 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: db3f4201dbf5ff925449b0924d08a43ee4283b3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651792"
---
# <a name="compiler-warning-level-4-c4629"></a>Kompilator ostrzeżenie (poziom 4) C4629

użyto dwuznaku, sekwencja znaków 'dwuznak' zinterpretowana jako token "char" (Wstaw spację między dwoma znakami, jeśli to nie mają)

W obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md), kompilator wyświetla ostrzeżenie, gdy wykryje dwuznak.

Poniższy przykład spowoduje wygenerowanie C4629:

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```