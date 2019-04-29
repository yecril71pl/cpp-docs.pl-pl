---
title: Błąd kompilatora C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366371"
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