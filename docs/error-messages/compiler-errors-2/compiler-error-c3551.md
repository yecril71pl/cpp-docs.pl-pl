---
title: Błąd kompilatora C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 48b378eb734c5830bedbf417d99d34955e2e6d0f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023272"
---
# <a name="compiler-error-c3551"></a>Błąd kompilatora C3551

"Oczekiwano, że późno określony zwracany typ"

Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, musisz podać późno określony typ zwracany. W poniższym przykładzie późno określony zwracany typ funkcji `myFunction` jest wskaźnikiem do tablicy czterech elementów typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Zobacz także

[auto](../../cpp/auto-cpp.md)