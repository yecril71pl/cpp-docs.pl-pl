---
title: _ecvt_s
ms.date: 04/05/2018
apiname:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: 0123c618eb5ba614bd8e5b5b3f1f4b0aff539c4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435584"
---
# <a name="ecvts"></a>_ecvt_s

Konwertuje **double** liczb na ciąg. To jest wersja [_ecvt —](ecvt.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>Parametry

*Właściwość _Buffer*<br/>
Wypełniony wskaźnik na ciąg cyfr, wynik konwersji.

*_SizeInBytes*<br/>
Rozmiar buforu w bajtach.

*_Wartość*<br/>
Numer ma zostać przekonwertowany.

*_Count*<br/>
Liczba cyfr przechowywane.

*_Dec*<br/>
Przechowywane położenie punktu dziesiętnego.

*Zalo_guj*<br/>
Znak przekonwertowany numer.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu, jeśli wystąpi awaria. Kody błędów są definiowane w Errno.h. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowy parametr, zgodnie z opisem w poniższej tabeli funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

### <a name="error-conditions"></a>Warunki błędów

|*Właściwość _Buffer*|*_SizeInBytes*|_Wartość|_Count|_Dec|Zalo_guj|Wartość zwracana|Wartość w *buforu*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|<=0|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**NULL**|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**NULL**|**EINVAL**|Nie jest modyfikowany.|

## <a name="security-issues"></a>Problemy dotyczące zabezpieczeń

**_ecvt_s —** może generować naruszenie zasad dostępu, jeśli *buforu* nie wskazuje na prawidłową pamięci i nie jest **NULL**.

## <a name="remarks"></a>Uwagi

**_Ecvt_s —** funkcja konwertuje liczbę zmiennoprzecinkową ciąg znaków. *_Wartość* parametr jest liczba zmiennoprzecinkowa, która ma zostać przekonwertowany. Ta funkcja przechowuje maksymalnie *liczba* cyfr *_wartość* jako ciąg i dołącza znak null ('\0'). Jeśli liczba cyfr w *_wartość* przekracza *_Count*, cyfra niskiego rzędu jest zaokrąglana. W przypadku mniej niż *liczba* cyfry, ciąg jest dopełniana zerami.

Tylko cyfry są przechowywane w ciągu. Pozycja punkt dziesiętny i znak *_wartość* można otrzymać od *_Dec* i *_podpisz* po wywołaniu. *_Dec* parametr wskazuje wartość całkowitą, dzięki czemu położenie punktu dziesiętnego w odniesieniu do początku ciągu. Wartość 0 ani ujemna liczba całkowita wskazuje, punkt dziesiętny znajduje się po lewej stronie pierwsza cyfra. *_Podpisz* parametr wskazuje na liczbę całkowitą, która określa znak przekonwertowany numer. Jeśli wartość całkowitą ma wartość 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.

Bufor o długości **_CVTBUFSIZE** jest wystarczająca dla dowolnej wartości zmiennoprzecinkowych.

Różnica między **_ecvt_s —** i **_fcvt_s —** znajduje się w interpretacji *_Count* parametru. **_ecvt_s —** interpretuje *_Count* jako łączna liczba cyfr w ciągu wyjściowego, natomiast **_fcvt_s —** interpretuje *_Count* jako liczbę cyfr po punktu dziesiętnego.

W języku C++ za pomocą tej funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Ta funkcja w wersji debugowania wypełnia najpierw bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
