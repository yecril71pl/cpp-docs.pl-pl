---
title: Błąd kompilatora C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 87b5afe2133bb737a8f9c855b0652c2f50ca27ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740523"
---
# <a name="compiler-error-c2601"></a>Błąd kompilatora C2601

"Function": definicje funkcji lokalnych są niedozwolone

Kod próbuje zdefiniować funkcję w ramach funkcji.

Lub w kodzie źródłowym może być dodatkowy nawias klamrowy przed lokalizacją błędu C2601.

Poniższy przykład generuje C2601:

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
