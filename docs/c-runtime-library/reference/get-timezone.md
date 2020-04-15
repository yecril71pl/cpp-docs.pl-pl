---
title: _get_timezone
ms.date: 4/2/2020
api_name:
- _get_timezone
- _o__get_timezone
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_timezone
- get_timezone
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
ms.openlocfilehash: 94dfae1aaaddf9c545af4309d3ddc62a0bcb33f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344903"
---
# <a name="_get_timezone"></a>_get_timezone

Pobiera różnicę w sekundach między skoordynowanym czasem uniwersalnym (UTC) a czasem lokalnym.

## <a name="syntax"></a>Składnia

```C
error_t _get_timezone(
    long* seconds
);
```

### <a name="parameters"></a>Parametry

*Sekund*<br/>
Różnica w sekundach między czasem UTC a czasem lokalnym.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli zakończy się pomyślnie lub **errno** wartość, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_get_timezone** pobiera różnicę w sekundach między czasem UTC a czasem lokalnym jako liczę całkowitą. Wartość domyślna to 28 800 sekund dla czasu pacyficznego (osiem godzin za UTC).

Jeśli *wartość null* ma wartość **NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_timezone**|\<> time.h|

Aby uzyskać więcej informacji, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_tzname](get-tzname.md)<br/>
