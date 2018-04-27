---
title: _fcvt_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e76888f3e4162a35cacbf9c6f2f88bf9d90e34f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fcvts"></a>_fcvt_s

Konwertuje liczba zmiennoprzecinkowa na ciąg. To jest wersja [_fcvt —](fcvt.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Podany bufor, który wstrzymuje wynik konwersji.

*sizeInBytes*<br/>
Rozmiar buforu w bajtach.

*value*<br/>
Numer do skonwertowania.

*Liczba*<br/>
Liczba cyfr po punkcie dziesiętnym.

*DEC*<br/>
Wskaźnik do składowanej położenie punktu dziesiętnego.

*sign*<br/>
Wskaźnik do wskaźnika logowania przechowywanej.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu w przypadku awarii. Kody błędów są definiowane w Errno.h. Aby uzyskać listę tych błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku nieprawidłowy parametr wymienionych w poniższej tabeli, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca **einval —**.

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*sizeInBytes*|value|count|dec|znak|Zwraca|Wartość w *buforu*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**NULL**|wszystkie|wszystkie|wszystkie|wszystkie|wszystkie|**EINVAL —**|Nie modyfikować.|
|Nie **NULL** (wskazuje prawidłowy pamięci)|<=0|wszystkie|wszystkie|wszystkie|wszystkie|**EINVAL —**|Nie modyfikować.|
|wszystkie|wszystkie|wszystkie|wszystkie|**NULL**|wszystkie|**EINVAL —**|Nie modyfikować.|
|wszystkie|wszystkie|wszystkie|wszystkie|wszystkie|**NULL**|**EINVAL —**|Nie modyfikować.|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

**_fcvt_s —** może generować naruszenia zasad dostępu, jeśli *buforu* nie wskazuje na prawidłową pamięci i nie jest **NULL**.

## <a name="remarks"></a>Uwagi

**_Fcvt_s —** funkcja konwertuje liczba zmiennoprzecinkowa na ciąg znaków zakończony znakiem null. *Wartość* parametr jest liczbie zmiennoprzecinkowej do skonwertowania. **_fcvt_s —** przechowuje cyfry *wartość* jako ciąg i dołącza znak null ('\0'). *Liczba* parametr określa liczbę cyfr po punkcie dziesiętnym przechowywania. Nadmiarowe cyfry są zaokrąglane do *liczba* miejsca. Jeśli jest dostępnych mniej niż *liczba* cyfr precyzji, ten ciąg jest uzupełniana zerami z.

Tylko cyfry są przechowywane w ciągu. Położenie punktu dziesiętnego i znak *wartość* można uzyskać od *gru* i *znak* po wywołaniu. *Gru* parametr wskazuje na wartość całkowitą; daje to wartość całkowita położenie punktu dziesiętnego względem początku ciąg. Wartość zero lub wartość ujemną całkowitą wskazuje dziesiętnego znajduje się na lewo od pierwszą. Parametr *znak* wskazuje na liczbę całkowitą określającą znak *wartość*. Liczba całkowita jest ustawiony na 0, jeśli *wartość* jest dodatnia i ma ustawioną wartość różna od zera, jeśli liczba *wartość* jest ujemna.

Bufor o długości **_CVTBUFSIZE** jest wystarczająca dla dowolnej liczby zmiennoprzecinkowe wartości.

Różnica między **_ecvt_s —** i **_fcvt_s —** jest interpretacji *liczba* parametru. **_ecvt_s —** interpretuje *liczba* jako liczba cyfr w ciągu wyjściowego i **_fcvt_s —** interpretuje *liczby* jako liczbę cyfr po separatorem dziesiętnym.

W języku C++ za pomocą tej funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążenie można wnioskować o długości buforu automatycznie, eliminując konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Wersja do debugowania tej funkcji po raz pierwszy wypełnia bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wszystkie wersje [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).

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
