---
title: Kompilator ostrzeżenie (poziom 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: 11c6b1ad50c44ac4ad2a9d014e57efef097d9d8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524530"
---
# <a name="compiler-warning-level-4-c4208"></a>Kompilator ostrzeżenie (poziom 4) C4208

użyto niestandardowego rozszerzenia: delete [exp] - exp obliczono, ale zignorowano

Rozszerzenia Microsoft (/Ze), możesz usunąć tablicy przy użyciu wartości w nawiasach z [delete operator](../../cpp/delete-operator-cpp.md). Wartość jest ignorowana.

```
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

Wartości te są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).