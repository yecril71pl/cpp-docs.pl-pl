---
title: Błąd CXX0064 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 71e4e3e87b33849e6b487b79268ebc9574c2e5a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299481"
---
# <a name="expression-evaluator-error-cxx0064"></a>Błąd CXX0064 programu Expression Evaluator

Nie można ustawić punktu przerwania w powiązanej wirtualnej funkcji składowej

Punkt przerwania ustawiono funkcja wirtualna elementu członkowskiego, za pomocą wskaźnika do obiektu, takie jak:

```
pClass->vfunc( int );
```

Dla wirtualnej funkcji można ustawić punktu przerwania, wprowadzając klasy, takie jak:

```
Class::vfunc( int );
```

Ten błąd jest taka sama jak CAN0064.