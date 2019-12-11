---
title: Ostrzeżenie kompilatora (poziomy 1 i 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: f614373e1b96de2c8167d7981c0a87a4e1c58435
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991228"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Ostrzeżenie kompilatora (poziomy 1 i 4) C4112

wiersz \#wymaga liczby całkowitej z zakresu od 1 do cyfry

Dyrektywa [#line](../../preprocessor/hash-line-directive-c-cpp.md) określa parametr liczby całkowitej, który jest poza dozwolonym zakresem.

Jeśli określony parametr jest mniejszy niż 1, licznik wiersza zostanie zresetowany do 1. Jeśli określony parametr jest większy niż *Liczba*, który jest limitem zdefiniowanym przez kompilator, licznik wiersza nie jest zmieniany. Jest to ostrzeżenie poziomu 1 w obszarze zgodność ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenie poziomu 4 z rozszerzeniami Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)).

Poniższy przykład generuje C4112:

```cpp
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```
