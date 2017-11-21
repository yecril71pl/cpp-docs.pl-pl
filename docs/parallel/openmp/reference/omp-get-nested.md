---
title: omp_get_nested | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_get_nested
dev_langs: C++
helpviewer_keywords: omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2d67008fde4d8d3093c33bfc9389004ce3b339db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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