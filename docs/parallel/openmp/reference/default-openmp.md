---
title: "domyślne (OpenMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: default
dev_langs: C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: caafb7818c32dad7b21ac7a05d10f77753c1da73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="default-openmp"></a>domyślne (OpenMP)
Określa zachowanie niewystępującego w zakresie zmiennych równoległego regionu.  
  
## <a name="syntax"></a>Składnia  
  
```  
default(shared | none)  
```  
  
## <a name="remarks"></a>Uwagi  
 `shared`, które są włączone jeśli `default` klauzuli nie zostanie określony, oznacza, że dowolnej zmiennej w równoległego regionu będą traktowane jak została podana w [udostępnionego](../../../parallel/openmp/reference/shared-openmp.md) klauzuli. `none`oznacza, że wszystkie zmienne używane w równoległego regionu, które są poza zakresem z [prywatnej](../../../parallel/openmp/reference/private-openmp.md), [udostępnionego](../../../parallel/openmp/reference/shared-openmp.md), [redukcji](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), lub [lastprivate](../../../parallel/openmp/reference/lastprivate.md) klauzuli spowoduje błąd kompilatora.  
  
 `default`ma zastosowanie do następujących dyrektyw:  
  
-   [równoległe](../../../parallel/openmp/reference/parallel.md)  
  
-   [dla](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.5 domyślne](../../../parallel/openmp/2-7-2-5-default.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [prywatnej](../../../parallel/openmp/reference/private-openmp.md) przykład przy użyciu `default`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)