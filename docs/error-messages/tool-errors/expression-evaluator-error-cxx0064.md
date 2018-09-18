---
title: Błąd ewaluatora wyrażeń CXX0064 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b16133484af5a2225f79c5d293a2c8edd948bdb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025896"
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