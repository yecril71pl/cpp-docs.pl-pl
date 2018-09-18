---
title: Błąd kompilatora C2891 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86d81662cb02fa3c8f6af75009daf4dab9b70196
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016562"
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