---
title: lastprivate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: lastprivate
dev_langs: C++
helpviewer_keywords: lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9429a54a21d58be7f2dd1667478ae653da5a8c35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 `lastprivate`ma zastosowanie do następujących dyrektyw:  
  
-   [dla](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.3 ostatnia prywatna](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [harmonogram](../../../parallel/openmp/reference/schedule.md) przykład przy użyciu `lastprivate` klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)