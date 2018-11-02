---
title: Kompilator ostrzeżenie (poziom 4) C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: c66e2243ee5eca55105de27c9824ee8ced338500
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536162"
---
# <a name="compiler-warning-level-4-c4202"></a>Kompilator ostrzeżenie (poziom 4) C4202

użyto niestandardowego rozszerzenia: "…": parametr prototypu w liście nazw jest niedozwolony

Definicja w starym stylu funkcji zawiera zmienne argumenty. Te definicje wygenerowanie błędu w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Przykład

```
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```