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
ms.openlocfilehash: fad749b91470f7834169fe8ed734f1d627aa228e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686074"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 Funkcja omp_get_thread_num
`omp_get_thread_num` Funkcja zwraca wątku liczbę, w ramach jego zespołu wątku wykonywania funkcji. Polega liczba wątków między 0 a **omp_get_num_threads()**-1, wraz z wartościami granicznymi. Główny wątek zespołu jest wątek 0.  
  
 Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 Jeśli wywoływane z obszarem serial `omp_get_thread_num` zwraca wartość 0. Wywołane z wnętrza zagnieżdżonych równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 0.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   `omp_get_num_threads` funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.