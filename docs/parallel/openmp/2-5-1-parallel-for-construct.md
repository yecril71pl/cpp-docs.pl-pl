---
title: "2.5.1 równoległe dla konstrukcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7dcd763b68a78e11c3c33bf3d750a26e88ad02ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="251-parallel-for-construct"></a>2.5.1 Konstrukcja równoległa
**Równoległe w** dyrektywa jest skrót **równoległych** region, który zawiera tylko jeden **dla** dyrektywy. Składnia **równoległe w** dyrektywy wygląda następująco:  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop  
```  
  
 Ta dyrektywa umożliwia wszystkie klauzule **równoległych** dyrektywy i **dla** dyrektywy, z wyjątkiem `nowait` klauzuli przy użyciu identyczne znaczenie i ograniczeń. Semantyka są takie same jak jawne określenie **równoległych** dyrektywy poprzedzającą **dla** dyrektywy.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **równoległe** dyrektywy, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.  
  
-   **Aby uzyskać** dyrektywy, zobacz [sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11.  
  
-   Klauzule atrybutu danych, zobacz [2.7.2 klauzule atrybutu udostępniania danych](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.