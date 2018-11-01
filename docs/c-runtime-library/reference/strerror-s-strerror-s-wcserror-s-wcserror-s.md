---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 11/04/2016
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 00ff9d0df1a78d07eaa509201fb998b30396cc4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429643"
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Komunikat o błędzie systemu (**strerror_s —**, **_wcserror_s —**) lub wydrukuj komunikat o błędzie dostarczone przez użytkownika (**_strerror_s —**, **__wcserror_s —** ). Są to wersje [strerror _strerror —, _wcserror —, \__wcserror —](strerror-strerror-wcserror-wcserror.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *strErrMsg
);
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Bufor do przechowywania ciągu błędu.

*numberOfElements*<br/>
Rozmiar buforu.

*errnum*<br/>
Numer błędu.

*strErrMsg*<br/>
Wiadomości dostarczone przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu.

### <a name="error-condtions"></a>Warunki błędów

|*buffer*|*numberOfElements*|*strErrMsg*|Zawartość *buforu*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|Wszystkie|Wszystkie|n/d|
|Wszystkie|0|Wszystkie|Nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

**Strerror_s —** funkcja mapy *errnum* na ciąg komunikatu o błędzie zwraca ciąg w *buforu*. **_strerror_s —** nie przyjmuje numeru błędu; używa bieżącej wartości **errno** Aby określić odpowiedni komunikat. Ani **strerror_s —** ani **_strerror_s —** faktycznie drukują komunikatu: W tym należy wywołać funkcję danych wyjściowych, takich jak [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Jeśli *strErrMsg* jest **NULL**, **_strerror_s —** zwraca ciąg w *buforu* zawierający komunikat o błędzie systemu dla ostatniego wywołania biblioteki który wygenerował błąd. Ciąg komunikatu o błędzie jest zakończony przez znak nowego wiersza (\n). Jeśli *strErrMsg* nie jest równa **NULL**, następnie **_strerror_s —** zwraca ciąg w *buforu* zawierający (w kolejności) komunikat ciągu, dwukropek, spację, komunikat o błędzie systemu dla ostatniego wywołania biblioteki produkujących błąd i znak nowego wiersza. Ciąg wiadomości może być co najwyżej 94 znaki długości.

Te funkcje przerywają komunikat o błędzie, jeśli jego rozmiar przekracza *numberOfElements* -1. Wynikowy ciąg w *buforu* jest zawsze zakończony znakiem null.

Numer błędu dla **_strerror_s —** jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), który jest tablicą wiadomości według wielkości błędu. **_strerror_s —** uzyskuje dostęp do odpowiedniego komunikatu błędu za pomocą **errno** wartość jako indeksu do zmiennej **_sys_errlist**. Wartość zmiennej [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest zdefiniowana jako maksymalna liczba elementów w **_sys_errlist** tablicy. Aby wygenerować dokładne wyniki, należy wywołać **_strerror_s —** natychmiast, po procedurze biblioteki zwraca błąd. W przeciwnym razie, kolejne wywołania **strerror_s —** lub **_strerror_s —** może spowodować zastąpienie **errno** wartości.

**_wcserror_s —** i **__wcserror_s —** są wersjami znaków dwubajtowych **strerror_s —** i **_strerror_s —**, odpowiednio.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli bufor to **NULL** , czy rozmiar parametru to 0, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustaw **errno** do **EINVAL**.

**_strerror_s —**, **_wcserror_s —**, i **__wcserror_s —** nie są częścią definicji ANSI, ale zamiast tego są rozszerzeniami Microsoft do niej. Nie należy ich używać gdzie pożądana jest przenośność; dla zgodności ANSI, użyj **strerror_s —** zamiast tego.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje debugowania tych funkcji najpierw wypełniają bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s —**|**strerror_s —**|**strerror_s —**|**_wcserror_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror_s —**, **_strerror_s —**|\<string.h>|
|**_wcserror_s —**, **__wcserror_s —**|\<Włącz String.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [perror](perror-wperror.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
