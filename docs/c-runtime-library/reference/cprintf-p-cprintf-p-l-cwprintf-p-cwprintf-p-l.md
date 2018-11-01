---
title: _cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l
ms.date: 11/04/2016
apiname:
- _cprintf_p_l
- _cwprintf_p_l
- _cwprintf_p
- _cprintf_p
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
- cprintf_p
- cwprintf_p
- tcprintf_p
- _cwprintf_p_l
- _cprintf_p
- csprintf_p_l
- _cprintf_p_l
- _cwprintf_p
- _tcprintf_p
- cprintf_p_l
helpviewer_keywords:
- _cwprintf_p_l function
- cwprintf_p function
- tcprintf_p_l function
- cprintf_p_l function
- _tcprintf_p function
- _tcprintf_p_l function
- _cprintf_p function
- _cprintf_p_l function
- cwprintf_p_l function
- _cwprintf_p function
- tcprintf_p function
- cprintf_p function
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
ms.openlocfilehash: ef4ac6a89749c2784e4935fcf83810e81b61ae11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658461"
---
# <a name="cprintfp-cprintfpl-cwprintfp-cwprintfpl"></a>_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l

Formatuje i drukuje do konsoli oraz obsługuje parametry pozycyjne w ciągu formatu.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _cprintf_p(
   const char * format [,
   argument] ...
);
int _cprintf_p_l(
   const char * format,
   locale_t locale [,
   argument] ...
);
int _cwprintf_p(
   const wchar * format [,
   argument] ...
);
int _cwprintf_p_l(
   const wchar * format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*Format*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Parametry opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Liczba znaków drukowanych lub wartość ujemną, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Te funkcje formatują i drukują szeregi znaków i wartości bezpośrednio do konsoli, za pomocą **_putch** i **_putwch** funkcji do znaków danych wyjściowych. Każdy *argument* (jeśli istnieje) jest konwertowaya i wychodzi według specyfikacji formatu w *format*. Format ma taką samą formę i funkcjonuje jako *format* parametr [printf_p](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) funkcji. Różnica między **_cprintf_p —** i **cprintf_s —** jest fakt, że **_cprintf_p —** wspiera parametry pozycyjne, które umożliwiają określenie kolejności, w której argumenty są: używany w ciągu formatu. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).

W odróżnieniu od **fprintf_p —**, **printf_p**, i **sprintf_p —** funkcji ani **_cprintf_p —** ani **_cwprintf_p —** tłumaczy znaków wysuwu wiersza na powrotu karetki, kombinacje kanał wiersza powrotu (CR-LF) podczas drukowania. Jest to ważna różnica **_cwprintf_p —** Wyświetla znaki Unicode, gdy są używane w Windows NT. W odróżnieniu od **_cprintf_p —**, **_cwprintf_p —** używa bieżących ustawień regionalnych konsoli.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika.

Ponadto, podobnie jak **_cprintf_s** i **_cwprintf_s —**, walidują one wskaźnik danych wejściowych i ciąg formatu. Jeśli *format* lub *argument* są **NULL**, lub ciąg formatu zawiera nieprawidłowe znaki formatowania, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, jako opisane w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcprintf_p —**|**_cprintf_p**|**_cprintf_p**|**_cwprintf_p**|
|**_tcprintf_p_l —**|**_cprintf_p_l**|**_cprintf_p_l**|**_cwprintf_p_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cprintf_p —**, **_cprintf_p_l —**|\<conio.h>|
|**_cwprintf_p —**, **_cwprintf_p_l —**|\<conio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_cprintf_p.c
// This program displays some variables to the console
// using the _cprintf_p function.

#include <conio.h>

int main( void )
{
    int         i = -16,
                h = 29;
    unsigned    u = 62511;
    char        c = 'A';
    char        s[] = "Test";

    // Note that console output does not translate
    // \n as standard output does. Use \r\n instead.
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",
                h, i, u, c, s );
}
```

```Output
-16  001d  62511  A Test
```

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)<br/>
[_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p Parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
