---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 11/04/2016
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 74caba0398fdb5cdd0f9c80270a42d2903200a5d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625808"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Pobierz systemowy komunikat o błędzie (**strerror_s**, **_wcserror_s**) lub wydrukuj komunikat o błędzie dostarczony przez użytkownika ( **_strerror_s**, **__wcserror_s**). Są to wersje [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcjach zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buforu*<br/>
Bufor do przechowywania ciągu błędu.

*numberOfElements*<br/>
Rozmiar buforu.

*errnum*<br/>
Numer błędu.

*strErrMsg*<br/>
Wiadomość dostarczona przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku niepowodzenia.

### <a name="error-condtions"></a>Warunki błędów

|*buforu*|*numberOfElements*|*strErrMsg*|Zawartość *buforu*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|Ile|Ile|n/d|
|Ile|0|Ile|nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Funkcja **strerror_s** mapuje *errnum* na ciąg komunikatu o błędzie, zwracając ciąg w *buforze*. **_strerror_s** nie przyjmuje numeru błędu; używa ona bieżącej wartości **errno** , aby określić odpowiedni komunikat. Nie **strerror_s** ani **_strerror_s** faktycznie drukuje komunikat: dla tego elementu należy wywołać funkcję wyjściową, taką jak [fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Jeśli *strErrMsg* ma **wartość null**, funkcja **_strerror_s** zwraca ciąg w *buforze* zawierającym komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które spowodowało wystąpienie błędu. Ciąg komunikatu o błędzie jest zakończony znakiem nowego wiersza ("\n"). Jeśli *strErrMsg* nie jest równa **null**, wówczas **_strerror_s** zwraca ciąg w *buforze* zawierającym (w kolejności) komunikat ciągu, dwukropek, spację, komunikat o błędzie systemu dla ostatniego wywołania biblioteki, generując błąd i wiersz polecenia Opis. Ciąg może zawierać maksymalnie 94 znaków.

Te funkcje obcinają komunikat o błędzie, jeśli jego długość przekracza *NumberOfElements* -1. Ciąg otrzymany w *buforze* jest zawsze zakończony wartością null.

Rzeczywisty numer błędu dla **_strerror_s** jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Do komunikatów o błędach systemu uzyskuje się dostęp za pomocą zmiennej [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicą komunikatów uporządkowanych według numeru błędu. **_strerror_s** uzyskuje dostęp do odpowiedniego komunikatu o błędzie przy użyciu wartości **errno** jako indeksu do zmiennej **_sys_errlist**. Wartość zmiennej [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest definiowana jako maksymalna liczba elementów w tablicy **_sys_errlist** . Aby wygenerować dokładne wyniki, należy wywołać **_strerror_s** natychmiast po powrocie procedury biblioteki z błędem. W przeciwnym razie kolejne wywołania **strerror_s** lub **_strerror_s** mogą zastąpić wartość **errno** .

**_wcserror_s** i **__wcserror_s** są odpowiednio wersjami **strerror_s** i **_strerror_s**.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli bufor ma **wartość null** lub jeśli parametr size ma wartość 0, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcje zwracają **EINVAL** i ustawiają **errno** na **EINVAL**.

**_strerror_s**, **_wcserror_s**i **__wcserror_s** nie są częścią definicji ANSI, ale zamiast niej są rozszerzeniami Microsoft. Nie należy używać ich w przypadku, gdy przenośność jest pożądana; w przypadku zgodności ze standardem ANSI zamiast tego należy użyć **strerror_s** .

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string. h >|
|**_wcserror_s**, **__wcserror_s**|\<String. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [pError](perror-wperror.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
