---
title: Kategorie regionalne
ms.date: 11/04/2016
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
ms.openlocfilehash: 434500dab0c68aa9475f54e930b91da0b1cd2fc9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749805"
---
# <a name="locale-categories"></a>Kategorie regionalne

## <a name="syntax"></a>Składnia

```
#include <locale.h>
```

## <a name="remarks"></a>Uwagi

Kategorie ustawień regionalnych są stałe manifestu, używane przez procedury lokalizacji, aby określić, która część informacji o ustawieniach regionalnych programu, który będzie używany. Ustawienia regionalne odnosi się do lokalizacji (lub Kraj/Region), dla którego można dostosować niektóre aspekty programu. Obszary zależne od ustawień regionalnych obejmują na przykład, formatowanie daty lub format wyświetlania wartości pieniężnych.

|Kategorii ustawień regionalnych|Części programu, w których to dotyczy|
|---------------------|-------------------------------|
|`LC_ALL`|Wszystkie zachowania specyficzne dla ustawień regionalnych (wszystkie kategorie)|
|`LC_COLLATE`|Zachowanie `strcoll` i `strxfrm` funkcji|
|`LC_CTYPE`|Zachowanie funkcje obsługi znaków (z wyjątkiem `isdigit`, `isxdigit`, `mbstowcs`, i `mbtowc`, które są bez zmian)|
|`LC_MAX`|Takie same jak `LC_TIME`|
|`LC_MIN`|Takie same jak `LC_ALL`|
|`LC_MONETARY`|Zwrócone przez informacje o formatowaniu walutowym `localeconv` — funkcja|
|`LC_NUMERIC`|Znak dla sformatowanych procedur danych wyjściowych dziesiętny (na przykład `printf`), procedury konwersji danych i niewalutowych informacji formatowania zwracanych przez `localeconv` — funkcja|
|`LC_TIME`|Zachowanie `strftime` — funkcja|

Zobacz [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) przykład.

## <a name="see-also"></a>Zobacz także

[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcoll, funkcje](../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
