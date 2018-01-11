---
title: Dyrektywy OpenMP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51d501139d0610d670f7d646dc985a694a5b741c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-directives"></a>OpenMP — Dyrektywy
Zawiera łącza do dyrektywy używany w interfejsie API OpenMP.  
  
 Visual C++ obsługuje następujące dyrektywy OpenMP:  
  
|Dyrektywy|Opis|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|Określa, że lokalizacji pamięci, która zostanie automatycznie zaktualizowany.|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymane w bariery, dopóki wszystkie wątki wykonania bariera.|  
|[critical](../../../parallel/openmp/reference/critical.md)|Określa, że wykonywany jest kod tylko w jednym wątku w czasie.|  
|[Flush](../../../parallel/openmp/reference/flush-openmp.md)|Określa, że wszystkie wątki tego samego widoku pamięci dla wszystkich obiektów udostępnionych.|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|Powoduje, że pracy wykonanej dla pętli równoległego regionu do podzielony wątków.|  
|[master](../../../parallel/openmp/reference/master.md)|Określa, że tylko wzorca threadshould wykonywane części programu.|  
|[uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Określa ten kod w obszarze zrównoleglone pętli powinna zostać wykonana w takich jak loop sekwencyjnych.|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|Definiuje równoległego regionu jest kod, który zostanie wykonane przez wiele wątków jednocześnie.|  
|[sekcje](../../../parallel/openmp/reference/sections-openmp.md)|Identyfikuje sekcji kodu do podzielony wszystkie wątki.|  
|[single](../../../parallel/openmp/reference/single.md)|Umożliwia określenie, czy mają zostać wykonane sekcji kodu w jednym wątku, niekoniecznie głównego wątku.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Określa, czy zmienna jest prywatny do wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)