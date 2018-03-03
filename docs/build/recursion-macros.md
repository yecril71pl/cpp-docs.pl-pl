---
title: Makra rekursji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8d9ef7f194151fb3259712759d0c29ed157d564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recursion-macros"></a>Makra rekursji
Makra rekursji umożliwia wywołanie rekursywnie NMAKE. Sesje cykliczne dziedziczą makra zmiennych środowiskowych i z wierszem polecenia i Tools.ini informacji. Nie dziedziczą zasady zdefiniowane w pliku reguł programu make wnioskowania lub **. SUFIKSY** i **. CENNY** specyfikacji. Aby przekazać makr NMAKE cykliczne sesji, ustaw zmienną środowiskową z ZESTAWEM przed wywołanie cykliczne, zdefiniuj makra w poleceniu wywołanie cykliczne lub Definiowanie makr w Tools.ini.  
  
|Makra|Definicja|  
|-----------|----------------|  
|**WPROWADŹ**|Polecenie użyte pierwotnie do wywołania NMAKE.<br /><br /> Makro $(MAKE) zapewnia pełną ścieżkę do nmake.exe.|  
|**MAKEDIR —**|Bieżący katalog NMAKE został wywołany.|  
|**MAKEFLAGS**|Opcje aktualnie obowiązującą. Użyj jako `/$(MAKEFLAGS)`.  Uwaga: /F nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Specjalne makra NMAKE](../build/special-nmake-macros.md)