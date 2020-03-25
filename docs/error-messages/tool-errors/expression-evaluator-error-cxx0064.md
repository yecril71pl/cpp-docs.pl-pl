---
title: Błąd CXX0064 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: f763754299ed9257fb909b49a7a19c6f3ad58681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184466"
---
# <a name="expression-evaluator-error-cxx0064"></a>Błąd CXX0064 programu Expression Evaluator

nie można ustawić punktu przerwania dla powiązanej wirtualnej funkcji członkowskiej

Punkt przerwania został ustawiony dla wirtualnej funkcji składowej za pomocą wskaźnika do obiektu, takiego jak:

```
pClass->vfunc( int );
```

Punkt przerwania można ustawić dla funkcji wirtualnej, wprowadzając klasę, taką jak:

```
Class::vfunc( int );
```

Ten błąd jest identyczny z CAN0064.
