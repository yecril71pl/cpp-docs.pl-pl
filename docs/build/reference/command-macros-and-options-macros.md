---
title: Makra poleceń i makra opcji
description: Opisuje wstępnie zdefiniowane makra NMAKE dla narzędzi do kompilacji i ich opcji.
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303180"
---
# <a name="command-macros-and-options-macros"></a>Makra poleceń i makra opcji

Makra poleceń są wstępnie zdefiniowane dla produktów firmy Microsoft. Makra opcji reprezentują opcje tych produktów i są domyślnie niezdefiniowane. Oba są używane we wstępnie zdefiniowanych regułach wnioskowania i mogą być używane w blokach opisu lub regułach wnioskowania zdefiniowanych przez użytkownika. Makra poleceń można ponownie zdefiniować do reprezentowania części lub całości wiersza polecenia, w tym opcji. Makra opcji generują ciąg o wartości null, jeśli został niezdefiniowany.

|Produkt firmy Microsoft|Makro polecenia|Zdefiniowane jako|Opcje — makro|
|-----------------------|-------------------|----------------|-------------------|
|Asembler makro|**AS**|ml, iaslub ml64|**AFLAGS**|
|Kompilator języka C|**CC**|cl|**CFLAGS**|
|Kompilator C++|**CPP**|cl|**CPPFLAGS**|
|Kompilator C++|**CXX**|cl|**CXXFLAGS**|
|Kompilator zasobów|**RC**|zwrot|**RFLAGS**|

## <a name="see-also"></a>Zobacz także

[Specjalne makra NMAKE](special-nmake-macros.md)
