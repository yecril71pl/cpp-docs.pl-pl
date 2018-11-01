---
title: Kompilator ostrzeżenie (poziom 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: c51a4409c2a3028823462539343654b5eac365d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598175"
---
# <a name="compiler-warning-level-1-c4788"></a>Kompilator ostrzeżenie (poziom 1) C4788

'Identyfikator': identyfikator został obcięty do 'Liczba' znaków

Kompilator ogranicza maksymalną długość dozwoloną dla nazwy funkcji. Gdy kompilator generuje funclets kodu EH/SEH, wchodzi w skład nazwy polecenie funclet poprzez dodawanie przed nazwą funkcji, z tekstem, na przykład "__catch", "\__unwind", lub innego ciągu.

Wynikowa Nazwa polecenie funclet może być za długa, a kompilator będzie skrócić je i wygenerować C4788.

Aby rozwiązać tego ostrzeżenia, Skróć oryginalna nazwa funkcji. Jeśli funkcja znajduje się funkcja szablonu języka C++ lub metody, na użytek typedef część nazwy. Na przykład:

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

może być zastąpiony:

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Ostrzeżenie to pojawia się tylko w x64 kompilatora.