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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 80f02467e160e3196982c10576ad55f5487e5fc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347455"
---
# <a name="_fcvt_s"></a>_fcvt_s

Konwertuje liczbę zmiennoprzecinkową na ciąg. Jest to wersja [_fcvt](fcvt.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Dostarczony bufor, który będzie zawierać wynik konwersji.

*rozmiarWzdjęty*<br/>
Rozmiar buforu w bajtach.

*value*<br/>
Liczba do konwersji.

*Liczba*<br/>
Liczba cyfr po przecinku.

*dec*<br/>
Wskaźnik do zapisanej pozycji dziesiętnej.

*Znak*<br/>
Wskaźnik do zapisanego wskaźnika znaku.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Zwracana wartość jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w errno.h. Aby uzyskać listę tych błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowego parametru, wymienionego w poniższej tabeli, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

### <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*rozmiarWzdjęty*|value|count|dec|znak|Zwraca|Wartość w *buforze*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**Null**|Wszelki|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano.|
|Nie **NULL** (punkty do prawidłowej pamięci)|<=0|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano.|
|Wszelki|Wszelki|Wszelki|Wszelki|**Null**|Wszelki|**Einval**|Nie zmodyfikowano.|
|Wszelki|Wszelki|Wszelki|Wszelki|Wszelki|**Null**|**Einval**|Nie zmodyfikowano.|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

**_fcvt_s** może wygenerować naruszenie zasad dostępu, jeśli *bufor* nie wskazuje prawidłowej pamięci i nie ma **wartości NULL.**

## <a name="remarks"></a>Uwagi

Funkcja **_fcvt_s** konwertuje liczbę zmiennoprzecinkową na ciąg znaków zakończonych z wartością null. Parametr *value* jest numerem zmiennoprzecinkowym, który ma zostać przekonwertowany. **_fcvt_s** przechowuje cyfry *wartości* jako ciąg i dołącza znak zerowy ('\0'). Parametr *count* określa liczbę cyfr, które mają być przechowywane po przecinku dziesiętnym. Nadmiar cyfr jest zaokrąglany w celu *zliczania* miejsc. Jeśli istnieje mniej niż *liczba* cyfr precyzji, ciąg jest wyściełane zerami.

Tylko cyfry są przechowywane w ciągu. Położenie przecinka dziesiętnego i znak *wartości* można uzyskać od *dec* i *znak* po wywołaniu. Parametr *dec* wskazuje wartość całkowitą; ta wartość całkowita podaje położenie przecinka dziesiętnego względem początku ciągu. Wartość całkowita zero lub ujemna wskazuje, że przecinek dziesiętnych znajduje się po lewej stronie pierwszej cyfry. *Znak* parametru wskazuje na liczbę całkowitą wskazującą znak *wartości*. Liczba całkowita jest ustawiona na 0, jeśli *wartość* jest dodatnia i jest ustawiona na liczbę niezerową, jeśli *wartość* jest ujemna.

Bufor długości **_CVTBUFSIZE** jest wystarczający dla każdej wartości zmiennoprzecinkowej.

Różnica między **_ecvt_s** a **_fcvt_s** polega na interpretacji parametru *count.* **_ecvt_s** interpretuje *liczbę* jako całkowitą liczbę cyfr w ciągu wyjściowym, a **_fcvt_s** interpretuje *liczyć* jako liczbę cyfr po przecinku.

W języku C++ użycie tej funkcji jest uproszczone przez przeciążenie szablonu; przeciążenie można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersja debugowania tej funkcji najpierw wypełnia bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<>|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
