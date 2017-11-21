---
title: OMP_SCHEDULE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_SCHEDULE
dev_langs: C++
helpviewer_keywords: OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c29ec07f9a912fb66adc391465885da8030cc466
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ompschedule"></a>OMP_SCHEDULE
Modyfikuje zachowanie [harmonogram](../../../parallel/openmp/reference/schedule.md) klauzuli podczas `schedule(runtime)` została określona w `for` lub `parallel for` dyrektywy.  
  
## <a name="syntax"></a>Składnia  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `size`(opcjonalnie)  
 Określa rozmiar iteracji. `size`musi być dodatnią liczbą całkowitą. Wartość domyślna to 1, chyba że `type` jest statyczna. Jeśli `type` jest `runtime`.  
  
 `type`  
 Rodzaj planowania:  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>Uwagi  
 Wartość domyślna w implementacji Visual C++ standardu OpenMP to `OMP_SCHEDULE=static,0`.  
  
 Aby uzyskać więcej informacji, zobacz [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie ustawia **OMP_SCHEDULE** zmiennej środowiskowej:  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 Następujące polecenie wyświetla bieżące ustawienie **OMP_SCHEDULE** zmiennej środowiskowej:  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)