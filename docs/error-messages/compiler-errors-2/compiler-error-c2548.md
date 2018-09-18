---
title: Błąd kompilatora C2548 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2548
dev_langs:
- C++
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4fd5087613466ecb483ad4ec28018c9321453ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050515"
---
# <a name="compiler-error-c2548"></a>Błąd kompilatora C2548

"class::member": Brak domyślnego parametru dla parametru parametru

Brak parametru w liście parametrów domyślnych. Jeśli podasz domyślnego parametru w dowolnym miejscu na liście parametrów, należy zdefiniować parametry domyślne dla wszystkich kolejnych parametrów.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2548:

```
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```