---
title: omp_get_dynamic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d97cae8091f88c283412b36ef757b03c72f7580d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
Zwraca wartość wskazującą, czy liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli jest różna od zera, dynamiczne Dostosowywanie wątków jest włączone.  
  
## <a name="remarks"></a>Uwagi  
 Dynamiczne Dostosowywanie wątków jest określany za pomocą [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) i [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).  
  
 Aby uzyskać więcej informacji, zobacz [3.1.7 funkcja omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) przykład przy użyciu `omp_get_dynamic`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)