---
title: 3.1.6 funkcja omp_in_parallel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ba6c35d42f8497869894bd5ec95b83f0c8793f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404621"
---
# <a name="316-ompinparallel-function"></a>3.1.6 Funkcja omp_in_parallel

**Omp_in_parallel** funkcja zwraca wartość różną od zera, jeśli jest to w ramach równoległego regionu wykonywanych równolegle zakres dynamiczny; w przeciwnym razie zwraca wartość 0. Format jest następujący:

```
#include <omp.h>
int omp_in_parallel(void);
```

Ta funkcja zwraca wartość różną od zera, gdy wywoływana z w obrębie regionu wykonywanych równolegle, w tym zagnieżdżone regionów, które są serializowane.