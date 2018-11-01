---
title: Punkt deklaracji w kodzie C++
ms.date: 11/04/2016
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
ms.openlocfilehash: d6cb4c3813d88c8b29fbcb2e0827805f406e6c81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560658"
---
# <a name="point-of-declaration-in-c"></a>Punkt deklaracji w kodzie C++

Nazwa jest uważany za zgłaszane natychmiast po jego deklaratora, ale przed jego Inicjator (opcjonalnie). (Aby uzyskać więcej informacji dotyczących deklaratorów, zobacz [deklaracje i definicje](declarations-and-definitions-cpp.md).)

Rozważmy następujący przykład:

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

Punkt deklaracji były *po* inicjowania, a następnie lokalnej `dVar` będzie można zainicjować 7.0, wartość zmiennej globalnej `dVar`. Jednakże, ponieważ nie jest tak, `dVar` jest ustawiana na wartość niezdefiniowana.

## <a name="see-also"></a>Zobacz także

[Zakres](../cpp/scope-visual-cpp.md)