---
title: _get_tzname
ms.date: 10/22/2018
api_name:
- _get_tzname
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
ms.openlocfilehash: 9f86a4997c328e86597e3bad8a7f7a3a5f5f50b6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955625"
---
# <a name="_get_tzname"></a>_get_tzname

Pobiera ciąg znaków reprezentujący nazwę strefy czasowej lub nazwę czasową standardowej strefy czasowej (DST).

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
Długość ciągu dla elementu *timeZoneName* uwzględniającego terminator o wartości null.

*timeZoneName*<br/>
Adres ciągu znaków dla reprezentacji nazwy strefy czasowej lub standardowej nazwy strefy czasowej (DST), w zależności od *indeksu*.

*sizeInBytes*<br/>
Rozmiar ciągu znaków *timeZoneName* w bajtach.

*index*<br/>
Indeks jednej z dwóch nazw stref czasowych do pobrania.

|*index*|Zawartość elementu *timeZoneName*|wartość domyślna *timeZoneName*|
|-|-|-|
|0|Nazwa strefy czasowej|KOPIA|
|1|Nazwa standardowej strefy czasowej|PDT|
|> 1 lub < 0|**errno** ustawiony na **EINVAL**|nie zmodyfikowano|

O ile wartości nie są jawnie zmieniane w czasie wykonywania, wartości domyślne to "PST" i "PDT".

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, w przeciwnym razie wartość typu **errno** .

Jeśli wartość *timeZoneName* ma **wartość null**lub *sizeInBytes* jest równa zero lub mniejsza od zera (ale nie obu), wywoływana jest procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

### <a name="error-conditions"></a>Warunki błędów

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Wartość zwracana|Zawartość elementu *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|rozmiar nazwy programu $|**NULL**|0|0 lub 1|0|nie zmodyfikowano|
|rozmiar nazwy programu $|Ile|> 0|0 lub 1|0|Nazwa $|
|nie zmodyfikowano|**NULL**|> 0|Ile|**EINVAL**|nie zmodyfikowano|
|nie zmodyfikowano|Ile|zero|Ile|**EINVAL**|nie zmodyfikowano|
|nie zmodyfikowano|Ile|> 0|> 1|**EINVAL**|nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Funkcja **_get_tzname** Pobiera ciąg znaków reprezentujący bieżącą nazwę strefy czasowej lub nazwę standardowego czasu letniego (DST) do *adresu strefy* czasowej w zależności od wartości indeksu, wraz z rozmiarem ciągu w *pReturnValue*. Jeśli *timeZoneName* ma **wartość null** , a *sizeInBytes* ma wartość zero, rozmiar ciągu wymaganego do przechowywania określonej strefy czasowej i zakończenie wartości null w bajtach jest zwracany w *pReturnValue*. Wartości indeksu muszą mieć wartość 0 dla standardowej strefy czasowej lub 1 dla standardowej strefy czasowej (letnia). wszystkie inne wartości *indeksu* mają nieokreślony wynik.

## <a name="example"></a>Przykład

Ten przykład wywołuje **_get_tzname** , aby uzyskać wymagany rozmiar buforu, aby wyświetlić bieżącą nazwę czasu standardowego czasu letniego, przydziela bufor tego rozmiaru i ponownie wywołuje **_get_tzname** w celu załadowania nazwy w buforze, a następnie drukuje ją do konsoli programu.

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

Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
