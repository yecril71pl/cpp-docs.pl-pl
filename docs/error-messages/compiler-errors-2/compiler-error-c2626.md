---
title: Błąd kompilatora C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 339d48265bdc1f68ea4e18fadfde48fca956dd1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754748"
---
# <a name="compiler-error-c2626"></a>Błąd kompilatora C2626

"Identyfikator": prywatna lub chroniona składowa danych nie jest dozwolona w anonimowej strukturze lub Unii

Członek anonimowej struktury lub Unii musi mieć dostęp publiczny.

Poniższy przykład generuje C2626:

```cpp
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

Aby rozwiązać ten problem, Usuń wszystkie Tagi prywatne lub chronione:

```cpp
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```
