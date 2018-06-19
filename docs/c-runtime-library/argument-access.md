---
title: Dostęp do argumentów | Dokumenty Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38d4031fcfba793a99688b6fd1cc91a3f1519989
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387096"
---
# <a name="argument-access"></a>Dostęp do argumentów

**Va_arg**, **va_end**, i **va_start —** makra zapewniają dostęp do argumentów funkcji, gdy zmienna jest liczbą argumentów. Następujące makra są zdefiniowane w \<stdarg.h > Zgodność ANSI/ISO C i w \<varargs.h > dla zgodności z V systemu UNIX.

## <a name="argument-access-macros"></a>Dostęp do argumentów makra

|Macro|Zastosowanie|
|-----------|-------------------------------|
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Pobrać argumentu z listy|
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Resetowanie wskaźnika|
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|Ustaw kursor na początku listy argumentów|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
