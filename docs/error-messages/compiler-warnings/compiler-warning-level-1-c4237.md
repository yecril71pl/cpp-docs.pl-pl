---
title: Kompilator ostrzeżenie (poziom 1) C4237 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4237
dev_langs:
- C++
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca72e4973c71655bc4a891570c6f686304d07eb0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092898"
---
# <a name="compiler-warning-level-1-c4237"></a>Kompilator ostrzeżenie (poziom 1) C4237

słowo kluczowe "— słowo kluczowe" jest jeszcze obsługiwane, ale zarezerwowane dla przyszłego użytku

Słowo kluczowe w specyfikacji C++ nie jest zaimplementowana w kompilator języka Visual C++, ale słowo kluczowe nie jest dostępna jako symbol zdefiniowany przez użytkownika.

Poniższy przykład spowoduje wygenerowanie C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```