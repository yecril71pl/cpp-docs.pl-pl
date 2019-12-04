---
title: Błąd kompilatora C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755034"
---
# <a name="compiler-error-c2870"></a>Błąd kompilatora C2870

"name": definicja przestrzeni nazw musi znajdować się w zakresie pliku lub bezpośrednio w innej definicji przestrzeni nazw

Przestrzeń nazw zdefiniowana `name` nieprawidłowa. Przestrzenie nazw muszą być zdefiniowane w zakresie pliku (poza wszystkimi blokami i klasami) lub bezpośrednio w innej przestrzeni nazw.

Poniższy przykład generuje C2870:

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
