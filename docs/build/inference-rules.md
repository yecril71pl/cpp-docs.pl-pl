---
title: Zasady wnioskowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2baa4bdd749e7553d052600cc9efe524ec09910d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="inference-rules"></a>Zasady wnioskowania
Zasady wnioskowania Podaj poleceń, aby zaktualizować elementów docelowych i rozpoznać zależności dla celów. Rozszerzenia w regule wnioskowania są zgodne z pojedynczym elementem docelowym i zależne, które mają taką samą nazwę podstawową. Zasady wnioskowania są zdefiniowane przez użytkownika lub wstępnie zdefiniowanej; można ponownie zdefiniować wstępnie zdefiniowanych reguł.  
  
 Jeśli nieaktualne zależności nie ma żadnych poleceń, a [. SUFIKSY](../build/dot-directives.md) zawiera rozszerzenie zależnego, używa NMAKE reguły, których rozszerzenia są zgodne z elementem docelowym i istniejące plików w katalogu bieżącego lub został określony. Jeśli więcej niż jeden reguła istniejące pliki **. SUFIKSY** lista określa, który ma zostać użyty; priorytet listy descends od lewej do prawej. Jeśli plik zależny nie istnieje i nie jest wymieniony jako element docelowy w innym bloku opis, reguła wnioskowania można utworzyć brakujący zależnych z innego pliku o tej samej nazwie podstawowej. Docelowy blok opis nie ma zależności ani poleceń, reguła wnioskowania może zaktualizować element docelowy. Zasady wnioskowania można utworzyć docelowej wiersza polecenia, nawet jeśli nie bloku opis istnieje. NMAKE może wywoływać regułę wnioskowany zależne od nawet wtedy, gdy określono jawnej zależne od.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Definiowanie zasady](../build/defining-a-rule.md)  
  
 [Zasady dotyczące trybu partii](../build/batch-mode-rules.md)  
  
 [Wstępnie zdefiniowane zasady](../build/predefined-rules.md)  
  
 [Zależności wywnioskowane oraz zasady](../build/inferred-dependents-and-rules.md)  
  
 [Pierwszeństwo w zasadach wnioskowania](../build/precedence-in-inference-rules.md)  
  
## <a name="see-also"></a>Zobacz też  
 [NMAKE — dokumentacja](../build/nmake-reference.md)