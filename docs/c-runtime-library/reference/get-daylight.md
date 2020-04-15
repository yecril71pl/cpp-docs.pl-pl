---
title: _get_daylight
ms.date: 4/2/2020
api_name:
- __daylight
- _get_daylight
- _o___daylight
- _o__get_daylight
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
- get_daylight
- _get_daylight
helpviewer_keywords:
- get_daylight function
- daylight saving time offset
- _get_daylight function
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
ms.openlocfilehash: 0abab77b1429b263c7e5d84a6d395f0411ebf8a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345302"
---
# <a name="_get_daylight"></a>_get_daylight

Pobiera przesunięcie czasu letniego w godzinach.

## <a name="syntax"></a>Składnia

```C
error_t _get_daylight( int* hours );
```

### <a name="parameters"></a>Parametry

*Godzin*<br/>
Przesunięcie w godzinach czasu letniego.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli zakończy się pomyślnie lub **errno** wartość, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **_get_daylight** pobiera liczbę godzin czasu letniego jako liczbę całkowitą. Jeśli obowiązuje czas letni, domyślne przesunięcie wynosi jedną godzinę (chociaż w kilku regionach obserwuje się przesunięcie dwóch godzin).

Jeśli *godziny* mają wartość **NULL**, nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

Zaleca się użycie tej funkcji zamiast **_daylight** makra lub przestarzałej funkcji **__daylight**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_daylight**|\<> time.h|

Aby uzyskać więcej informacji, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
