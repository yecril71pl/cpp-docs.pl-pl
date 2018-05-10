---
title: lastprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aaf80e3061877c42154ab9ee5ccd30f47f17135
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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