---
title: Dostęp do argumentów
ms.date: 04/04/2018
f1_keywords:
- c.arguments
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
ms.openlocfilehash: 8107cffa6a2da41c38b116b2e3fe36adf6ac945f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470411"
---
# <a name="argument-access"></a>Dostęp do argumentów

**Va_arg**, **va_end**, i **va_start** makra zapewniają dostęp do argumentów funkcji, gdy liczba argumentów jest zmienna. Te makra są zdefiniowane w \<stdarg.h > dla zgodności ANSI/ISO C i w \<varargs.h > dla zachowania zgodności z systemu UNIX V System.

## <a name="argument-access-macros"></a>Dostęp do argumentów makra

|Macro|Zastosowanie|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Pobrać argumentu z listy|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Resetuj wskaźnik|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Ustaw kursor na początku listy argumentów|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
