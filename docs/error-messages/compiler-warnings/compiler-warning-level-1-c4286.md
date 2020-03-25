---
title: Ostrzeżenie kompilatora (poziom 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: 27e7765c68b0bb6fb8c289260b16af1f3fe27054
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175808"
---
# <a name="compiler-warning-level-1-c4286"></a>Ostrzeżenie kompilatora (poziom 1) C4286

"type1": został przechwycony przez klasę bazową ("type2") w numerze wiersza

Określony typ wyjątku jest obsługiwany przez poprzednią procedurę obsługi. Typ drugiej wartości catch pochodzi od typu pierwszego. Wyjątki dla klasy podstawowej przechwytują wyjątki dla klasy pochodnej.

## <a name="example"></a>Przykład

```cpp
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```
