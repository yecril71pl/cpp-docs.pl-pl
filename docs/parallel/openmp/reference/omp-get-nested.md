---
title: omp_get_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59900f0a1aba1cbc3bacc5cd1d8832e60aebe30b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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