---
title: Makra poleceń i makra opcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab8b1d61c2c4f6ae9125b8eefaf05f791f57b259
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367362"
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