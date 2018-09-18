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
ms.openlocfilehash: c87dfc47f7f2554e75567a1de4ea9cb2e06eaa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028197"
---
# <a name="lastprivate"></a>lastprivate
Określa, że wersja w otaczającym kontekście zmiennej jest równa wersji prywatnej niezależnie od wątku wykonuje końcowe iteracji (konstrukcji pętli for) lub ostatnia sekcja (#pragma sekcji).  
  
## <a name="syntax"></a>Składnia  
  
```  
lastprivate(var)  
```  
  
### <a name="parameters"></a>Parametry
  
*var*<br/>
Zmienna, która jest równe prywatnej wersji niezależnie od wątku wykonuje końcowe iteracji (konstrukcji pętli for) lub ostatnia sekcja (#pragma sekcji).  
  
## <a name="remarks"></a>Uwagi  
 `lastprivate` mają zastosowanie do następujących dyrektywach:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.7.2.3 ostatnia lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [harmonogram](../../../parallel/openmp/reference/schedule.md) na przykład za pomocą `lastprivate` klauzuli.  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)