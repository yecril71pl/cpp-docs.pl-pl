---
title: _fcvt_s
ms.date: 4/2/2020
api_name:
- _fcvt_s
- _o__fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 557a1d359c389f0eb7477aab4bf9cbb51558703a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920205"
---
# <a name="_fcvt_s"></a>_fcvt_s

Konwertuje liczbę zmiennoprzecinkową na ciąg. Jest to wersja [_fcvt](fcvt.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Parametry

*buforu*<br/>
Podany bufor, który będzie przechowywać wynik konwersji.

*sizeInBytes*<br/>
Rozmiar buforu w bajtach.

*wartościami*<br/>
Liczba do przekonwertowania.

*liczbą*<br/>
Liczba cyfr po punkcie dziesiętnym.

*dec*<br/>
Wskaźnik do przechowywanej pozycji punktu dziesiętnego.

*zapis*<br/>
Wskaźnik do przechowywanego wskaźnika podpisywania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. Wartość zwracana jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w errno. h. Aby uzyskać listę tych błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowego parametru, jak wymieniono w poniższej tabeli, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

### <a name="error-conditions"></a>Warunki błędów

|*buforu*|*sizeInBytes*|value|count|dec|znak|Przesłać|Wartość w *buforze*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|ile|ile|ile|ile|ile|**EINVAL**|Nie zmodyfikowano.|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|<= 0|ile|ile|ile|ile|**EINVAL**|Nie zmodyfikowano.|
|ile|ile|ile|ile|**NULL**|ile|**EINVAL**|Nie zmodyfikowano.|
|ile|ile|ile|ile|ile|**NULL**|**EINVAL**|Nie zmodyfikowano.|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

**_fcvt_s** może generować naruszenie zasad dostępu, jeśli *bufor* nie wskazuje prawidłowej pamięci i nie ma **wartości null**.

## <a name="remarks"></a>Uwagi

Funkcja **_fcvt_s** konwertuje liczbę zmiennoprzecinkową na ciąg znaków zakończony znakiem null. Parametr *Value* jest liczbą zmiennoprzecinkową do przekonwertowania. **_fcvt_s** przechowuje cyfry *wartości* jako ciąg i dołącza znak null (' \ 0 '). Parametr *Count* określa liczbę cyfr, które mają być przechowywane po przecinku dziesiętnym. Nadmiarowe cyfry są zaokrąglane do *liczby* miejsc. W przypadku mniej niż *liczby* cyfr dokładności, ciąg jest dopełniany zerami.

W ciągu są przechowywane tylko cyfry. Pozycja punktu dziesiętnego i znak *wartości* można uzyskać od *gru* i *podpisywać* po wywołaniu. Parametr *gru* wskazuje na wartość całkowitą; Ta wartość całkowita wskazuje położenie punktu dziesiętnego w odniesieniu do początku ciągu. Wartość zero lub ujemna liczba całkowita wskazuje, że punkt dziesiętny znajduje się po lewej stronie pierwszej cyfry. *Znak* parametru wskazuje liczbę całkowitą wskazującą znak *wartości*. Liczba całkowita jest ustawiona na 0, jeśli *wartość* jest dodatnia i jest ustawiona *na wartość różną* od zera.

Bufor o długości **_CVTBUFSIZE** jest wystarczający dla każdej wartości zmiennoprzecinkowej.

Różnica między **_ecvt_s** i **_fcvt_s** jest interpretowana parametru *Count* . **_ecvt_s** interpretuje *liczbę* jako łączną liczbę cyfr w ciągu danych wyjściowych, a **_fcvt_s** interpretuje *jako liczbę* cyfr po przecinku dziesiętnym.

W języku C++ korzystanie z tej funkcji jest uproszczone przez Przeciążenie szablonu; Przeciążenie może automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersja do debugowania tej funkcji najpierw wypełnia bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<STDLIB. h>|\<errno. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

**Biblioteki:** Wszystkie wersje [funkcji biblioteki CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
