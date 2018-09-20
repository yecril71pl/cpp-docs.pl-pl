---
title: OpenMP, dyrektywy | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 983a71920e9e7ce390ab8c64e81886db0d459450
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389451"
---
# <a name="openmp-directives"></a>OpenMP — Dyrektywy

Zawiera łącza do informacji o dyrektywach używany w interfejsie API OpenMP.

Visual C++ obsługuje następujące dyrektywy OpenMP:

|— Dyrektywa|Opis|
|---------------|-----------------|
|[atomic](../../../parallel/openmp/reference/atomic.md)|Określa, że lokalizacji w pamięci, który będzie aktualizowany niepodzielne.|
|[barrier](../../../parallel/openmp/reference/barrier.md)|Synchronizuje wszystkie wątki w zespole; wszystkie wątki wstrzymać na barierze, dopóki wszystkie wątki wykonania barierę.|
|[critical](../../../parallel/openmp/reference/critical.md)|Określa, czy kod jest wykonywane tylko w jednym wątku w danym momencie.|
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|Określa, że wszystkie wątki mają tego samego widoku pamięci dla wszystkich obiektów udostępnionych.|
|[for](../../../parallel/openmp/reference/for-openmp.md)|Powoduje, że prace wykonane w pętli wewnątrz równoległego regionu podzielony między wątkami.|
|[master](../../../parallel/openmp/reference/master.md)|Określa, że tylko główny threadshould wykonywane części programu.|
|[Uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md)|Określa kod w ramach równoległego pętli ma być wykonany, takich jak pętla Sekwencyjna.|
|[parallel](../../../parallel/openmp/reference/parallel.md)|Definiuje równoległego regionu, czyli kodu wykonywanego przez wiele wątków jednocześnie.|
|[Sekcje](../../../parallel/openmp/reference/sections-openmp.md)|Identyfikuje sekcje kodu w celu podzielone między wszystkie wątki.|
|[single](../../../parallel/openmp/reference/single.md)|Pozwala określić, że sekcji kodu powinna zostać wykonana w jednym wątku, niekoniecznie głównego wątku.|
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|Określa, czy zmienna jest prywatnego wątku.|

## <a name="see-also"></a>Zobacz też

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)<br/>
[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)