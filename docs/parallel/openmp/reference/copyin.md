---
title: copyin | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: copyin
dev_langs: C++
helpviewer_keywords: copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: af833219039a03e7e403f7e3cd10210057f3abfa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 `copyin`ma zastosowanie do następujących dyrektyw:  
  
-   [równoległe](../../../parallel/openmp/reference/parallel.md)  
  
-   [dla](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [threadprivate](../../../parallel/openmp/reference/threadprivate.md) przykład przy użyciu `copyin`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)