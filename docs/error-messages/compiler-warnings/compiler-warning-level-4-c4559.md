---
title: Kompilator ostrzeżenie (poziom 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661412"
---
# <a name="compiler-warning-level-4-c4559"></a>Kompilator ostrzeżenie (poziom 4) C4559

> "*funkcja*": zmiana definicji; __declspec zyski — funkcja (*modyfikator*)

## <a name="remarks"></a>Uwagi

Funkcja została zdefiniowana ponownie lub ponownie zadeklarowany, i dodany drugi definicji lub deklaracji **__declspec** modyfikator (*modyfikator*). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```