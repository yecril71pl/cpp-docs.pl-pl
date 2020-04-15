---
title: ___lc_codepage_func
ms.date: 4/2/2020
api_name:
- ___lc_codepage_func
- _o____lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: 2f3eeb4611a0a41ff1782e0b162cd65d86d3ef65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351235"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

Wewnętrzna funkcja CRT. Pobiera bieżącą stronę kodową wątku.

## <a name="syntax"></a>Składnia

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Bieżąca strona kodowa wątku.

## <a name="remarks"></a>Uwagi

`___lc_codepage_func`jest wewnętrzną funkcją CRT, która jest używana przez inne funkcje CRT, aby uzyskać bieżącą stronę kodową z lokalnego magazynu wątku dla danych CRT. Te informacje są również dostępne za pomocą funkcji [_get_current_locale.](../c-runtime-library/reference/get-current-locale.md)

*Strona kodowa* jest mapowaniem kodów jedno-bajtowych lub dwu bajtowych na poszczególne znaki. Różne strony kodowe zawierają różne znaki specjalne, zazwyczaj dostosowane do języka lub grupy języków. Aby uzyskać więcej informacji na temat stron kodowych, zobacz [Strony kodowe](../c-runtime-library/code-pages.md).

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie z każdą wersją. Nie zaleca się ich używania w kodzie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz też

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
