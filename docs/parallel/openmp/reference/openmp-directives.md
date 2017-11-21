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
ms.openlocfilehash: 21cb751c4ee4c261db1d6a4d5efda49a1445ade7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="openmp-directives"></a>OpenMP — Dyrektywy
Zawiera łącza do dyrektywy używany w interfejsie API OpenMP.  
  
 Visual C++ obsługuje następujące dyrektywy OpenMP:  
  
|Dyrektywy|Opis|  
|---------------|-----------------|  
|[niepodzielne](../../../parallel/openmp/reference/atomic.md)|Określa, że lokalizacji pamięci, która zostanie automatycznie zaktualizowany.|  
|[bariery](../../../parallel/openmp/reference/barrier.md)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymane w bariery, dopóki wszystkie wątki wykonania bariera.|  
|[krytyczne](../../../parallel/openmp/reference/critical.md)|Określa, że wykonywany jest kod tylko w jednym wątku w czasie.|  
|[Flush](../../../parallel/openmp/reference/flush-openmp.md)|Określa, że wszystkie wątki tego samego widoku pamięci dla wszystkich obiektów udostępnionych.|  
|[dla](../../../parallel/openmp/reference/for-openmp.md)|Powoduje, że pracy wykonanej dla pętli równoległego regionu do podzielony wątków.|  
|[wzorzec](../../../parallel/openmp/reference/master.md)|Określa, że tylko wzorca threadshould wykonywane części programu.|  
|[uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Określa ten kod w obszarze zrównoleglone pętli powinna zostać wykonana w takich jak loop sekwencyjnych.|  
|[równoległe](../../../parallel/openmp/reference/parallel.md)|Definiuje równoległego regionu jest kod, który zostanie wykonane przez wiele wątków jednocześnie.|  
|[sekcje](../../../parallel/openmp/reference/sections-openmp.md)|Identyfikuje sekcji kodu do podzielony wszystkie wątki.|  
|[pojedynczy](../../../parallel/openmp/reference/single.md)|Umożliwia określenie, czy mają zostać wykonane sekcji kodu w jednym wątku, niekoniecznie głównego wątku.|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Określa, czy zmienna jest prywatny do wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)