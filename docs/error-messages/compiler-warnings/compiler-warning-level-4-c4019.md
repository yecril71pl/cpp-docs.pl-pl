---
title: Kompilator ostrzeżenie (poziom 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: d2bfec799b8b2981914b76839e51b7a0d09b30ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401478"
---
# <a name="compiler-warning-level-4-c4019"></a>Kompilator ostrzeżenie (poziom 4) C4019

Instrukcja pusta w globalnym zakresie

Średnik w zakresie globalnym nie jest poprzedzony przez instrukcję.

To ostrzeżenie, mogą zostać rozwiązane, jeśli usuniesz dodatkowe średnikami.

## <a name="example"></a>Przykład

```
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```