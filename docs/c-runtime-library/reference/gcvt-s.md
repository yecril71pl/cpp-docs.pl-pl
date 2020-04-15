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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 10d2b9af45b78a3f5ed673bde3d37894ccb00168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345377"
---
# <a name="_gcvt_s"></a>_gcvt_s

Konwertuje wartość zmiennoprzecinkową na ciąg. Jest to wersja [_gcvt](gcvt.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Bufor do przechowywania wyniku konwersji.

*rozmiarWzdjęty*<br/>
Rozmiar buforu.

*value*<br/>
Wartość do konwersji.

*cyfry*<br/>
Liczba zapisanych cyfr znaczących.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Jeśli wystąpi błąd z powodu nieprawidłowego parametru (zobacz poniższą tabelę dla nieprawidłowych wartości), nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, zwracany jest kod błędu. Kody błędów są zdefiniowane w errno.h. Aby uzyskać listę tych błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*rozmiarWzdjęty*|*value*|*cyfry*|Zwraca|Wartość w *buforze*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**Null**|Wszelki|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano.|
|Nie **NULL** (punkty do prawidłowej pamięci)|zero|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano.|
|Nie **NULL** (punkty do prawidłowej pamięci)|Wszelki|Wszelki|>= *rozmiarWzdjęty*|**Einval**|Nie zmodyfikowano.|

**Problemy z zabezpieczeniami**

**_gcvt_s** może wygenerować naruszenie zasad dostępu, jeśli *bufor* nie wskazuje prawidłowej pamięci i nie ma **wartości NULL**.

## <a name="remarks"></a>Uwagi

Funkcja **_gcvt_s** konwertuje *wartość* zmiennoprzecinkową na ciąg znaków (który zawiera dziesiętny i możliwy bajt znaku) i przechowuje ciąg w *buforze*. *bufor* powinien być wystarczająco duży, aby pomieścić przekonwertowane wartości plus kończący znak null, który jest dołączany automatycznie. Bufor długości **_CVTBUFSIZE** jest wystarczający dla każdej wartości zmiennoprzecinkowej. Jeśli używany jest rozmiar buforu *cyfr* + 1, funkcja nie zastąpi końca buforu, więc należy podać wystarczający bufor dla tej operacji. **_gcvt_s** próbuje tworzyć *cyfry* w formacie dziesiętnym. Jeśli nie, tworzy *cyfry* w formacie wykładniczym. Końcowe zera mogą być pomijane w konwersji.

W języku C++ użycie tej funkcji jest uproszczone przez przeciążenie szablonu; przeciążenie można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersja debugowania tej funkcji najpierw wypełnia bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<>|\<> error.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
