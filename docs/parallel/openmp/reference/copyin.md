---
title: copyin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae680b2af468b9b11a7d2de44966ad554eec0150
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="copyin"></a>kopiowanie
Umożliwia dostęp do wartości wątku głównego wątków do [threadprivate](../../../parallel/openmp/reference/threadprivate.md) zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
copyin(var)  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `var`  
 `threadprivate` Zmiennej, która zostanie zainicjowana wartość zmiennej w głównym wątku, ponieważ istnieje przed równoległych konstrukcji.  
  
## <a name="remarks"></a>Uwagi  
 `copyin` ma zastosowanie do następujących dyrektyw:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [threadprivate](../../../parallel/openmp/reference/threadprivate.md) przykład przy użyciu `copyin`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)