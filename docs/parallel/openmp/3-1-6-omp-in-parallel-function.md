---
title: 3.1.6 Funkcja omp_in_parallel
ms.date: 11/04/2016
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
ms.openlocfilehash: 2f251cb994771278c7f4e3f50f01e02126f6f88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482046"
---
# <a name="316-ompinparallel-function"></a>3.1.6 Funkcja omp_in_parallel

**Omp_in_parallel** funkcja zwraca wartość różną od zera, jeśli jest to w ramach równoległego regionu wykonywanych równolegle zakres dynamiczny; w przeciwnym razie zwraca wartość 0. Format jest następujący:

```
#include <omp.h>
int omp_in_parallel(void);
```

Ta funkcja zwraca wartość różną od zera, gdy wywoływana z w obrębie regionu wykonywanych równolegle, w tym zagnieżdżone regionów, które są serializowane.