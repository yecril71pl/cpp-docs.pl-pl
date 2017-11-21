---
title: "Makra poleceń i makra opcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 22afb96f3bc20ab769f3ef18015c721218ea7339
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="command-macros-and-options-macros"></a>Makra poleceń i makra opcji
Makra poleceń są wstępnie zdefiniowane dla produktów firmy Microsoft. Makra opcji reprezentują opcje do tych produktów i nie zdefiniowano domyślnie. Zarówno są używane w regułach wnioskowania wstępnie zdefiniowane i mogą być używane w bloki opisów lub w regułach wnioskowania zdefiniowane przez użytkownika. Makra poleceń można ponownie zdefiniować do reprezentowania części lub całości wiersza polecenia, włącznie z opcjami. Makra opcji generowania pusty ciąg, jeśli zdefiniowano po lewej.  
  
|Produkt firmy Microsoft|Makra poleceń|Zdefiniowany jako|Makra opcji|  
|-----------------------|-------------------|----------------|-------------------|  
|Macro Assembler|**JAKO**|ml|**AFLAGS**|  
|Basic Compiler|**BC**|BC|**BFLAGS**|  
|Kompilator języka C|**DW**|Cl|**CFLAGS**|  
|Kompilator C++|**CPP**|Cl|**CPPFLAGS**|  
|Kompilator C++|**CXX**|Cl|**CXXFLAGS**|  
|Kompilator zasobów|**RC**|RC|**RFLAGS**|  
  
## <a name="see-also"></a>Zobacz też  
 [Specjalne makra NMAKE](../build/special-nmake-macros.md)