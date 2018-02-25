---
title: OMP_DYNAMIC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fcff25541921ccac9dc2e205480dc6277f620b1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ompdynamic"></a>OMP_DYNAMIC
Określa, czy OpenMP czas wykonywania można zmienić liczbę wątków w równoległego regionu.  
  
## <a name="syntax"></a>Składnia  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Uwagi  
 `OMP_DYNAMIC` Zmiennej środowiskowej może zostać przesłonięta przez [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) funkcji.  
  
 Wartość domyślna w implementacji Visual C++ standardu OpenMP to `OMP_DYNAMIC=FALSE`.  
  
 Aby uzyskać więcej informacji, zobacz [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie ustawia `OMP_DYNAMIC` zmiennej środowiskowej na wartość TRUE:  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 Następujące polecenie wyświetla bieżące ustawienie `OMP_DYNAMIC` zmiennej środowiskowej:  
  
```  
set OMP_DYNAMIC  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)