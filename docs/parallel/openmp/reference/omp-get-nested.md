---
title: omp_get_nested | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df6a3fafdb749031ae5e55a58e1e26ccad76985c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ompgetnested"></a>omp_get_nested
Zwraca wartość wskazującą, czy włączono równoległości zagnieżdżonych.  
  
## <a name="syntax"></a>Składnia  
  
```  
int omp_get_nested( );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli włączono równoległości różną od zera, zagnieżdżonych.  
  
## <a name="remarks"></a>Uwagi  
 Równoległość zagnieżdżonych zostanie określony z [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) i [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md).  
  
 Aby uzyskać więcej informacji, zobacz [3.1.10 funkcja omp_get_nested](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) przykład przy użyciu `omp_get_nested`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)