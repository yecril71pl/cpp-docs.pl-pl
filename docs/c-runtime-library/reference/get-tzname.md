---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: 50f1f6e4320e3ef905b4eda67ba1d458a5b1df08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344875"
---
# <a name="_get_tzname"></a>_get_tzname

Pobiera reprezentację ciągu znaków nazwy strefy czasowej lub nazwy standardowej strefy czasowej (DST).

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

*pZawąkaWartość*<br/>
Długość ciągu *timeZoneName* z terminatorem zerowym.

*nazwa strefy czasowej*<br/>
Adres ciągu znaków dla reprezentacji nazwy strefy czasowej lub nazwy standardowej strefy czasowej (DST), w zależności od *indeksu*.

*rozmiarWzdjęty*<br/>
Rozmiar ciągu znaków *timeZoneName* w bajtach.

*Indeks*<br/>
Indeks jednej z dwóch nazw stref czasowych do pobrania.

|*Indeks*|Zawartość *nazwy timeZoneName*|wartość *domyślna timeZoneName*|
|-|-|-|
|0|Nazwa strefy czasowej|"PST"|
|1|Nazwa strefy czasu standardowego w okresie dziennym|"PDT"|
|> 1 lub < 0|**errno** ustawiony na **EINVAL**|nie zmodyfikowano|

Chyba że wartości są jawnie zmienione w czasie wykonywania, wartości domyślne są "PST" i "PDT" odpowiednio.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, w przeciwnym razie wartość typu **errno.**

Jeśli nazwa *systemu timeZoneName* ma **wartość NULL**lub *rozmiarWbajty* są zerowe lub mniejsze niż zero (ale nie oba), wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie Sprawdzanie poprawności [parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

### <a name="error-conditions"></a>Warunki błędu

|*pZawąkaWartość*|*nazwa strefy czasowej*|*rozmiarWzdjęty*|*Indeks*|Wartość zwracana|Zawartość *nazwy timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|rozmiar nazwy TZ|**Null**|0|0 lub 1|0|nie zmodyfikowano|
|rozmiar nazwy TZ|Wszelki|> 0|0 lub 1|0|Nazwa TZ|
|nie zmodyfikowano|**Null**|> 0|Wszelki|**Einval**|nie zmodyfikowano|
|nie zmodyfikowano|Wszelki|zero|Wszelki|**Einval**|nie zmodyfikowano|
|nie zmodyfikowano|Wszelki|> 0|> 1|**Einval**|nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Funkcja **_get_tzname** pobiera reprezentację ciągu znaku bieżącej nazwy strefy czasowej lub nazwy standardowej strefy czasu letniego (DST) na adres *timeZoneName* w zależności od wartości indeksu, wraz z rozmiarem ciągu w *pReturnValue*. Jeśli *nazwa systemu timeZoneName* ma **wartość NULL,** a *rozmiarWbajty* jest zerowy, rozmiar ciągu wymaganego do przechowywania określonej strefy czasowej i kończącej się wartości null w bajtach jest zwracany w *pReturnValue*. Wartości indeksu muszą być 0 dla standardowej strefy czasowej lub 1 dla standardowej strefy czasowej światła dziennego; wszelkie inne wartości *indeksu* mają nieokreślone wyniki.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="example"></a>Przykład

W tym przykładzie wywołuje **_get_tzname,** aby uzyskać wymagany rozmiar buforu, aby wyświetlić bieżącą nazwę standardowej strefy czasowej, przydziela bufor o tym rozmiarze, wywołuje **_get_tzname** ponownie, aby załadować nazwę w buforze i drukuje go do konsoli.

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
|**_get_tzname**|\<> time.h|

Aby uzyskać więcej informacji, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
