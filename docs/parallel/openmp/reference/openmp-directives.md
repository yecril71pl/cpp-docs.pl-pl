---
title: Dyrektywy OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7421f397b39c6d26c2e60042b25f37277afa5fd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692197"
---
# <a name="openmp-directives"></a>OpenMP — Dyrektywy
Zawiera łącza do dyrektywy używany w interfejsie API OpenMP.  
  
 Visual C++ obsługuje następujące dyrektywy OpenMP:  
  
|Dyrektywy|Opis|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|Określa, że lokalizacji pamięci, która zostanie automatycznie zaktualizowany.|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymane w bariery, dopóki wszystkie wątki wykonania bariera.|  
|[critical](../../../parallel/openmp/reference/critical.md)|Określa, że wykonywany jest kod tylko w jednym wątku w czasie.|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|Określa, że wszystkie wątki tego samego widoku pamięci dla wszystkich obiektów udostępnionych.|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|Powoduje, że pracy wykonanej dla pętli równoległego regionu do podzielony wątków.|  
|[master](../../../parallel/openmp/reference/master.md)|Określa, że tylko wzorca threadshould wykonywane części programu.|  
|[uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Określa ten kod w obszarze zrównoleglone pętli powinna zostać wykonana w takich jak loop sekwencyjnych.|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|Definiuje równoległego regionu jest kod, który zostanie wykonane przez wiele wątków jednocześnie.|  
|[Sekcje](../../../parallel/openmp/reference/sections-openmp.md)|Identyfikuje sekcji kodu do podzielony wszystkie wątki.|  
|[single](../../../parallel/openmp/reference/single.md)|Umożliwia określenie, czy mają zostać wykonane sekcji kodu w jednym wątku, niekoniecznie głównego wątku.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Określa, czy zmienna jest prywatny do wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)