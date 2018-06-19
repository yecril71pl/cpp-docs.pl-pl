---
title: strerror_s —, _strerror_s —, _wcserror_s —, __wcserror_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 362716963911a29a9b3558c387e69c4cd91b369e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415585"
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Komunikat o błędzie systemu (**strerror_s —**, **_wcserror_s —**) lub drukować komunikat dostarczone przez użytkownika (**_strerror_s —**, **__wcserror_s —** ). Są to wersje [strerror —, _strerror —, _wcserror —, \__wcserror —](strerror-strerror-wcserror-wcserror.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Bufor do przechowywania ciąg błędu.

*numberOfElements*<br/>
Rozmiar buforu.

*errnum*<br/>
Numer błędu.

*strErrMsg*<br/>
Komunikat dostarczone przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku awarii.

### <a name="error-condtions"></a>Błąd Condtions

|*buffer*|*numberOfElements*|*strErrMsg*|Zawartość *buforu*|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|wszystkie|wszystkie|n/d|
|wszystkie|0|wszystkie|Nie zmodyfikowano|

## <a name="remarks"></a>Uwagi

**Strerror_s —** funkcji mapy *errnum* na ciąg komunikat o błędzie zwraca ciąg w *buforu*. **_strerror_s —** nie przyjmuje kod błędu; używa bieżącej wartości **errno** Aby określić odpowiedni komunikat. Ani **strerror_s —** ani **_strerror_s —** faktycznie drukuje wiadomości: W tym należy wywołać funkcję dane wyjściowe takich jak [fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Jeśli *strErrMsg* jest **NULL**, **_strerror_s —** zwraca ciąg w *buforu* zawierający komunikat o błędzie systemu dla ostatniego wywołania biblioteki które spowodowało błąd. Komunikat o błędzie ciąg kończy się znakiem nowego wiersza ("\n"). Jeśli *strErrMsg* nie jest równa **NULL**, następnie **_strerror_s —** zwraca ciąg w *buforu* zawierający (w kolejności) wiadomości ciąg dwukropek, spacją, system komunikacie o błędzie ostatnim wywołaniu biblioteki produkujących błąd i znaku nowego wiersza. Ciąg komunikatu może zawierać co najwyżej 94 znaków.

Te funkcje obcięcia komunikat o błędzie, jeśli jego długość przekracza *numberOfElements* -1. Wynikowy ciąg w *buforu* jest zawsze zerem.

Numer błędu **_strerror_s —** jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicę komunikatów uporządkowanych według numer błędu. **_strerror_s —** uzyskuje dostęp do odpowiedniej komunikat przy użyciu **errno** wartość jako indeks do zmiennej **_sys_errlist —**. Wartość zmiennej [_sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest zdefiniowany jako maksymalną liczbę elementów w **_sys_errlist —** tablicy. Aby uzyskać dokładne wyniki, należy wywołać **_strerror_s —** natychmiast po procedury biblioteki zwraca błąd. W przeciwnym razie kolejne wywołania **strerror_s —** lub **_strerror_s —** mogą zastąpić **errno** wartości.

**_wcserror_s —** i **__wcserror_s —** wersji znaków dwubajtowych **strerror_s —** i **_strerror_s —** odpowiednio.

Te funkcje walidację ich parametrów. Jeśli bufor jest **NULL** lub jeśli parametr rozmiaru jest równa 0, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje zwracają **einval —** i ustaw **errno** do **einval —**.

**_strerror_s —**, **_wcserror_s —**, i **__wcserror_s —** nie są częścią definicji ANSI, ale zamiast tego są rozszerzenia Microsoft do niego. Nie używaj ich których potrzebne jest przenośność; Zgodność ANSI, użyj **strerror_s —** zamiast tego.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s —**|**strerror_s —**|**strerror_s —**|**_wcserror_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror_s —**, **_strerror_s —**|\<string.h>|
|**_wcserror_s —**, **__wcserror_s —**|\<String.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [perror](perror-wperror.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
