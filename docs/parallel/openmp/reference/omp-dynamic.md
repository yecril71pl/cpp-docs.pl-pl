---
title: OMP_DYNAMIC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_DYNAMIC
dev_langs: C++
helpviewer_keywords: OMP_DYNAMIC OpenMP environment variable
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 900f3e4ddd0e9901e72ed65f12bc036d87a6956e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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