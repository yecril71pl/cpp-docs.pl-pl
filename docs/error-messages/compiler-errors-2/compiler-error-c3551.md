---
title: Błąd kompilatora C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 9dfdee155e85bd772ed1d4ce22c525f8a4c79f5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458750"
---
# <a name="compiler-error-c3551"></a>Błąd kompilatora C3551

"Oczekiwano, że późno określony zwracany typ"

Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, musisz podać późno określony typ zwracany. W poniższym przykładzie późno określony zwracany typ funkcji `myFunction` jest wskaźnikiem do tablicy czterech elementów typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Zobacz też

[auto](../../cpp/auto-cpp.md)