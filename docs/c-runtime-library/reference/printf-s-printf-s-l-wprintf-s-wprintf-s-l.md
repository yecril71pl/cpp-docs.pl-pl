---
title: printf_s —, _printf_s_l —, wprintf_s —, _wprintf_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _printf_s_l
- wprintf_s
- _wprintf_s_l
- printf_s
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
- wprintf_s
- printf_s
dev_langs:
- C++
helpviewer_keywords:
- wprintf_s function
- tprintf_s function
- _tprintf_s function
- printf_s_l function
- printf_s function
- _printf_s_l function
- printf function, format specification fields
- printf function, using
- _tprintf_s_l function
- wprintf_s_l function
- formatted text [C++]
- tprintf_s_l function
- _wprintf_s_l function
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ffe17ed1fc562b61d306294e970a070b03186e7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="printfs-printfsl-wprintfs-wprintfsl"></a>printf_s, _printf_s_l, wprintf_s, _wprintf_s_l

Drukowanie sformatowanych dane wyjściowe do standardowego strumienia wyjściowego. Te wersje programu [printf, _printf_l —, wprintf, _wprintf_l —](printf-printf-l-wprintf-wprintf-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int printf_s(
   const char *format [,
   argument]...
);
int _printf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf_s(
   const wchar_t *format [,
   argument]...
);
int _wprintf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parametry

*Format*<br/>
Format formantu.

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znakom lub wartość ujemną, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

**Printf_s —** funkcji formatuje i wyświetla serii znaków i wartości do standardowego strumienia wyjściowego, **stdout**. Jeśli argumenty *format* ciągu *format* ciąg musi zawierać specyfikacji, które określają format wyjściowy dla argumentów.

Główną różnicą między **printf_s —** i **printf** jest to, że **printf_s —** sprawdza występowanie prawidłowych znaków formatowania, ciąg formatu konieczne **printf**  tylko umożliwia sprawdzenie, czy ciąg formatu wskaźnika o wartości null. Jeśli zaznacz kończy się niepowodzeniem, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy **errno** do **einval —**.

Aby uzyskać informacje dotyczące **errno** i kody błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**printf_s —** i **fprintf_s —** zachowują się tak samo, z wyjątkiem **printf_s —** zapisuje dane wyjściowe do **stdout** , a nie do miejsca docelowego typu **Pliku**. Aby uzyskać więcej informacji, zobacz [fprintf_s —, _fprintf_s_l —, fwprintf_s —, _fwprintf_s_l —](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

**wprintf_s —** jest wersja znaków dwubajtowych **printf_s —**; *format* jest ciągiem znaków dwubajtowych. **wprintf_s —** i **printf_s —** zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. **printf_s —** aktualnie nie obsługuje dane wyjściowe do strumienia UNICODE.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_unicode — definicja|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s —**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l —**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

*Format* argument składa się ze znaków zwykłej, sekwencji unikowych i (Jeśli argumenty *format*) specyfikacji formatu. Zwykłe znaków oraz sekwencje specjalne są kopiowane do **stdout** w kolejności ich wyglądu. Na przykład wiersza

```C
printf_s("Line one\n\t\tLine two\n");
```

generuje dane wyjściowe

```Output
Line one
        Line two
```

[Specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) zawsze zaczynać się od znaku procentu (**%**) i są odczytywane lewej do prawej. Gdy **printf_s —** napotka pierwszy specyfikacji formatu (jeśli istnieje), są konwertowane na wartość pierwszego argumentu po *format* i odpowiednio danych wyjściowych. Drugi specyfikacji formatu powoduje, że drugi argument przekonwertować i dane wyjściowe, i tak dalej. W przypadku więcej argumentów niż Brak specyfikacji formatu dodatkowe argumenty są ignorowane. Wyniki są niezdefiniowana, jeśli nie ma za mało argumentów dla wszystkich specyfikacji formatu.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**printf_s —**, **_printf_s_l —**|\<stdio.h>|
|**wprintf_s —**, **_wprintf_s_l —**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu **stdin**, **stdout**, i **stderr**, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_printf_s.c
/* This program uses the printf_s and wprintf_s functions
* to produce formatted output.
*/

#include <stdio.h>

int main( void )
{
   char   ch = 'h', *string = "computer";
   int    count = -9234;
   double fp = 251.7366;
   wchar_t wch = L'w', *wstring = L"Unicode";

   /* Display integers. */
   printf_s( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",
           count, count, count );

   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   /* Display in different radixes. */
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   /* Display characters. */

   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);

   /* Display strings. */

   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",
   string, string, wstring, wstring);
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",
       string, string, wstring, wstring);

   /* Display real numbers. */
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );

   /* Display pointer. */
   printf_s( "\nAddress as:   %p\n", &count);

}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF78

```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
