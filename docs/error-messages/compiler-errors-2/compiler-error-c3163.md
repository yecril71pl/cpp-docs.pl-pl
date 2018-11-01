---
title: Błąd kompilatora C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: b5c689842f59a9cf999de08f10926efce0ade5ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490210"
---
# <a name="compiler-error-c3163"></a>Błąd kompilatora C3163

"konstruowania": atrybuty niespójne z poprzednią deklaracją

Atrybuty, które są stosowane do definicji w konflikcie z atrybutów, które są stosowane do deklaracji.

Jednym ze sposobów rozwiązania C3163 jest, aby wyeliminować atrybuty deklaracją do przodu. Wszelkie atrybuty w deklaracji do przodu powinna być mniejsza niż atrybuty w definicji lub co najwyżej równa się do nich.

Możliwe przyczyny błędu C3163 obejmuje Microsoft język kodu źródłowego adnotacji (SAL). Makra SAL rozwija się, chyba że Kompilowanie projektu przy użyciu **/ analyze** flagi. Program, który kompiluje nie pozostawia żadnych śladów bez / analyze może zgłosić C3163, Jeśli spróbujesz ponownie skompilować ją za pomocą / analyze — opcja. Aby uzyskać więcej informacji na temat SAL, zobacz [adnotacji SAL](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3163.

```
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>Zobacz też

[Adnotacje SAL](../../c-runtime-library/sal-annotations.md)