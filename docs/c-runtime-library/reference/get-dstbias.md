---
title: _get_dstbias
ms.date: 4/2/2020
api_name:
- _get_dstbias
- __dstbias
- _o___dstbias
- _o__get_dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: 969b6d2dfd83a1a136fdfb3d17f8f843337b792c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345227"
---
# <a name="_get_dstbias"></a>_get_dstbias

Pobiera przesunięcie czasu letniego w sekundach.

## <a name="syntax"></a>Składnia

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>Parametry

*Sekund*<br/>
Przesunięcie w sekundach czasu letniego.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli zakończy się pomyślnie lub **errno** wartość, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_get_dstbias** pobiera liczbę sekund czasu letniego jako liczbę całkowitą. Jeśli obowiązuje czas letni, domyślne przesunięcie wynosi 3600 sekund, co oznacza liczbę sekund w ciągu jednej godziny (choć w kilku regionach obserwuje się przesunięcie dwugodzinne).

Jeśli *wartość NULL* ma wartość **NULL,** nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w programie Sprawdzanie poprawności [parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

Zaleca się użycie tej funkcji zamiast **_dstbias** makra lub przestarzałej funkcji **__dstbias**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_dstbias**|\<> time.h|

Aby uzyskać więcej informacji, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
