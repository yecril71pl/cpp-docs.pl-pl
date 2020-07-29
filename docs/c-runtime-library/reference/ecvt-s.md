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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: e76ebd065d323a9ae501ce6a7a5790389c7d5dad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234214"
---
# <a name="_ecvt_s"></a>_ecvt_s

Konwertuje **`double`** liczbę na ciąg. Jest to wersja [_ecvt](ecvt.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wypełnienie wskaźnikiem do ciągu cyfr, wynik konwersji.

*_SizeInBytes*<br/>
Rozmiar buforu w bajtach.

*_Value*<br/>
Liczba do przekonwertowania.

*_Count*<br/>
Liczba przechowywanych cyfr.

*_Dec*<br/>
Przechowywana pozycja punktu dziesiętnego.

*_Sign*<br/>
Znak przekonwertowanego numeru.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. Wartość zwracana jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w errno. h. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowego parametru, jak wymieniono w poniższej tabeli, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

### <a name="error-conditions"></a>Warunki błędów

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Sign|Wartość zwracana|Wartość w *buforze*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**NULL**|dowolny|dowolny|dowolny|dowolny|dowolny|**EINVAL**|Nie zmodyfikowano.|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|<= 0|dowolny|dowolny|dowolny|dowolny|**EINVAL**|Nie zmodyfikowano.|
|dowolny|dowolny|dowolny|dowolny|**NULL**|dowolny|**EINVAL**|Nie zmodyfikowano.|
|dowolny|dowolny|dowolny|dowolny|dowolny|**NULL**|**EINVAL**|Nie zmodyfikowano.|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

**_ecvt_s** może generować naruszenie zasad dostępu, jeśli *bufor* nie wskazuje prawidłowej pamięci i nie ma **wartości null**.

## <a name="remarks"></a>Uwagi

Funkcja **_ecvt_s** konwertuje liczbę zmiennoprzecinkową na ciąg znaków. Parametr *_Value* jest liczbą zmiennoprzecinkową do przekonwertowania. Ta funkcja przechowuje maksymalnie *liczbę* cyfr *_Value* jako ciąg i dołącza znak null (' \ 0 '). Jeśli liczba cyfr w *_Value* przekracza *_Count*, zostanie zaokrąglona cyfra z niską kolejnością. Jeśli jest mniej niż *Liczba* cyfr, ciąg jest dopełniany zerami.

W ciągu są przechowywane tylko cyfry. Pozycja punktu dziesiętnego i znak *_Value* można uzyskać z *_Dec* i *_Sign* po wywołaniu. Parametr *_Dec* wskazuje liczbę całkowitą określającą położenie przecinka dziesiętnego w odniesieniu do początku ciągu. Wartość 0 lub ujemna liczba całkowita wskazuje, że punkt dziesiętny znajduje się po lewej stronie pierwszej cyfry. Parametr *_Sign* wskazuje liczbę całkowitą wskazującą znak przekonwertowanego numeru. Jeśli wartość całkowita to 0, liczba jest dodatnia. W przeciwnym razie liczba jest ujemna.

Bufor o długości **_CVTBUFSIZE** jest wystarczający dla każdej wartości zmiennoprzecinkowej.

Różnica między **_ecvt_s** i **_fcvt_s** jest interpretacją parametru *_Count* . **_ecvt_s** interpretuje *_Count* jako łączną liczbę cyfr w ciągu danych wyjściowych, a **_fcvt_s** interpretuje *_Count* jako liczbę cyfr po przecinku dziesiętnym.

W języku C++ korzystanie z tej funkcji jest uproszczone przez Przeciążenie szablonu; Przeciążenie może automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersja do debugowania tej funkcji najpierw wypełnia bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
