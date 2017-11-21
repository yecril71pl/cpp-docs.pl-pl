---
title: "udostępnione (OpenMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Shared
dev_langs: C++
helpviewer_keywords: shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 966584b3a294551560bb88430a2424f353a1e3b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="shared-openmp"></a>udostępnione (OpenMP)
Określa, że co najmniej jedną zmienną powinna być współużytkowane przez wszystkie wątki.  
  
## <a name="syntax"></a>Składnia  
  
```  
shared(var)  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `var`  
 Co więcej zmiennych do udziału. Jeśli określono więcej niż jednej zmiennej, oddziel przecinkami nazwy zmiennych.  
  
## <a name="remarks"></a>Uwagi  
 Innym sposobem udostępniają zmienne między wątków jest z [copyprivate](../../../parallel/openmp/reference/copyprivate.md) klauzuli.  
  
 `shared`ma zastosowanie do następujących dyrektyw:  
  
-   [dla](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [równoległe](../../../parallel/openmp/reference/parallel.md)  
  
-   [sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.4 udostępnionych](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [prywatnej](../../../parallel/openmp/reference/private-openmp.md) przykład przy użyciu `shared`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)