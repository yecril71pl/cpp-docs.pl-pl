---
title: Zasady wnioskowania
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: d3d7ca41d96d3845237b445edefff05044dacdc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170517"
---
# <a name="inference-rules"></a>Zasady wnioskowania

Reguły wnioskowania dostarczają poleceń, aby aktualizować elementy docelowe i wywnioskować zależności dla celów. Rozszerzenia w regule wnioskowania pasują do pojedynczego elementu docelowego i są zależne od tej samej nazwy bazowej. Reguły wnioskowania są zdefiniowane przez użytkownika lub wstępnie zdefiniowane; można ponownie zdefiniować wstępnie zdefiniowane reguły.

Jeśli nieaktualna zależność nie ma poleceń i jeśli [. SUFIKSy](dot-directives.md) zawierają rozszerzenie zależne, NMAKE używa reguły, której rozszerzenia są zgodne z elementem docelowym i istniejącym plikiem w bieżącym lub określonym katalogu. Jeśli więcej niż jedna reguła pasuje do istniejących plików, **. Lista SUFIKSów** określa, która z nich ma być używana; Wyświetl listę o priorytecie od lewej do prawej. Jeśli plik zależny nie istnieje i nie znajduje się na liście jako obiekt docelowy w innym bloku opisu, reguła wnioskowania może utworzyć brakujące zależne od innego pliku o tej samej nazwie. Jeśli element docelowy bloku opisu nie zawiera żadnych elementów zależnych ani poleceń, reguła wnioskowania może zaktualizować element docelowy. Reguły wnioskowania mogą kompilować obiekt docelowy wiersza polecenia, nawet jeśli nie istnieje blok opisu. NMAKE może wywoływać regułę dla wywnioskowanego elementu zależnego, nawet jeśli określono jawne zależne.

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

[Definiowanie reguły](defining-a-rule.md)

[Reguły trybu wsadowego](batch-mode-rules.md)

[Wstępnie zdefiniowane reguły](predefined-rules.md)

[Wywnioskowane zależności i reguły](inferred-dependents-and-rules.md)

[Pierwszeństwo w regułach wnioskowania](precedence-in-inference-rules.md)

## <a name="see-also"></a>Zobacz też

[NMAKE — dokumentacja](nmake-reference.md)
