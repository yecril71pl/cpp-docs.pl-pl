---
title: _ecvt_s
ms.date: 4/2/2020
api_name:
- _ecvt_s
- _o__ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: e33840e772de770e0f05ae45d2c2d4bec7e09939
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348048"
---
# <a name="_ecvt_s"></a>_ecvt_s

Konwertuje **podwójną** liczbę na ciąg. Jest to wersja [_ecvt](ecvt.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*_Buffer*<br/>
Wypełniony wskaźnikiem do ciągu cyfr, wynik konwersji.

*_SizeInBytes*<br/>
Rozmiar buforu w bajtach.

*_value*<br/>
Liczba do konwersji.

*_count*<br/>
Liczba zapisanych cyfr.

*_Dec*<br/>
Przechowywana pozycja dziesiętna.

*_Sign*<br/>
Znak przekonwertowanego numeru.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Zwracana wartość jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w errno.h. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowego parametru, wymienionego w poniższej tabeli, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość EINVAL**.

### <a name="error-conditions"></a>Warunki błędu

|*_Buffer*|*_SizeInBytes*|_value|_count|_Dec|_Sign|Wartość zwracana|Wartość w *buforze*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**Null**|Wszelki|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano.|
|Nie **NULL** (punkty do prawidłowej pamięci)|<=0|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|Nie zmodyfikowano.|
|Wszelki|Wszelki|Wszelki|Wszelki|**Null**|Wszelki|**Einval**|Nie zmodyfikowano.|
|Wszelki|Wszelki|Wszelki|Wszelki|Wszelki|**Null**|**Einval**|Nie zmodyfikowano.|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

**_ecvt_s** może wygenerować naruszenie zasad dostępu, jeśli *bufor* nie wskazuje prawidłowej pamięci i nie ma **wartości NULL.**

## <a name="remarks"></a>Uwagi

Funkcja **_ecvt_s** konwertuje liczbę zmiennoprzecinkową na ciąg znaków. Parametr *_Value* jest numerem zmiennoprzecinkowym, który ma zostać przekonwertowany. Ta funkcja przechowuje się, aby *zliczać* cyfry *_Value* jako ciąg i dołącza znak zerowy ('\0'). Jeśli liczba cyfr w *_Value* przekracza *_Count,* cyfra niskiego rzędu jest zaokrąglana. Jeśli jest mniej niż *cyfry,* ciąg jest wyściełane zerami.

Tylko cyfry są przechowywane w ciągu. Położenie przecinka dziesiętnego i znak *_Value* można uzyskać z *_Dec* i *_Sign* po wywołaniu. Parametr *_Dec* wskazuje wartość całkowitą, podając pozycję przecinka dziesiętnego względem początku ciągu. Wartość całkowita 0 lub ujemna wskazuje, że przecinek dziesiętny znajduje się po lewej stronie pierwszej cyfry. Parametr *_Sign* wskazuje liczbę całkowitą wskazującą znak przekonwertowanego numeru. Jeśli wartość całkowita wynosi 0, liczba ta jest dodatnia. W przeciwnym razie liczba jest ujemna.

Bufor długości **_CVTBUFSIZE** jest wystarczający dla każdej wartości zmiennoprzecinkowej.

Różnica między **_ecvt_s** a **_fcvt_s** polega na interpretacji parametru *_Count.* **_ecvt_s** interpretuje *_Count* jako całkowitą liczbę cyfr w ciągu wyjściowym, podczas gdy **_fcvt_s** interpretuje *_Count* jako liczbę cyfr po przecinku.

W języku C++ użycie tej funkcji jest uproszczone przez przeciążenie szablonu; przeciążenie można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersja debugowania tej funkcji najpierw wypełnia bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<>|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
