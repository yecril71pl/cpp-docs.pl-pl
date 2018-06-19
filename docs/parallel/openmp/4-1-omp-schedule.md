---
title: 4.1 OMP_SCHEDULE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e13332077a40e741f56b5602ac5197bbdfef071
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691053"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE
**OMP_SCHEDULE** dotyczą tylko **dla** i **równoległe w** dyrektywy, które mają typ harmonogramu **środowiska uruchomieniowego**. Rozmiar typu i fragmentu harmonogramu dla wszystkich takich pętli można ustawić w czasie wykonywania przez ustawienie tej zmiennej środowiskowej do dowolnego typu rozpoznanym harmonogram i opcjonalne *chunk_size*.  
  
 Dla **dla** i **równoległe w** dyrektywy mających harmonogramu typu innego niż **środowiska uruchomieniowego**, **OMP_SCHEDULE** jest ignorowana. Domyślna wartość tej zmiennej środowiskowej jest zdefiniowane w implementacji. Jeśli opcjonalny *chunk_size* jest ustawiona, wartość musi być dodatnia. Jeśli *chunk_size* nie jest ustawiona, przyjmowana jest wartość 1, z wyjątkiem w odniesieniu **statycznych** harmonogramu. Dla **statycznych** , domyślny rozmiar fragmentu ustawiono harmonogramu do obszaru iteracji pętli podzielona przez liczbę wątków stosowane do pętli.  
  
 Przykład:  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **Aby uzyskać** dyrektywy, zobacz [sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11.  
  
-   **równoległe dla** dyrektywy, zobacz [sekcji 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stronie 16.