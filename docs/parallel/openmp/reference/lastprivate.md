---
title: lastprivate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7945edb879d81bb50753619c1206b9da575dbcda
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="lastprivate"></a>lastprivate
Określa, że wersja otaczającym kontekście zmiennej jest taki sam, niezależnie od wątku wykonuje końcowego iteracji (konstrukcji pętli for) lub ostatniej sekcji (#pragma sekcje) wersji prywatnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
lastprivate(var)  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `var`  
 Zmienna, która jest równe wersji prywatnej niezależnie od wątku wykonuje końcowego iteracji (konstrukcji pętli for) lub ostatniej sekcji (#pragma sekcji).  
  
## <a name="remarks"></a>Uwagi  
 `lastprivate` ma zastosowanie do następujących dyrektyw:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.3 ostatnia prywatna](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [harmonogram](../../../parallel/openmp/reference/schedule.md) przykład przy użyciu `lastprivate` klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)