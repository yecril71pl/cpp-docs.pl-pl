---
title: Kompilator ostrzeżenie (poziom 4) C4673
ms.date: 11/04/2016
f1_keywords:
- C4673
helpviewer_keywords:
- C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
ms.openlocfilehash: ceaa5cd647dfb527713613b9ce3b5cd81a780fd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657733"
---
# <a name="compiler-warning-level-4-c4673"></a>Kompilator ostrzeżenie (poziom 4) C4673

Zgłaszanie 'Identyfikator' następujących typów, nie zostanie uwzględniony w obszarze przechwytywania

Obiekt throw nie mogą być obsługiwane w **catch** bloku. Każdy typ, który nie może być obsługiwane znajduje się w dane wyjściowe błędu zaraz po wierszu, zawierające to ostrzeżenie. Każdy nieobsługiwany typ ma swój własny ostrzeżenie. Przeczytaj ostrzeżenia dla każdego określonego typu, aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4673:

```
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