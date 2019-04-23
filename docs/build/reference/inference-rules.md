---
title: Zasady wnioskowania
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: 0c1db9150c3b2c36c35e6802bfcd639af45bdc82
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035705"
---
# <a name="inference-rules"></a>Zasady wnioskowania

Zasady wnioskowania podać poleceń, aby zaktualizować obiektów docelowych i zależności dla celów wywnioskuj. Rozszerzenia w regule wnioskowania są zgodne z pojedynczy element docelowy i zależnych, które mają taką samą nazwę. Zasady wnioskowania są zdefiniowane przez użytkownika lub wstępnie zdefiniowanych; można ponownie zdefiniować wstępnie zdefiniowanych zasad.

Jeśli nieaktualne zależność posiada żadnych poleceń i [. SUFIKSY](dot-directives.md) zawiera rozszerzenie zależnego, używa NMAKE reguły, których rozszerzenia są zgodne z obiektu docelowego i istniejącego pliku w katalogu bieżącej lub określonej. Jeśli więcej niż jedna reguła pasuje do istniejących plików **. SUFIKSY** Określa listę, której mają zostać użyte; priorytet listy descends od lewej do prawej. Jeśli plik zależny nie istnieje, nie jest wymieniony jako element docelowy inny opis bloku reguły wnioskowania można utworzyć brakujący zależne z innego pliku o tej samej nazwie podstawowej. Jeśli blok opis elementu docelowego nie ma zależności lub polecenia, reguła wnioskowania można zaktualizować obiektu docelowego. Zasady wnioskowania można zbudować obiekt docelowy wiersza polecenia, nawet jeśli istnieje bez blokady opis. NMAKE może wywołać regułę dotyczącą wywnioskowane zależnych od ustawień lokalnych, nawet, jeśli określono jawne zależnych od ustawień lokalnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Definiowanie zasady](defining-a-rule.md)

[Zasady dotyczące trybu partii](batch-mode-rules.md)

[Wstępnie zdefiniowane zasady](predefined-rules.md)

[Zależności wywnioskowane oraz zasady](inferred-dependents-and-rules.md)

[Pierwszeństwo w zasadach wnioskowania](precedence-in-inference-rules.md)

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](nmake-reference.md)