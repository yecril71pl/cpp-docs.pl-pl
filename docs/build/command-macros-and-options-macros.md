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
ms.openlocfilehash: 7c66295a42fff6a2e6dde5205fb5d9139e6eceb6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705539"
---
# <a name="command-macros-and-options-macros"></a>Makra poleceń i makra opcji

Makra poleceń wstępnie zdefiniowanych dla produktów firmy Microsoft. Makra opcji reprezentują opcje do tych produktów, a domyślnie są niezdefiniowane. Obie są używane w regułach wnioskowania wstępnie zdefiniowanych i mogą być używane w bloki opisów lub reguły wnioskowania zdefiniowanych przez użytkownika. Makra poleceń można ponownie zdefiniować do reprezentowania część lub całość wiersza polecenia, włącznie z opcjami. Makra opcji wygenerować ciągu o wartości null, jeśli pozostawione niezdefiniowane.

|Produkt firmy Microsoft|Polecenie — Makro|Zdefiniowane jako|Makra opcji|
|-----------------------|-------------------|----------------|-------------------|
|Macro Assembler|**PODOBNIE JAK**|ml|**AFLAGS**|
|Basic Compiler|**BC**|BC|**BFLAGS**|
|Kompilator języka C|**DW**|Cl|**CFLAGS**|
|Kompilator C++|**CPP**|Cl|**CPPFLAGS**|
|Kompilator C++|**CXX**|Cl|**CXXFLAGS**|
|Kompilator zasobów|**RC**|RC|**RFLAGS**|

## <a name="see-also"></a>Zobacz też

[Specjalne makra NMAKE](../build/special-nmake-macros.md)