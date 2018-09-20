---
title: bariera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c220106d62bf65505c9c5b48085a9ee3e67fe0cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415034"
---
# <a name="barrier"></a>ograniczenie

Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymać na barierze, dopóki wszystkie wątki wykonania barierę.

## <a name="syntax"></a>Składnia

```
#pragma omp barrier
```

## <a name="remarks"></a>Uwagi

`barrier` Dyrektywy nie obsługuje żadnych klauzule OpenMP.

Aby uzyskać więcej informacji, zobacz [2.6.3 dyrektywa określająca bariery](../../../parallel/openmp/2-6-3-barrier-directive.md).

## <a name="example"></a>Przykład

Przykład sposobu użycia `barrier`, zobacz [wzorca](../../../parallel/openmp/reference/master.md).

## <a name="see-also"></a>Zobacz też

[Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)