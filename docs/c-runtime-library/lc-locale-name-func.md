---
title: ___lc_locale_name_func
ms.date: 4/2/2020
api_name:
- ___lc_locale_name_func
- _o____lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: c48041c6c01e22c7771c0b5449de2cc8df1a2df0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912973"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Wewnętrzna funkcja CRT. Pobiera bieżącą nazwę ustawień regionalnych wątku.

## <a name="syntax"></a>Składnia

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który zawiera bieżącą nazwę ustawień regionalnych wątku.

## <a name="remarks"></a>Uwagi

`___lc_locale_name_func`to wewnętrzna funkcja CRT, która jest używana przez inne funkcje CRT do uzyskiwania bieżącej nazwy ustawień regionalnych z lokalnego magazynu wątków dla danych CRT. Te informacje są również dostępne przy użyciu funkcji [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) lub [setlocale _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Functions.

Wewnętrzne funkcje CRT są specyficzne dla implementacji i mogą ulec zmianie w każdej wersji. Nie zalecamy ich używania w kodzie.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz też

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
