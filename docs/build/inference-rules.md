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
ms.openlocfilehash: ed45e5ad61ea1cc50172cd86716b357baa64fa39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724389"
---
# <a name="inference-rules"></a>Zasady wnioskowania

Zasady wnioskowania podać poleceń, aby zaktualizować obiektów docelowych i zależności dla celów wywnioskuj. Rozszerzenia w regule wnioskowania są zgodne z pojedynczy element docelowy i zależnych, które mają taką samą nazwę. Zasady wnioskowania są zdefiniowane przez użytkownika lub wstępnie zdefiniowanych; można ponownie zdefiniować wstępnie zdefiniowanych zasad.

Jeśli nieaktualne zależność posiada żadnych poleceń i [. SUFIKSY](../build/dot-directives.md) zawiera rozszerzenie zależnego, używa NMAKE reguły, których rozszerzenia są zgodne z obiektu docelowego i istniejącego pliku w katalogu bieżącej lub określonej. Jeśli więcej niż jedna reguła pasuje do istniejących plików **. SUFIKSY** Określa listę, której mają zostać użyte; priorytet listy descends od lewej do prawej. Jeśli plik zależny nie istnieje, nie jest wymieniony jako element docelowy inny opis bloku reguły wnioskowania można utworzyć brakujący zależne z innego pliku o tej samej nazwie podstawowej. Jeśli blok opis elementu docelowego nie ma zależności lub polecenia, reguła wnioskowania można zaktualizować obiektu docelowego. Zasady wnioskowania można zbudować obiekt docelowy wiersza polecenia, nawet jeśli istnieje bez blokady opis. NMAKE może wywołać regułę dotyczącą wywnioskowane zależnych od ustawień lokalnych, nawet, jeśli określono jawne zależnych od ustawień lokalnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Definiowanie zasady](../build/defining-a-rule.md)

[Zasady dotyczące trybu partii](../build/batch-mode-rules.md)

[Wstępnie zdefiniowane zasady](../build/predefined-rules.md)

[Zależności wywnioskowane oraz zasady](../build/inferred-dependents-and-rules.md)

[Pierwszeństwo w zasadach wnioskowania](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>Zobacz też

[NMAKE — dokumentacja](../build/nmake-reference.md)