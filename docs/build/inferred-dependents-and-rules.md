---
title: Zależności wywnioskowane oraz zasady
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: 6d2f439a0e936b06012045c62d55b6ad76e5817d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548905"
---
# <a name="inferred-dependents-and-rules"></a>Zależności wywnioskowane oraz zasady

NMAKE zakłada wywnioskowane zależnych od ustawień lokalnych dla miejsca docelowego, jeśli istnieje reguła dotyczy wnioskowania. Reguła ma zastosowanie, jeśli:

- *toext* pasuje do rozszerzenia elementu docelowego.

- *fromext* dopasowania rozszerzenie pliku, który ma nazwę podstawową obiektu docelowego i czy istnieje w bieżącej lub określonej katalogu.

- *fromext* znajduje się w [. SUFIKSY](../build/dot-directives.md); żadne inne *fromext* zgodną regułę ma wyższe **. SUFIKSY** priorytetu.

- Nie jawnego zależnych od ustawień lokalnych ma wyższe **. SUFIKSY** priorytetu.

Zależności wywnioskowane może spowodować nieoczekiwane działania niepożądane. Jeśli blok opis docelowy zawiera polecenia, NMAKE wykonuje tych poleceń, zamiast polecenia w regule.

## <a name="see-also"></a>Zobacz też

[Zasady wnioskowania](../build/inference-rules.md)