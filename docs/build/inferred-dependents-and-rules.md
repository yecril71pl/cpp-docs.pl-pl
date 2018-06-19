---
title: Wywnioskowane zależności i reguły | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aae09fd756e0eb4eab3031beb5b4cba8c4d35a40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368047"
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