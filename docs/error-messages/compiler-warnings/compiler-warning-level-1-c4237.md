---
title: Ostrzeżenie kompilatora (poziom 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: e53c4632f8bfc9764f6ab1e124582bda273d945e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624903"
---
# <a name="compiler-warning-level-1-c4237"></a>Ostrzeżenie kompilatora (poziom 1) C4237

słowo kluczowe "Keyword" nie jest jeszcze obsługiwane, ale zarezerwowane do użytku w przyszłości

Słowo kluczowe w C++ specyfikacji nie jest zaimplementowane w kompilatorze firmy C++ Microsoft, ale słowo kluczowe nie jest dostępne jako symbol zdefiniowany przez użytkownika.

Poniższy przykład generuje C4237:

```cpp
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```