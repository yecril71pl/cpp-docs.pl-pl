---
title: _get_tzname | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_tzname
apilocation:
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
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4b49aa404dda6234382ae461459dece64e5996d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451696"
---
# <a name="gettzname"></a>_get_tzname

Pobiera reprezentacji ciągu znaków nazwy strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST).

## <a name="syntax"></a>Składnia

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Długość ciągu *timeZoneName* włącznie z terminatorem null.

*timeZoneName*<br/>
Adres ciąg znaków reprezentację Nazwa strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST), w zależności od *indeksu*.

*sizeInBytes*<br/>
Rozmiar *timeZoneName* znaków ciągu w bajtach.

*index*<br/>
Indeks jednej nazwy dwie strefy czasowej do pobrania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, w przeciwnym razie **errno** wpisz wartość.

Jeśli dowolny *timeZoneName* jest **NULL**, lub *sizeInBytes* jest zerowy lub mniejsza od zera (ale nie oba), program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca **einval —**.

### <a name="error-conditions"></a>Warunki błędów

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Wartość zwracana|Zawartość *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|rozmiar TZ nazwy|**NULL**|0|0 lub 1|0|Nie zmodyfikowano|
|rozmiar TZ nazwy|wszystkie|> 0|0 lub 1|0|Nazwa TZ|
|Nie zmodyfikowano|**NULL**|> 0|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|Nie zmodyfikowano|wszystkie|zero|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|Nie zmodyfikowano|wszystkie|> 0|> 1|**EINVAL —**|Nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

**_Get_tzname —** funkcja pobiera reprezentacja ciągu znaków nazwy strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST) na adres *timeZoneName* w zależności od indeksu wartość, wraz z rozmiar ciągu w *pReturnValue*. Jeśli *timeZoneName* jest **NULL** i *sizeInBytes* jest zero, po prostu rozmiar ciągu albo czasu strefy w bajtach jest zwracany w *pReturnValue*. Wartości indeksu musi być 0 dla strefy (czas standardowy) lub 1 dla letniej strefy czasowej standard; mają inne wartości indeksu nieokreślonej wyników.

### <a name="index-values"></a>Wartości indeksu

|*index*|Zawartość *timeZoneName*|*timeZoneName* wartość domyślna|
|-------------|--------------------------------|----------------------------------|
|0|Nazwa strefy czasowej|"PST"|
|1|Nazwa strefy czasu letniego (czas standardowy)|"PDT"|
|> 1 lub < 0|**errno** ustawioną **einval —**|Nie zmodyfikowano|

Jeśli wartości są zmieniane jawnie w czasie wykonywania, wartości domyślne to "PST" i "PDT" odpowiednio.  Rozmiary te tablice znaków są regulowane przez **tzname_max —** wartość.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[TZNAME_MAX](../../c-runtime-library/tzname-max.md)<br/>
