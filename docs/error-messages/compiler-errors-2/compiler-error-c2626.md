---
title: Błąd kompilatora C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 434858991c23345e2a6c174c8f323000d42b9b6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222887"
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