---
title: Błąd kompilatora C2705
description: Opis błędu kompilatora Microsoft C/C++ C2705.
ms.date: 08/25/2020
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 40d0f70ee379f5d1347b7443817713a53e097f89
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898747"
---
# <a name="compiler-error-c2705"></a>Błąd kompilatora C2705

> "*Label*": niedozwolony skok do zakresu "blok obsługi wyjątków"

## <a name="remarks"></a>Uwagi

Wykonanie przeskakuje do etykiety w **`try`** / **`catch`** bloku, **`__try`** / **`__except`** , lub **`__try`** / **`__finally`** . Kompilator nie zezwala na to zachowanie. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../cpp/exception-handling-in-visual-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2705:

```cpp
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```
