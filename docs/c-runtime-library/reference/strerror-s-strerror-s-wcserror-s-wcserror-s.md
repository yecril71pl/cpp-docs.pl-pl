---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 4/2/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ef712ecb6236513d169b4a8836b1365b0aca0633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337367"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Pobierz komunikat o błędzie systemu **(strerror_s**, **_wcserror_s**) lub wydrukuj komunikat o błędzie dostarczony przez użytkownika (**_strerror_s**, **__wcserror_s**). Są to wersje [strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) z ulepszeniami zabezpieczeń, jak opisano w funkcji zabezpieczeń w [CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Bufor do przechowywania ciągu błędu.

*liczbaOfElements*<br/>
Rozmiar bufora.

*errnum ( errnum )*<br/>
Numer błędu.

*strErrMsg*<br/>
Komunikat dostarczony przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, kod błędu w przypadku awarii.

### <a name="error-condtions"></a>Kondcje błędów

|*Buforu*|*liczbaOfElements*|*strErrMsg*|Zawartość *buforu*|
|--------------|------------------------|-----------------|--------------------------|
|**Null**|Wszelki|Wszelki|Nie dotyczy|
|Wszelki|0|Wszelki|nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

Funkcja **strerror_s** *mapuje errnum* do ciągu komunikatu o błędzie, zwracając ciąg w *buforze*. **_strerror_s** nie przyjmuje numeru błędu; używa bieżącej wartości **errno** do określenia odpowiedniego komunikatu. Ani **strerror_s,** ani **_strerror_s** faktycznie drukuje wiadomość: W tym celu należy wywołać funkcję wyjściową, taką jak [fprintf:](fprintf-fprintf-l-fwprintf-fwprintf-l.md)

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Jeśli *strErrMsg* ma **wartość NULL**, **_strerror_s** zwraca ciąg w *buforze* zawierający komunikat o błędzie systemowego dla ostatniego wywołania biblioteki, który spowodował błąd. Ciąg komunikatu o błędzie jest kończony przez znak nowego typu ('\n'). Jeśli *strErrMsg* nie jest równa **NULL**, a następnie **_strerror_s** zwraca ciąg w *buforze* zawierający (w kolejności) komunikat ciąg, dwukropek, spacja, komunikat o błędzie systemu dla ostatniego wywołania biblioteki powodujący błąd i znak nowego. Wiadomość ciągu może mieć co najwyżej 94 znaki.

Te funkcje obcinają komunikat o błędzie, jeśli jego długość przekracza *numberOfElements* -1. Wynikowy ciąg w *buforze* jest zawsze zakończony z wartością null.

Rzeczywisty numer błędu dla **_strerror_s** jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicą komunikatów uporządkowanych według numeru błędu. **_strerror_s** uzyskuje dostęp do odpowiedniego komunikatu o błędzie przy użyciu wartości **errno** jako indeksu do zmiennej **_sys_errlist**. Wartość [zmiennej _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest definiowana jako maksymalna liczba elementów w tablicy **_sys_errlist.** Aby uzyskać dokładne wyniki, wywołaj **_strerror_s** natychmiast po powrocie rutynowych biblioteki z błędem. W przeciwnym razie kolejne wywołania **strerror_s** lub **_strerror_s** mogą zastąpić wartość **errno.**

**_wcserror_s** i **__wcserror_s** są odpowiednio szerokoznakowymi wersjami **strerror_s** i **_strerror_s.**

Te funkcje sprawdzają ich parametry. Jeśli bufor ma **wartość NULL** lub parametr size wynosi 0, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje zwracają **EINVAL** i ustawić **errno** na **EINVAL**.

**_strerror_s**, **_wcserror_s**i **__wcserror_s** nie są częścią definicji ANSI, ale zamiast tego są rozszerzeniami firmy Microsoft. Nie używaj ich tam, gdzie wymagana jest przenośność; aby uzyskać zgodność z ANSI, użyj **strerror_s.**

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string.h>|
|**_wcserror_s** **, __wcserror_s**|\<string.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [perror](perror-wperror.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
