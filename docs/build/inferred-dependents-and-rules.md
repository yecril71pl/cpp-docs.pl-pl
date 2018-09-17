---
title: Wywnioskowane zależności i reguł | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c13ae7784ff40b39642ce26fd062a1aab80f2d4c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707554"
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