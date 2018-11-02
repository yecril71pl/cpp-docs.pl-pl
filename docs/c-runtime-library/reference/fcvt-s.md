---
title: _fcvt_s
ms.date: 04/05/2018
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 51ff3c675f1f53aee9beab629b17193164a2e7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536854"
---
# <a name="fcvts"></a>_fcvt_s

Konwertuje liczbę zmiennoprzecinkową na ciąg. To jest wersja [_fcvt —](fcvt.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buffer*<br/>
Dostarczony bufor, który będzie przechowywać wynik konwersji.

*sizeInBytes*<br/>
Rozmiar buforu w bajtach.

*value*<br/>
Numer ma zostać przekonwertowany.

*Liczba*<br/>
Liczba cyfr po punkcie dziesiętnym.

*Gru*<br/>
Wskaźnik do przechowywanej położenie punktu dziesiętnego.

*sign*<br/>
Wskaźnik do wskaźnika przechowywanych logowania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu, jeśli wystąpi awaria. Kody błędów są definiowane w Errno.h. Aby uzyskać listę tych błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowy parametr, zgodnie z opisem w poniższej tabeli funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*sizeInBytes*|value|count|dec|znak|Wróć|Wartość w *buforu*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|Wszystkie|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|<=0|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**NULL**|Wszystkie|**EINVAL**|Nie jest modyfikowany.|
|Wszystkie|Wszystkie|Wszystkie|Wszystkie|Wszystkie|**NULL**|**EINVAL**|Nie jest modyfikowany.|

## <a name="security-issues"></a>Problemy dotyczące zabezpieczeń

**_fcvt_s —** może generować naruszenie zasad dostępu, jeśli *buforu* nie wskazuje na prawidłową pamięci i nie jest **NULL**.

## <a name="remarks"></a>Uwagi

**_Fcvt_s —** funkcja konwertuje liczbę zmiennoprzecinkową ciąg znaków zakończony znakiem null. *Wartość* parametr jest liczba zmiennoprzecinkowa, która ma zostać przekonwertowany. **_fcvt_s —** przechowuje cyfry *wartość* jako ciąg i dołącza znak null ('\0'). *Liczba* parametr określa liczbę cyfr, które mają być przechowywane po punkcie dziesiętnym. Nadmiarowe cyfry są zaokrąglane do *liczba* miejsc. W przypadku mniej niż *liczba* cyfr precyzji, ciąg jest dopełniana zerami.

Tylko cyfry są przechowywane w ciągu. Pozycja punkt dziesiętny i znak *wartość* można otrzymać od *gru* i *logowania* po wywołaniu. *Gru* parametr wskazuje na wartość całkowitą; tej wartości liczby całkowitej zapewnia położenie punktu dziesiętnego w odniesieniu do początku ciągu. Zero lub wartość ujemną liczbę całkowitą wskazuje punkt dziesiętny znajduje się po lewej stronie pierwsza cyfra. Parametr *logowania* wskazuje na liczbę całkowitą określającą znak *wartość*. Liczba całkowita jest ustawiona na 0, jeśli *wartość* jest dodatnia i jest ustawiona na wartość różną od zera jeśli liczba *wartość* jest ujemna.

Bufor o długości **_CVTBUFSIZE** jest wystarczająca dla dowolnego zmiennoprzecinkowe wartości.

Różnica między **_ecvt_s —** i **_fcvt_s —** znajduje się w interpretacji *liczba* parametru. **_ecvt_s —** interpretuje *liczba* jako łączna liczba cyfr w ciągu danych wyjściowych i **_fcvt_s —** interpretuje *liczba* jako liczbę cyfr po punkt dziesiętny.

W języku C++ za pomocą tej funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Ta funkcja w wersji debugowania wypełnia najpierw bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wszystkie wersje [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
