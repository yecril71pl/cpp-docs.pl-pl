---
title: Kompilator ostrzeżenie (poziom 1) C4788 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c8a6ad1aa3ae17944b8c2a292d484d55c24d9cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051740"
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