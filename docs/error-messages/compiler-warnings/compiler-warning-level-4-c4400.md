---
title: Kompilator ostrzeżenie (poziom 4) C4400
ms.date: 11/04/2016
f1_keywords:
- C4400
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
ms.openlocfilehash: 61a6d3090355c9bda8aa11c041b302e4ec77ec8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557290"
---
# <a name="compiler-warning-level-4-c4400"></a>Kompilator ostrzeżenie (poziom 4) C4400

"type": kwalifikatory const/volatile dla tego typu nie są obsługiwane.

[Const](../../cpp/const-cpp.md)i [volatile](../../cpp/volatile-cpp.md)kwalifikatory nie będzie działać z zmienne typowych typów środowiska wykonawczego języka.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4400.

```
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```