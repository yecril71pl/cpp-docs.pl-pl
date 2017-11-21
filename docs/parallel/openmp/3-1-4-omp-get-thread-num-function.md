---
title: 3.1.4 funkcja omp_get_thread_num | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9beb9e81d767a11b4ca701725ac44cc19cd3c3e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
  
-   `omp_get_num_threads`funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.