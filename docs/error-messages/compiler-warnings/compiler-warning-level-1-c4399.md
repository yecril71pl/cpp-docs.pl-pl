---
title: Kompilator ostrzeżenie (poziom 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: 56fe0f314142d873fc02136bc2c3fe65e71f4dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544069"
---
# <a name="compiler-warning-level-1-c4399"></a>Kompilator ostrzeżenie (poziom 1) C4399

> "*symbol*": symbol w procesie nie powinien być oznaczony przy użyciu atrybutu __declspec(dllimport), gdy skompilowano z opcją/CLR: pure

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Nie można zaimportować dane z obrazów natywnych lub obrazu macierzystego i konstrukcje CLR w czysty obraz. Aby rozwiązać to ostrzeżenie, skompiluj z **/CLR** (nie **/CLR: pure**) lub usunąć `__declspec(dllimport)`.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```