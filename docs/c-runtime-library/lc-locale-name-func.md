---
title: ___lc_locale_name_func
ms.date: 11/04/2016
apiname:
- ___lc_locale_name_func
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: 17724fe5335ba54d7e32ed7851b6a35b132b1086
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639846"
---
# <a name="lclocalenamefunc"></a>___lc_locale_name_func

Wewnętrzny funkcji CRT. Pobiera nazwę ustawień regionalnych bieżącego wątku.

## <a name="syntax"></a>Składnia

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który zawiera nazwę ustawień regionalnych bieżącego wątku.

## <a name="remarks"></a>Uwagi

`___lc_locale_name_func` jest wewnętrzny funkcji CRT, który jest używany przez inne funkcje CRT, można uzyskać z magazynu lokalnego wątku CRT data bieżąca nazwa ustawień regionalnych. Te informacje są dostępne również za pomocą [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md) funkcji lub [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkcji.

Wewnętrzne funkcje CRT są specyficzne dla implementacji i może ulec zmianie z każdej wersji. Nie zalecamy ich użycie w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Zobacz też

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)