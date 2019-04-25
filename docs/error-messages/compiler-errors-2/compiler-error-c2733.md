---
title: Błąd kompilatora C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 26819f1928223b5fa96d275290105f32787057f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208327"
---
# <a name="compiler-error-c2733"></a>Błąd kompilatora C2733

drugie powiązanie C przeciążonej funkcji "function" niedozwolone

Więcej niż jeden przeciążonej funkcji jest zadeklarowany z powiązaniem C. Korzystając z powiązaniem C, tylko jeden formularz określonej funkcji może być zewnętrzne. Ponieważ przeciążone funkcje mają taką samą nazwę niedekorowanego, nie można używać z programów C.

Poniższy przykład spowoduje wygenerowanie C2733:

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```