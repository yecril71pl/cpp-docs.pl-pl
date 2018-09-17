---
title: Makra rekursji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a5f327686a522608b6eec9fd7106cbab00028
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702043"
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