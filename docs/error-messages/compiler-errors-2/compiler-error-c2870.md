---
title: Błąd kompilatora C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: f61281da23e46236e7fce496a4d89086e5d6c0ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546379"
---
# <a name="compiler-error-c2870"></a>Błąd kompilatora C2870

"name": definicja przestrzeni nazw musi znajdować się w zakresie pliku albo natychmiast w innej definicji przestrzeni nazw

Definicja przestrzeni nazw `name` niepoprawnie. Przestrzenie nazw musi być zdefiniowany w zakresie pliku (na zewnątrz wszystkich bloków i klasy) lub bezpośrednio w innej przestrzeni nazw.

Poniższy przykład spowoduje wygenerowanie C2870:

```
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```