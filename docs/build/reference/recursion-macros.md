---
title: Makra rekursji
description: Opisuje makra używane do wywoływania NMAKE w sesjach cyklicznych.
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303152"
---
# <a name="recursion-macros"></a>Makra rekursji

Używaj makr rekursji do wywoływania NMAKE rekursywnie. Sesje cykliczne dziedziczą makra w wierszu polecenia i zmienne środowiskowe oraz informacje Tools. ini. Nie dziedziczą one reguł wnioskowania zdefiniowanych przez plik reguł programu make ani specyfikacji `.SUFFIXES` i `.PRECIOUS`. Istnieją trzy sposoby przekazywania makr do cyklicznej sesji NMAKE: Ustaw zmienną środowiskową z :::no-loc text="SET"::: poleceniem przed wywołaniem cyklicznym. Zdefiniuj makro w poleceniu dla wywołania cyklicznego. Lub Zdefiniuj makro w pliku Tools. ini.

|Macro|Definicja|
|-----------|----------------|
|**MAKE**|Polecenie użyte pierwotnie do wywołania NMAKE.<br /><br /> Makro `$(MAKE)` zapewnia pełną ścieżkę do NMAKE. exe.|
|**MAKEDIR**|Bieżący katalog po wywołaniu NMAKE.|
|**MAKEFLAGS**|Obecnie obowiązujące opcje. Użyj jako `/$(MAKEFLAGS)`. Opcja **/f** nie jest uwzględniona.|

## <a name="see-also"></a>Zobacz także

[Specjalne makra NMAKE](special-nmake-macros.md)
