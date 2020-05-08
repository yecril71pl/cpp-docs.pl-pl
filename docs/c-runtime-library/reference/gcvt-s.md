---
title: _gcvt_s
ms.date: 4/2/2020
api_name:
- _gcvt_s
- _o__gcvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 83e34bffbe62bf07d2d3f9f649d12607b0e08be7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919428"
---
# <a name="_gcvt_s"></a>_gcvt_s

Konwertuje wartość zmiennoprzecinkową na ciąg. Jest to wersja [_gcvt](gcvt.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buforu*<br/>
Bufor do przechowywania wyniku konwersji.

*sizeInBytes*<br/>
Rozmiar buforu.

*wartościami*<br/>
Wartość do przekonwertowania.

*cyfry*<br/>
Liczba przechowywanych cyfr znaczących.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. Jeśli wystąpi błąd spowodowany nieprawidłowym parametrem (patrz Poniższa tabela dla nieprawidłowych wartości), procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracany jest kod błędu. Kody błędów są zdefiniowane w errno. h. Aby uzyskać listę tych błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*buforu*|*sizeInBytes*|*wartościami*|*cyfry*|Przesłać|Wartość w *buforze*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|ile|ile|ile|**EINVAL**|Nie zmodyfikowano.|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|zero|ile|ile|**EINVAL**|Nie zmodyfikowano.|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|ile|ile|>= *sizeInBytes*|**EINVAL**|Nie zmodyfikowano.|

**Problemy z zabezpieczeniami**

**_gcvt_s** może generować naruszenie zasad dostępu, jeśli *bufor* nie wskazuje prawidłowej pamięci i nie ma **wartości null**.

## <a name="remarks"></a>Uwagi

Funkcja **_gcvt_s** konwertuje *wartość* zmiennoprzecinkową na ciąg znaków (który zawiera separator dziesiętny i możliwy bajt znaku) i przechowuje ciąg w *buforze*. *bufor* powinien być wystarczająco duży, aby pomieścić przekonwertowaną wartość oraz kończący znak null, który jest dołączany automatycznie. Bufor o długości **_CVTBUFSIZE** jest wystarczający dla każdej wartości zmiennoprzecinkowej. Jeśli jest używany rozmiar bufora *cyfr* + 1, funkcja nie zastąpi końca buforu, dlatego należy podać odpowiedni bufor dla tej operacji. **_gcvt_s** próbuje utworzyć *cyfry cyfr w* formacie dziesiętnym. Jeśli nie *, generuje cyfry cyfr w* formacie wykładniczym. Końcowe zera można pominąć w konwersji.

W języku C++ korzystanie z tej funkcji jest uproszczone przez Przeciążenie szablonu; Przeciążenie może automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersja do debugowania tej funkcji najpierw wypełnia bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<STDLIB. h>|\<błąd. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
