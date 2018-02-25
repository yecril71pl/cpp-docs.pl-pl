---
title: omp_get_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865104055fc98946c09152f328f4812af0120e64
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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