---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: ccf544608bcba83af17702767562ef93d775b5a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227260"
---
# <a name="novtable"></a>novtable

**Specyficzne dla firmy Microsoft**

Jest to **`__declspec`** rozszerzony atrybut.

Ten formularz **`__declspec`** może być stosowany do dowolnej deklaracji klasy, ale powinien być stosowany tylko do czystych klas interfejsów, czyli klas, które nigdy nie zostaną utworzone samodzielnie. **`__declspec`** Uniemożliwia kompilatorowi generowanie kodu w celu zainicjowania vfptr w konstruktorach i destruktorze klasy. W wielu przypadkach powoduje to usunięcie tylko odwołań do tablic wirtualnych, które są skojarzone z klasą, a w rezultacie konsolidator usunie. Użycie tej formy **`__declspec`** może spowodować znaczny spadek rozmiaru kodu.

Jeśli spróbujesz utworzyć wystąpienie klasy oznaczonej przez, **`novtable`** a następnie uzyskać dostęp do elementu członkowskiego klasy, otrzymasz naruszenie dostępu (AV).

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

## <a name="see-also"></a>Zobacz także

[`__declspec`](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
