---
title: 3.1.4 funkcja omp_get_thread_num | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a21a682c051daffde16b3d5cfc63fd2d679c4de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444921"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 Funkcja omp_get_thread_num

`omp_get_thread_num` Funkcja zwraca liczbę wątków, w w ramach jego zespołu wątku wykonującego funkcji. Polega liczba wątków między 0 a **omp_get_num_threads()**-1 (włącznie). Główny wątek zespołu znajduje się wątek 0.

Format jest następujący:

```
#include <omp.h>
int omp_get_thread_num(void);
```

Jeśli wywołania będą regionowi serial `omp_get_thread_num` zwraca wartość 0. Wywołane z wnętrza zagnieżdżonych równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 0.

## <a name="cross-references"></a>Odsyłacze:

- `omp_get_num_threads` funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.