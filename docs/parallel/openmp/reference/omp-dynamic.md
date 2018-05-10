---
title: OMP_DYNAMIC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_DYNAMIC
dev_langs:
- C++
helpviewer_keywords:
- OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de4a81d861bf72943a67356577da37c36df63f69
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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