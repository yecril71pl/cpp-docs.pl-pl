---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: d101e73f2f8d476c50b1b80b8daa7994151d43af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177836"
---
# <a name="novtable"></a>novtable

**Specyficzne dla firmy Microsoft**

Jest to **__declspec** rozszerzony atrybut.

Ten formularz **__declspec** można zastosować do dowolnej deklaracji klasy, ale powinien być stosowany tylko do czystych klas interfejsów, czyli klas, które nigdy nie będą tworzone samodzielnie. **__Declspec** uniemożliwia kompilatorowi generowanie kodu w celu zainicjowania vfptr w konstruktorach i destruktorze klasy. W wielu przypadkach powoduje to usunięcie tylko odwołań do tablic wirtualnych, które są skojarzone z klasą, a w rezultacie konsolidator usunie. Użycie tej formy **__declspec** może spowodować znaczne zmniejszenie rozmiaru kodu.

Jeśli spróbujesz utworzyć wystąpienie klasy oznaczonej jako Nostatic **, a następnie** uzyskać dostęp do elementu członkowskiego klasy, otrzymasz naruszenie dostępu (AV).

## <a name="example"></a>Przykład

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
