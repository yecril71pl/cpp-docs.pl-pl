---
title: _vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l
ms.date: 11/04/2016
apiname:
- _vfprintf_p
- _vfwprintf_p
- _vfprintf_p_l
- _vfwprintf_p_l
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
- _vfwprintf_p_l
- _vfprintf_p
- vfwprintf_p_l
- vfwprintf_p
- vfprintf_p_l
- _vfwprintf_p
- _vftprintf_p
- _vfprintf_p_l
- vfprintf_p
helpviewer_keywords:
- vfprintf_p_l function
- _vftprintf_p_l function
- _vfprintf_p function
- vfprintf_p function
- vftprintf_p_l function
- _vfprintf_p_l function
- _vftprintf_p function
- _vfwprintf_p_l function
- vfwprintf_p_l function
- _vfwprintf_p function
- vftprintf_p function
- formatted text [C++]
- vfwprintf_p function
ms.assetid: 4d4a0914-4175-4b65-9ca1-037c4ef29147
ms.openlocfilehash: 7e93972ccd77d730d873177fe92f958877c83fe4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515313"
---
# <a name="vfprintfp-vfprintfpl-vfwprintfp-vfwprintfpl"></a>_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l

Napisz sformatowane wyniki za pomocą wskaźnika do listy argumentów, za pomocą możliwość określenia kolejność, że argumenty są używane w ciągu formatu.

## <a name="syntax"></a>Składnia

```C
int _vfprintf_p(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_p_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vfwprintf_p(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_p_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*Format*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**_vfprintf_p —** i **_vfwprintf_p —** zwracają liczbę znaków napisanych, nie wliczając kończącego znaku null lub wartość ujemną, jeśli wystąpi błąd danych wyjściowych.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dostarczone dane do *strumienia*. Funkcje te różnią się od **_vfprint_s** i **_vfwprint_s** wersje tylko dlatego, że obsługują one parametry pozycyjne. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).

**_vfwprintf_p —** jest wersją znaków dwubajtowych **_vprintf_p —**; dwie funkcje zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **_vprintf_p —** aktualnie nie obsługuje danych wyjściowych w strumieniu UNICODE.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych wątku.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

Jeśli *strumienia* lub *format* jest wskaźnikiem typu null lub jeżeli ciąg formatu zawiera nieprawidłowe znaki formatowania, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_p —**|**_vfprintf_p**|**_vfprintf_p**|**_vfwprintf_p**|
|**_vftprintf_p_l —**|**_vfprintf_p_l**|**_vfprintf_p_l**|**_vfwprintf_p_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_vfprintf_p —**, **_vfprintf_p_l —**|\<stdio.h > i \<stdarg.h >|\<varargs.h>*|
|**_vfwprintf_p —**, **_vfwprintf_p_l —**|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Wymagane dla zgodności systemu UNIX V.

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p Parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)<br/>
[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
