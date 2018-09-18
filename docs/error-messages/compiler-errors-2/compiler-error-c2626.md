---
title: Błąd kompilatora C2626 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2626
dev_langs:
- C++
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9929da1f0cf9ffd9c70048017fdef1d854c1fcc9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074685"
---
# <a name="compiler-error-c2626"></a>Błąd kompilatora C2626

'Identyfikator': element członkowski danych prywatnych lub chronionych nie jest dozwolona w anonimowej struktury lub Unii

Składowej anonimowej struktury lub Unii musi mieć dostęp publiczny.

Poniższy przykład spowoduje wygenerowanie C2626:

```
// C2626.cpp
int main() {
   union {
   protected:
      int j;     // C2626, j is protected
   private:
      int k;     // C2626, k is private
   };
}
```

Aby rozwiązać ten problem, usuń wszelkie tagi prywatnych lub chronionych:

```
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```