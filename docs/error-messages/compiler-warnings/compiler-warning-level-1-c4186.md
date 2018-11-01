---
title: Kompilator ostrzeżenie (poziom 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: fa5f0c3d3d409384b7cdc3c8a9cbe884732cbf8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646579"
---
# <a name="compiler-warning-level-1-c4186"></a>Kompilator ostrzeżenie (poziom 1) C4186

\#Atrybut import "attribute" wymaga argumentów liczba; ignorowane

A `#import` atrybut ma nieprawidłową liczbę argumentów.

## <a name="example"></a>Przykład

```
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

`no_namespace` Atrybutu nie przyjmuje żadnych argumentów. **Zmień nazwę** atrybut przyjmuje tylko dwa argumenty.