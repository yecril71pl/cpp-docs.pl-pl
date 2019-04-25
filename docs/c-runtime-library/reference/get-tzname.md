---
title: _get_tzname
ms.date: 10/22/2018
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
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: c173832efb866eed133a908b5f2b72266fd3798a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332043"
---
# <a name="gettzname"></a>_get_tzname

Pobiera znak ciąg reprezentujący nazwę strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST).

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
Długość ciągu *timeZoneName* łącznie z terminatorem null.

*timeZoneName*<br/>
Adres ciąg znaków reprezentujący nazwę strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST), w zależności od *indeksu*.

*sizeInBytes*<br/>
Rozmiar *timeZoneName* znaków ciągu w bajtach.

*index*<br/>
Indeks jedną z nazw dwie strefy czasowej do pobrania.

|*index*|Zawartość *timeZoneName*|*timeZoneName* wartość domyślna|
|-|-|-|
|0|Nazwa strefy czasowej|"PST"|
|1|Nazwa strefy (czas standardowy) czasu letniego|"PDT"|
|> 1 lub < 0|**errno** równa **EINVAL**|Nie zmodyfikowano|

Jeśli wartości są jawnie zmieniona w czasie wykonywania, wartości domyślne są "PST" i "(PDT)".

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli operacja się powiedzie, w przeciwnym razie **errno** wpisz wartość.

Jeśli *timeZoneName* jest **NULL**, lub *sizeInBytes* ma wartość zero lub mniejszą od zera (ale nie oba), program obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

### <a name="error-conditions"></a>Warunki błędów

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Wartość zwracana|Zawartość *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|rozmiar nazwy TZ|**NULL**|0|0 lub 1|0|Nie zmodyfikowano|
|rozmiar nazwy TZ|Wszystkie|> 0|0 lub 1|0|Nazwa TZ|
|Nie zmodyfikowano|**NULL**|> 0|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Nie zmodyfikowano|Wszystkie|zero|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Nie zmodyfikowano|Wszystkie|> 0|> 1|**EINVAL**|Nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

**_Get_tzname —** funkcja pobiera znak ciąg reprezentujący nazwę bieżącej strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST) na adres *timeZoneName* w zależności od Indeks wartości oraz rozmiar ciągu w *pReturnValue*. Jeśli *timeZoneName* jest **NULL** i *sizeInBytes* jest równy zero, rozmiar ciągu do przeprowadzenia określonej strefy czasowej i kończącą wartość null w bajtach jest zwracany w *pReturnValue*. Wartości indeksu musi być 0 dla strefy (czas standardowy) lub 1 dla letniej strefy czasowej standard; wszelkie inne wartości *indeksu* ma nieokreślony wyników.

## <a name="example"></a>Przykład

Ten przykład wywołuje **_get_tzname —** uzyskać wymagany rozmiar buforu do wyświetlenia bieżącego czasu letniego (czas standardowy) Nazwa strefy, przydziela bufor o takim rozmiarze wywołania **_get_tzname —** ponownie, aby załadować nazwy w Buffer i wyświetla go w konsoli.

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Dane wyjściowe

```Output
The current Daylight standard time zone name is PDT.
```

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
