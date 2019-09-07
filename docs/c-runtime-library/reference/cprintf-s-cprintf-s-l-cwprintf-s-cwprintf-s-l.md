---
title: _cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l
ms.date: 11/04/2016
apiname:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
- _cwprintf_s_l
- _cprintf_s
- cwprintf_s
- _cprintf_s_l
- cwprintf_s_l
- cprintf_s_l
- _tcprintf_s
- cprintf_s
- _cwprintf_s
- tcprintf_s
helpviewer_keywords:
- tcprintf_s_l function
- _cprintf_s_l function
- _cwprintf_s_l function
- tcprintf_s function
- _tcprintf_s_l function
- _cwprintf_s function
- cwprintf_s function
- _cprintf_s function
- cprintf_s function
- _tcprintf_s function
- cprintf_s_l function
- cwprintf_s_l function
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
ms.openlocfilehash: 3652587c9622c2eb9fe316782d1b1c7c9644dc8f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739831"
---
# <a name="_cprintf_s-_cprintf_s_l-_cwprintf_s-_cwprintf_s_l"></a>_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l

Formatuje i drukuje do konsoli. Te wersje [_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _cprintf_s(
   const char * format [,
   argument] ...
);
int _cprintf_s_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_s(
   const wchar * format [,
   argument] ...
);
int _cwprintf_s_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Ciąg kontroli formatu.

*argument*<br/>
Parametry opcjonalne.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Liczba drukowanych znaków.

## <a name="remarks"></a>Uwagi

Te funkcje formatują i drukują serie znaków i wartości bezpośrednio do konsoli przy użyciu funkcji **_putch** ( **_putwch** for **_cwprintf_s**) do znaków danych wyjściowych. Każdy *argument* (jeśli istnieje) jest konwertowany i wyprowadzany zgodnie ze specyfikacją formatu w *formacie*. Format ma taką samą formę i funkcję jak parametr *formatu* dla funkcji [printf_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) . W przeciwieństwie do funkcji **fprintf_s**, **printf_s**i **sprintf_s** , żadne **_cprintf_s** ani **_cwprintf_s** nie tłumaczy znaków WYSUWU wiersza na kombinacje wysuwu wiersza (CR-LF) w przypadku danych wyjściowych.

Ważną różnicą jest to, że **_cwprintf_s** Wyświetla znaki Unicode, gdy są używane w systemie Windows NT. W przeciwieństwie do **_cprintf_s**, **_cwprintf_s** używa bieżących ustawień regionalnych konsoli

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *Format* nie jest ciągiem zdefiniowanym przez użytkownika.

Podobnie jak w przypadku niezabezpieczonych wersji (zobacz [_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)), te funkcje sprawdzają poprawność swoich parametrów i wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md), jeśli *Format* ma wartość null przytrzymaj. Funkcje te różnią się od wersji niezabezpieczonej, ponieważ sam ciąg formatu jest również sprawdzany. Jeśli istnieją jakieś nieznane lub źle sformułowane specyfikatory formatowania, te funkcje wywołują procedurę obsługi nieprawidłowego parametru. We wszystkich przypadkach, jeśli wykonanie może być kontynuowane, funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_s**|**_cprintf_s**|**_cprintf_s**|**_cwprintf_s**|
|**_tcprintf_s_l**|**_cprintf_s_l**|**_cprintf_s_l**|**_cwprintf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cprintf_s**, **_cprintf_s_l**|\<conio.h>|
|**_cwprintf_s**, **_cwprintf_s_l**|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_cprintf_s.c
// compile with: /c
// This program displays some variables to the console.

#include <conio.h>

int main( void )
{
   int      i = -16, h = 29;
   unsigned u = 62511;
   char     c = 'A';
   char     s[] = "Test";

   /* Note that console output does not translate \n as
    * standard output does. Use \r\n instead.
    */
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)<br/>
[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)<br/>
[Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
