---
title: _snprintf_s —, _snprintf_s_l —, _snwprintf_s —, _snwprintf_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _snprintf_s
- _snprintf_s_l
- _snwprintf_s
- _snwprintf_s_l
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
apitype: DLLExport
f1_keywords:
- _snwprintf_s_l
- _sntprintf_s_l
- snprintf_s_l
- _snprintf_s_l
- _sntprintf_s
- _snprintf_s
- snprintf_s
- _snwprintf_s
- snwprintf_s_l
- snwprintf_s
- sntprintf_s
- sntprintf_s_l
dev_langs:
- C++
helpviewer_keywords:
- _snprintf_s_l function
- _snwprintf_s_l function
- _sntprintf_s_l function
- snwprintf_s_l function
- snprintf_s function
- _snprintf_s function
- snprintf_s_l function
- _sntprintf_s function
- sntprintf_s_l function
- sntprintf_s function
- snwprintf_s function
- _snwprintf_s function
- formatted text [C++]
ms.assetid: 9336ab86-13e5-4a29-a3cd-074adfee6891
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3744fc543cd5c478ffba01e3abca9b152145be6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416442"
---
# <a name="snprintfs-snprintfsl-snwprintfs-snwprintfsl"></a>_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l

Zapisuje sformatowane dane do ciągu. Są to wersje [snprintf —, _snprintf —, _snprintf_l —, _snwprintf —, _snwprintf_l —](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int _snprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
);
int _snwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format [,
   argument] ...
);
int _snwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int _snprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja w pamięci dla danych wyjściowych.

*sizeOfBuffer*<br/>
Rozmiar lokalizację magazynu dla danych wyjściowych. Rozmiar **bajtów** dla **_snprintf_s —** lub rozmiar w **słowa** dla **_snwprintf_s —**.

*Liczba*<br/>
Maksymalna liczba znaków do przechowywania, lub [_truncate —](../../c-runtime-library/truncate.md).

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_snprintf_s —** zwraca liczbę znaków przechowywanych w *buforu*, bez uwzględnienia znak końcowy null. **_snwprintf_s —** zwraca liczbę przechowywanych w znaki dwubajtowe *buforu*, bez uwzględnienia zakończenia null znaków dwubajtowych.

Jeśli przekracza magazynu wymaganego do przechowywania danych i zakończenia null *sizeOfBuffer*, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli program obsługi nieprawidłowych parametrów wykonywania odtwarzanie jest kontynuowane, te funkcje ustawić *buforu* na pusty ciąg, ustaw **errno** do **erange —** i zwróć -1.

Jeśli *buforu* lub *format* jest **NULL** wskaźnika, lub, jeśli *liczba* jest mniejsza lub równa zero, program obsługi nieprawidłowych parametrów jest wywoływany. Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwróć -1.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Snprintf_s —** funkcja formaty i magazyny *liczba* lub mniej znaków w *buforu* i dołącza zakończenia wartości null. Każdy argument (jeśli istnieje) jest konwertowana i dane wyjściowe według specyfikacji formatu w *format*. Format jest zgodny z **printf** rodziny funkcji; zobacz [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

Jeśli *liczba* jest [_truncate —](../../c-runtime-library/truncate.md), następnie **_snprintf_s —** zapisy tyle ciągu jako spowoduje mieści się w *buforu* pozostawiając miejsca dla Trwa przerywanie wykonywania wartości null. Jeśli cały ciąg (przy użyciu zakończenia wartości null) mieści się *buforu*, następnie **_snprintf_s —** zwraca liczbę znaków, zapisane (bez przerywania null); w przeciwnym razie **_snprintf_s —**  zwraca -1, aby wskazać, że obcięcie wystąpił.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika.

**_snwprintf_s —** jest wersja znaków dwubajtowych **_snprintf_s —**; argumenty wskaźnika **_snwprintf_s —** są ciągami znaków dwubajtowych. Wykrywanie błędów kodowania **_snwprintf_s —** może się różnić od w **_snprintf_s —**. **_snwprintf_s —**, takiej jak **swprintf_s —**, zapisuje dane wyjściowe z ciągiem, a nie do miejsca docelowego typu **pliku**.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf_s —**|**_snprintf_s**|**_snprintf_s**|**_snwprintf_s**|
|**_sntprintf_s_l —**|**_snprintf_s_l**|**_snprintf_s_l**|**_snwprintf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_snprintf_s —**, **_snprintf_s_l —**|\<stdio.h>|
|**_snwprintf_s —**, **_snwprintf_s_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_snprintf_s.cpp
// compile with: /MTd

// These #defines enable secure template overloads
// (see last part of Examples() below)
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <crtdbg.h>  // For _CrtSetReportMode
#include <errno.h>

// This example uses a 10-byte destination buffer.

int snprintf_s_tester( const char * fmt, int x, size_t count )
{
   char dest[10];

   printf( "\n" );

   if ( count == _TRUNCATE )
      printf( "%zd-byte buffer; truncation semantics\n",
               _countof(dest) );
   else
      printf( "count = %zd; %zd-byte buffer\n",
               count, _countof(dest) );

   int ret = _snprintf_s( dest, _countof(dest), count, fmt, x );

   printf( "    new contents of dest: '%s'\n", dest );

   return ret;
}

void Examples()
{
   // formatted output string is 9 characters long: "<<<123>>>"
   snprintf_s_tester( "<<<%d>>>", 121, 8 );
   snprintf_s_tester( "<<<%d>>>", 121, 9 );
   snprintf_s_tester( "<<<%d>>>", 121, 10 );

   printf( "\nDestination buffer too small:\n" );

   snprintf_s_tester( "<<<%d>>>", 1221, 10 );

   printf( "\nTruncation examples:\n" );

   int ret = snprintf_s_tester( "<<<%d>>>", 1221, _TRUNCATE );
   printf( "    truncation %s occur\n", ret == -1 ? "did"
                                                  : "did not" );

   ret = snprintf_s_tester( "<<<%d>>>", 121, _TRUNCATE );
   printf( "    truncation %s occur\n", ret == -1 ? "did"
                                                  : "did not" );
   printf( "\nSecure template overload example:\n" );

   char dest[10];
   _snprintf( dest, 10, "<<<%d>>>", 12321 );
   // With secure template overloads enabled (see #defines
   // at top of file), the preceding line is replaced by
   //    _snprintf_s( dest, _countof(dest), 10, "<<<%d>>>", 12345 );
   // Instead of causing a buffer overrun, _snprintf_s invokes
   // the invalid parameter handler.
   // If secure template overloads were disabled, _snprintf would
   // write 10 characters and overrun the dest buffer.
   printf( "    new contents of dest: '%s'\n", dest );
}

void myInvalidParameterHandler(
   const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);
}

int main( void )
{
   _invalid_parameter_handler oldHandler, newHandler;

   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);
   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   Examples();
}
```

```Output

count = 8; 10-byte buffer
    new contents of dest: '<<<121>>'

count = 9; 10-byte buffer
    new contents of dest: '<<<121>>>'

count = 10; 10-byte buffer
    new contents of dest: '<<<121>>>'

Destination buffer too small:

count = 10; 10-byte buffer
Invalid parameter handler invoked: ("Buffer too small", 0)
    new contents of dest: ''

Truncation examples:

10-byte buffer; truncation semantics
    new contents of dest: '<<<1221>>'
    truncation did occur

10-byte buffer; truncation semantics
    new contents of dest: '<<<121>>>'
    truncation did not occur

Secure template overload example:
Invalid parameter handler invoked: ("Buffer too small", 0)
    new contents of dest: ''
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
