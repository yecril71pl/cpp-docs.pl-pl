---
title: ___lc_codepage_func
ms.date: 11/04/2016
api_name:
- ___lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
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
ms.openlocfilehash: dbadf8239652f5c96e7177dedd91d340e545b9fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944925"
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

`___lc_codepage_func`to wewnętrzna funkcja CRT, która jest używana przez inne funkcje CRT do uzyskiwania bieżącej strony kodowej z lokalnego magazynu wątków dla danych CRT. Te informacje są również dostępne przy użyciu funkcji [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) .

*Strona kodowa* jest mapowaniem jednobajtowych i dwubajtowych kodów do poszczególnych znaków. Różne strony kodowe zawierają różne znaki specjalne, zwykle dostosowane do języka lub grupy języków. Aby uzyskać więcej informacji na temat stron kodowych, zobacz [strony kodowe](../c-runtime-library/code-pages.md).

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie w każdej wersji. Nie zalecamy ich używania w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz także

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
