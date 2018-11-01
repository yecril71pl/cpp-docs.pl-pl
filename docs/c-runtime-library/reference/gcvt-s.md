---
title: _gcvt_s
ms.date: 04/05/2018
apiname:
- _gcvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: 168e0657150d072bbe41cd0ad6e914ca1f53e512
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554968"
---
# <a name="gcvts"></a>_gcvt_s

Konwertuje wartość zmiennoprzecinkowa do ciągu. To jest wersja [_gcvt —](gcvt.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Bufor do przechowywania wynik konwersji.

*sizeInBytes*<br/>
Rozmiar buforu.

*value*<br/>
Wartość do przekonwertowania.

*cyfry*<br/>
Liczba cyfr znaczących przechowywane.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Jeśli wystąpi błąd z powodu nieprawidłowy parametr (zobacz w poniższej tabeli nieprawidłowe wartości), zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracany jest kod błędu. Kody błędów są definiowane w Errno.h. Aby uzyskać listę tych błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*sizeInBytes*|*value*|*cyfry*|Wróć|Wartość w *buforu*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|zero|Wszystkie|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|Wszystkie|Wszystkie|>= *sizeInBytes*|**EINVAL**|Nie jest modyfikowany.|

**Problemy dotyczące zabezpieczeń**

**_gcvt_s —** może generować naruszenie zasad dostępu, jeśli *buforu* nie wskazuje na prawidłową pamięci i nie jest **NULL**.

## <a name="remarks"></a>Uwagi

**_Gcvt_s —** funkcja konwertuje liczb zmiennoprzecinkowych *wartość* na ciąg znaków, (która zawiera przecinek dziesiętny i bajtów możliwe logowania) i zapisuje ciąg w *buforu* . *Bufor* powinien być wystarczająco duży, aby pomieścić przekonwertowana wartości, a także kończący znak null, która jest dołączana automatycznie. Bufor o długości **_CVTBUFSIZE** jest wystarczająca dla dowolnego zmiennoprzecinkowe wartości. Jeśli rozmiar buforu *cyfr* + 1 jest używany, funkcja nie zastąpi koniec buforu, dlatego należy podać wystarczające buforu dla tej operacji. **_gcvt_s —** próbuje utworzyć *cyfr* cyfr w formacie dziesiętnym. Jeśli jest ona nieosiągalna, tworzy *cyfr* cyfr w notacji wykładniczej. Końcowe zera można pominąć w konwersji.

W języku C++ za pomocą tej funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Ta funkcja w wersji debugowania wypełnia najpierw bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
