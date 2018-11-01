---
title: Błąd kompilatora C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547962"
---
# <a name="compiler-error-c2891"></a>Błąd kompilatora C2891

"parametru": nie można przyjąć adresu parametru szablonu

Nie można przyjąć adresu parametru szablonu, chyba że jest to lvalue. Parametry typu nie są wartościami lvalue, ponieważ mają one żadnego adresu. Wartości typu bez listy parametrów szablonu, które nie są wartościami lvalue nie ma również adresu. To przykładowy kod, który powoduje błąd kompilatora C2891, ponieważ wartość przekazany jako parametr szablonu jest generowany przez kompilator kopię argumentu szablonu.

```
template <int i> int* f() { return &i; }
```

Parametry szablonu, które są wartościami lvalue, takie jak typy odwołań może mieć swój adres pobrany.

```
template <int& r> int* f() { return &r; }
```

Aby naprawić ten błąd, nie przyjąć adresu parametru szablonu, chyba że jest l-wartością.