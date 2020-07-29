---
title: Ostrzeżenie kompilatora (poziom 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: e361077a5584ba97c7efe22b99ec46567fc9ba4e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228742"
---
# <a name="compiler-warning-level-4-c4673"></a>Ostrzeżenie kompilatora (poziom 4) C4673

Zgłaszanie "Identyfikator" następujących typów nie będzie brane pod uwagę w witrynie catch

Nie można obsłużyć obiektu throw w **`catch`** bloku. Każdy typ, którego nie można obsłużyć, jest wymieniony w danych wyjściowych błędu bezpośrednio po wierszu zawierającym to ostrzeżenie. Każdy nieobsługiwany typ ma własne ostrzeżenie. Aby uzyskać więcej informacji, przeczytaj Ostrzeżenie dla każdego określonego typu.

Poniższy przykład generuje C4673:

```cpp
// C4673.cpp
// compile with: /EHsc /W4
class Base {
private:
   char * m_chr;
public:
   Base() {
      m_chr = 0;
   }

   ~Base() {
      if(m_chr)
         delete m_chr;
   }
};

class Derv : private Base {
public:
   Derv() {}
   ~Derv() {}
};

int main() {
   try {
      Derv D1;
      // delete previous line, uncomment the next line to resolve
      // Base D1;
      throw D1;   // C4673
   }

   catch(...) {}
}
```
