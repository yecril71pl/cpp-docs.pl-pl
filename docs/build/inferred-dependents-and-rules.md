---
title: "Wywnioskowane zależności i reguły | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe7c49607f466d8fd1d333883414b24d7837432b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="inferred-dependents-and-rules"></a>Zależności wywnioskowane oraz zasady
Jeśli istnieje reguła dotyczy wnioskowania NMAKE przyjęto założenie wnioskowany zależne od elementu docelowego. Reguła ma zastosowanie, jeśli:  
  
-   *toext* rozszerzenie elementu docelowego.  
  
-   *fromext* dopasowań rozszerzenie pliku, który ma element docelowy nazwie podstawowej i że istnieje w bieżącym katalogu lub określony.  
  
-   *fromext* w [. SUFIKSY](../build/dot-directives.md); żadnych innych *fromext* w Reguła dopasowywania ma wyższy **. SUFIKSY** priorytet.  
  
-   Jawne zależnych ma wyższy **. SUFIKSY** priorytet.  
  
 Zależności wywnioskowane może spowodować nieoczekiwane efekty uboczne. Jeśli element docelowy opis blok zawiera polecenia, NMAKE wykonuje tych poleceń, zamiast polecenia w regule.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady wnioskowania](../build/inference-rules.md)