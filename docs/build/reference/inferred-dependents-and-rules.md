---
title: Zależności wywnioskowane oraz zasady
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: b9c3055db0cc173999e1737986166eb334dcf96c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269911"
---
# <a name="inferred-dependents-and-rules"></a>Zależności wywnioskowane oraz zasady

NMAKE zakłada wywnioskowane zależnych od ustawień lokalnych dla miejsca docelowego, jeśli istnieje reguła dotyczy wnioskowania. Reguła ma zastosowanie, jeśli:

- *toext* pasuje do rozszerzenia elementu docelowego.

- *fromext* dopasowania rozszerzenie pliku, który ma nazwę podstawową obiektu docelowego i czy istnieje w bieżącej lub określonej katalogu.

- *fromext* znajduje się w [. SUFIKSY](dot-directives.md); żadne inne *fromext* zgodną regułę ma wyższe **. SUFIKSY** priorytetu.

- Nie jawnego zależnych od ustawień lokalnych ma wyższe **. SUFIKSY** priorytetu.

Zależności wywnioskowane może spowodować nieoczekiwane działania niepożądane. Jeśli blok opis docelowy zawiera polecenia, NMAKE wykonuje tych poleceń, zamiast polecenia w regule.

## <a name="see-also"></a>Zobacz także

[Zasady wnioskowania](inference-rules.md)
