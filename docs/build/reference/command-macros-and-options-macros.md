---
title: Makra poleceń i makra opcji
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: c6dad7b50d265a1460a98747665d48051078163a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272441"
---
# <a name="command-macros-and-options-macros"></a>Makra poleceń i makra opcji

Makra poleceń wstępnie zdefiniowanych dla produktów firmy Microsoft. Makra opcji reprezentują opcje do tych produktów, a domyślnie są niezdefiniowane. Obie są używane w regułach wnioskowania wstępnie zdefiniowanych i mogą być używane w bloki opisów lub reguły wnioskowania zdefiniowanych przez użytkownika. Makra poleceń można ponownie zdefiniować do reprezentowania część lub całość wiersza polecenia, włącznie z opcjami. Makra opcji wygenerować ciągu o wartości null, jeśli pozostawione niezdefiniowane.

|Produkt firmy Microsoft|Polecenie — Makro|Zdefiniowane jako|Makra opcji|
|-----------------------|-------------------|----------------|-------------------|
|Macro Assembler|**PODOBNIE JAK**|ml|**AFLAGS**|
|Basic Compiler|**BC**|bc|**BFLAGS**|
|C Compiler|**CC**|cl|**CFLAGS**|
|Kompilator C++|**CPP**|cl|**CPPFLAGS**|
|Kompilator C++|**CXX**|cl|**CXXFLAGS**|
|Kompilator zasobów|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Zobacz także

[Specjalne makra NMAKE](special-nmake-macros.md)
