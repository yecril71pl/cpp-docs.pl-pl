---
title: Błąd kompilatora C2801 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d57ee5bf5f5152ef55852c9f9b829bc4a1d17d41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040638"
---
# <a name="compiler-error-c2801"></a>Błąd kompilatora C2801

"operator operator" musi być niestatycznego elementu członkowskiego

Następujące operatory mogą być przeciążone tylko jako niestatycznych elementów członkowskich:

- Przypisania `=`

- Dostęp do składowej klasy `->`

- Subscripting `[]`

- Wywołanie funkcji `()`

Możliwe przyczyny C2801:

- Przeciążony operator nie jest klasy, struktury lub Unii.

- Przeciążony operator jest zadeklarowany jako `static`.

- Poniższy przykład spowoduje wygenerowanie C2801:

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```