---
title: Błąd kompilatora C2246
ms.date: 11/04/2016
f1_keywords:
- C2246
helpviewer_keywords:
- C2246
ms.assetid: 4f3e4f83-21f3-4256-af96-43e0bb060311
ms.openlocfilehash: c8efb71e0a39c56628fc582421e0f24ceb9b290c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302608"
---
# <a name="compiler-error-c2246"></a>Błąd kompilatora C2246

'Identyfikator': niedozwolona statyczna składowa danych zdefiniowana lokalnie w klasie

Składowa klasy, struktury lub Unii o zakresie lokalnym jest zadeklarowana `static`.

Poniższy przykład spowoduje wygenerowanie C2246:

```
// C2246.cpp
// compile with: /c
void func( void ) {
   class A { static int i; };   // C2246  i is local to func
   static int j;   // OK
};
```