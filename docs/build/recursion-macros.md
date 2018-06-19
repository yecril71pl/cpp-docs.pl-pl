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
ms.openlocfilehash: 2759deaff6014cbba40c97f9d627baf6a800732f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368964"
---
# <a name="recursion-macros"></a>Makra rekursji
Makra rekursji umożliwia wywołanie rekursywnie NMAKE. Sesje cykliczne dziedziczą makra zmiennych środowiskowych i z wierszem polecenia i Tools.ini informacji. Nie dziedziczą zasady zdefiniowane w pliku reguł programu make wnioskowania lub **. SUFIKSY** i **. CENNY** specyfikacji. Aby przekazać makr NMAKE cykliczne sesji, ustaw zmienną środowiskową z ZESTAWEM przed wywołanie cykliczne, zdefiniuj makra w poleceniu wywołanie cykliczne lub Definiowanie makr w Tools.ini.  
  
|Macro|Definicja|  
|-----------|----------------|  
|**WPROWADŹ**|Polecenie użyte pierwotnie do wywołania NMAKE.<br /><br /> Makro $(MAKE) zapewnia pełną ścieżkę do nmake.exe.|  
|**MAKEDIR —**|Bieżący katalog NMAKE został wywołany.|  
|**MAKEFLAGS**|Opcje aktualnie obowiązującą. Użyj jako `/$(MAKEFLAGS)`.  Uwaga: /F nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Specjalne makra NMAKE](../build/special-nmake-macros.md)