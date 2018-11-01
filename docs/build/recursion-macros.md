---
title: Makra rekursji
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 0005a4be0422ed83816eabc7b55932a81441ae25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451262"
---
# <a name="recursion-macros"></a>Makra rekursji

Makra rekursji umożliwia wywołanie NMAKE cyklicznie. Sesje cyklicznego dziedziczyć wiersza polecenia i zmienną środowiskową makr i Tools.ini informacji. Nie dziedziczą reguły wnioskowania zdefiniowane w pliku reguł programu make lub **. SUFIKSY** i **. CENNEGO** specyfikacji. Aby przekazać makra do sesji NMAKE cykliczne, ustawić zmienną środowiskową przy użyciu zestawu przed wywołaniem cykliczne, zdefiniować makro w poleceniu wywołanie cykliczne lub zdefiniować makro w Tools.ini.

|Macro|Definicja|
|-----------|----------------|
|**WPROWADŹ**|Polecenie pierwotnie używana do wywołania NMAKE.<br /><br /> Makra $(MAKE) zapewnia pełną ścieżkę do nmake.exe.|
|**MAKEDIR —**|Bieżący katalog NMAKE została wywołana.|
|**MAKEFLAGS**|Opcje aktualnie w obiekcie. Użyj jako `/$(MAKEFLAGS)`.  Uwaga: /F nie jest włączony.|

## <a name="see-also"></a>Zobacz też

[Specjalne makra NMAKE](../build/special-nmake-macros.md)