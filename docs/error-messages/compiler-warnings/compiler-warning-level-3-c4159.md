---
title: Kompilator ostrzeżenie (poziom 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: e898af8f109ed23bd1784df7b39c174bbed675f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552285"
---
# <a name="compiler-warning-level-3-c4159"></a>Kompilator ostrzeżenie (poziom 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma(pop,...): ma zdjęte ze stosu poprzednio włożonego identyfikatora "*identyfikator*"

## <a name="remarks"></a>Uwagi

Zawiera kod źródłowy **wypychania** instrukcji z identyfikatorem pragmę, następuje **pop** instrukcji bez identyfikatora. W rezultacie *identyfikator* jest zdjęte ze stosu, a kolejne użycia *identyfikator* może spowodować nieoczekiwane zachowanie.

## <a name="example"></a>Przykład

Aby uniknąć tego ostrzeżenia, należy podać identyfikator w **pop** instrukcji. Na przykład:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```