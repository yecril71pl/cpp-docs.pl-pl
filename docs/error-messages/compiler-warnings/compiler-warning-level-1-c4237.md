---
title: Kompilator ostrzeżenie (poziom 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: c68e84daa2ca1aa023123203bb851e92758f9e40
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447679"
---
# <a name="compiler-warning-level-1-c4237"></a>Kompilator ostrzeżenie (poziom 1) C4237

słowo kluczowe "— słowo kluczowe" jest jeszcze obsługiwane, ale zarezerwowane dla przyszłego użytku

Słowo kluczowe w C++ specyfikacji nie jest zaimplementowany w Microsoft C++ kompilator, ale słowo kluczowe nie jest dostępna jako symbole zdefiniowane przez użytkownika.

Poniższy przykład spowoduje wygenerowanie C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```