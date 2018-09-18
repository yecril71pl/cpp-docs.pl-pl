---
title: Kompilator ostrzeżenie (poziom 4) C4400 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd22db0313d2d0ea6494908259e7d098336f6dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016198"
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