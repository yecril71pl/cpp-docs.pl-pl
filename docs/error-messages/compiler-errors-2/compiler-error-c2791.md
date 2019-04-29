---
title: Błąd kompilatora C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: 66a111ea6fe2ca5acfbc473d19da62d9de67372a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360167"
---
# <a name="compiler-error-c2791"></a>Błąd kompilatora C2791

niedozwolone użycie "super": "class" nie ma żadnych klas bazowych

Słowo kluczowe [super](../../cpp/super.md) została użyta w kontekście funkcji składowej klasy, która nie ma żadnych klas bazowych.

Poniższy przykład spowoduje wygenerowanie C2791:

```
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```